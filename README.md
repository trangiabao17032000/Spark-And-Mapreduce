# Spark
<pre><b>Apache spark (Spark)</b></pre>
<b>Apache Spark</b> Là 1 hệ thống được dùng để xử lý các vấn đề về dữ liệu lớn. Matei Zaharia, cha đẻ của Spark, sử dụng Hadoop từ những ngày đầu. Đến năm 2009 ông viết Apache Spark để giải quyết những bài toán học máy ở đại học UC Berkely vì Hadoop MapReduce hoạt động không hiệu quả cho những bài toán này. Rất sớm sau đó ông nhận ra rằng Spark không chỉ hữu ích cho học máy mà còn cho cả việc xử lý luồng dữ liệu hoàn chỉnh.<br>

<b>Apache Spark</b> gồm có 5 thành phần chính : Spark Core, Spark Luồng, Spark SQL, MLlib và GraphX, trong đó:<br>

<pre><b>PHÂN TÍCH THỜI GIAN THỰC</b></pre>
<b>Spark</b> có thể xử lý dữ liệu thời gian thực, tức là dữ liệu đến từ các luồng sự kiện thời gian thực với tốc độ hàng triệu sự kiện mỗi giây, chẳng hạn như dữ liệu Twitter và Facebook. Sức mạnh của Spark nằm ở khả năng xử lý luồng trực tiếp thực sự hiệu quả.<br>
<b>MapReduce</b> không tốt khi xử lý dữ liệu thời gian thực, vì nó được thiết kế để thực hiện xử lý hàng loạt trên lượng dữ liệu khổng lồ.<br>

•	<b>Spark Core</b>: Spark Core đảm nhận vai trò thực hiện công việc tính toán và xử lý trong bộ nhớ (In-memory computing) đồng thời nó cũng tham chiếu các dữ liệu được lưu trữ tại các hệ thống lưu trữ bên ngoài.<br>
•	<b>Spark SQL</b>: cung cấp một kiểu data abstraction mới (SchemaRDD) nhằm hỗ trợ cho cả kiểu dữ liệu có cấu trúc (structured data) và dữ liệu nửa cấu trúc (semi-structured data – thường là dữ liệu dữ liệu có cấu trúc nhưng không đồng nhất và cấu trúc của dữ liệu phụ thuộc vào chính nội dung của dữ liệu ấy).<br>
•	<b>Spark Luồng</b> được sử dụng để thực hiện việc phân tích luồng bằng việc coi các luồng là các mini-batches và thực hiệc kỹ thuật RDD transformation đối với các dữ liệu mini-batches này. Qua đó cho phép các đoạn code được viết cho xử lý batch có thể được tận dụng lại vào trong việc xử lý luồng, làm cho việc phát triển lambda architecture được dễ dàng hơn. Tuy nhiên điều này lại tạo ra độ trễ trong xử lý dữ liệu (độ trễ chính bằng mini-batch duration) <br>
•	<b>MLlib (Machine Learning Library)</b>: là một nền tảng học máy phân tán bên trên Spark do kiến trúc phân tán dựa trên bộ nhớ. <br>
•	<b>GrapX</b>: Grapx là nền tảng xử lý đồ thị dựa trên Spark. Nó cung cấp các Api để diễn tả các tính toán trong đồ thị bằng cách sử dụng Pregel Api.<br>


<pre><b>Apache Spark RDD</b></pre>
<b>Resilient Distributed Datasets (RDD)</b>: là một cấu trúc dữ liệu cơ bản của Spark, là một tập hợp bất biến phân tán của một đối tượng. Mỗi dataset trong RDD được chia ra thành nhiều phần vùng logical. Có thể được tính toán trên các node khác nhau của một cụm máy chủ <br>
RDDs có thể chứa bất kỳ kiểu dữ liệu nào của Python, Java, hoặc đối tượng Scala, bao gồm các kiểu dữ liệu do người dùng định nghĩa.<br> 
Có thể tạo ra RDD từ một tập hợp dữ liệu có sẵn trong ngôn ngữ sử dụng như Java, Python, Scala hoặc lấy từ dataset hệ thống lưu trữ bên ngoài như HDFS, Hbase, các cơ sở dữ liệu quan hệ. <br>
<b>Các loại RDD</b><br>

-Apache, Spark , ... , processing (kiểu chuỗi)<br>
-(for, 12) ; (Spark, 21), ... ,(the, 31) (Kiểu cặp)<br>

  Các RDD biểu diễn một tập hợp cố định, đã được phân vùng các record để có thể xử lý song song.<br>
  Các record trong RDD có thể là đối tượng Java, Scale hay Python tùy lập trình viên chọn. <br>
  RDD API có thể được sử dụng trong Python, Scala hay Java:<br>
  
<b>Một số transformation:</b><br>
  •	<b>distinct:</b> loại bỏ trùng lắp trong RDD<br>
  •	<b>filter:</b> tương đương với việc sử dụng ở trong SQL – tìm các record trong RDD xem những phần tử nào thỏa điều kiện. Có thể cung cấp một hàm phức tạp sử dụng để lọc các record cần thiết <br>
  •	<b>map:</b> thực hiện một công việc nào đó trên toàn bộ RDD. Trong Python sử dụng lambda với từng phần tử để truyền vào map.<br>
  •	<b>flatMap:</b> cung cấp một hàm đơn giản hơn hàm map. Yêu cầu output của map phải là một cấu trúc có thể lặp và mở rộng được.<br>
  •	<b>sortBy:</b> mô tả một hàm để trích xuất dữ liệu từ các đối tượng của RDD và thực hiện sắp xếp được từ đó.<br>
  •	<b>randomSplit:</b> nhận một mảng trọng số và tạo một random seed, tách các RDD thành một mảng các RDD có số lượng chia theo trọng số.<br>

<b>Một số action:</b><br>
Action thực thi ngay các transformation đã được thiết lập để thu thập dữ liệu về driver để xử lý hoặc ghi dữ liệu xuống các công cụ lưu trữ.<br>
  •	<b>reduce:</b> thực hiện hàm reduce trên RDD để thu về 1 giá trị duy nhất.<br>
  •	<b>count:</b> đếm số dòng trong RDD.<br>
  •	<b>countApprox:</b> phiên bản đếm xấp xỉ của count, nhưng phải cung cấp timeout vì có thể không nhận được kết quả.<br>
  •	<b>countByValue:</b> đếm số giá trị của RDD.<br>
    chỉ sử dụng nếu map kết quả nhỏ vì tất cả dữ liệu sẽ được load lên memory của driver để tính toán<br>
    chỉ nên sử dụng trong tình huống số dòng nhỏ và số lượng item khác nhau cũng nhỏ.<br>
  •	<b>countApproxDistinct:</b> đếm xấp xỉ các giá trị khác nhau.<br>
  •	<b>countByValueApprox:</b> đếm xấp xỉ các giá trị.<br>
  •	<b>first:</b> lấy giá trị đầu tiên của dataset.<br>
  •	<b>max và min:</b> lần lượt lấy giá trị lớn nhất và nhỏ nhất của dataset.<br>
  •	<b>take và các method tương tự:</b> lấy một lượng giá trị từ trong RDD. take sẽ trước hết scan qua một partition và sử dụng kết quả để dự đoán số lượng partition cần phải lấy thêm để thỏa mãn số lượng lấy.<br>
  •	<b>top và takeOrdered:</b> top sẽ hiệu quả hơn takeOrdered vì top lấy các giá trị đầu tiên được sắp xếp ngầm trong RDD.<br>
  •	<b>takeSamples:</b> lấy một lượng giá trị ngẫu nhiên trong RDD.<br>
 
<pre><b>Spark Dataframe</b></pre>

<b>DataFrame</b> là một API bậc cao hơn RDD được Spark giới thiệu vào năm 2013 (<b>từ Apache Spark 1.3</b>). Tương tự như RDD, dữ liệu trong DataFrame cũng được quản lý theo <b>kiểu phân tán và không thể thay đổi (immutable distributed)</b>. Tuy nhiên dữ liệu này được sắp sếp theo các cột, tương tự như trong <b>Relation Database</b>.<br>
DataFrame được phát triển để giúp người dùng có thể dễ dàng thực hiện các thao tác xử lý dữ liệu cũng như làm tăng đáng kể hiệu quả xử lý của hệ thống.<br>
Khi sử dụng DataFrame API, chúng ta gọi các hàm để trích xuất kết quả mong muốn và Spark sẽ tự động tiến hành các thuật toán xử lý. Tuy nhiên ở bước cuối cùng thì các thuật toán này vẫn được chạy trên RDD mặc dù người dùng chỉ tương tác với DataFrame.<br>

<b>Ưu điểm của Spark Datafram :</b><br>
  •	Giống như viết SQL, đầy đủ chức năng như select, where ... đặc biệt là join với các DataFrame khác.<br>
  •	Sử dụng các method như filter, select để trích xuất dữ liệu theo cột, hàng.<br>
  •	Xử gọn các loại data như Log ... với groupBy. <br>
  •	Thêm 1 cột dễ dàng với UDF(User Defined Function).<br>
  •	Giống như SQL, Spark DataFrame đã hỗ trợ Pivot (Spark 1.6 trở lên) rất hữu ích cho việc lập bảng biểu, báo cáo.<br>

<pre><b>Spark MachineLearning</b></pre>

<b>MachineLearning</b> - học máy - <br> là một lĩnh vực nhỏ của Khoa Học Máy Tính, nó có khả năng tự học hỏi dựa trên dữ liệu đưa vào mà không cần phải được lập trình cụ thể. Cốt lõi của nó là các thuật toán tự học phát triển bằng cách liên tục cải tiến công việc được giao. Đối với thuật toán học máy càng nhiều dữ liệu càng tốt.

Trong <b>pyspark.ml</b> bao gồm 2 class cơ bản là <b>Transformer</b> cho phép biến đổi dữ liệu và <b>Estimator</b> ước lượng mô hình dự báo.

   • Transfromer sử dụng hàm .transform() nhận đầu vào là 1 DataFrame và trả ra một DataFrame mới có các trường đã biến đổi theo Transform. Các bạn sẽ hiểu hơn qua thực hành ở ví dụ bên dưới.

   • Estimator sử dụng hàm .fit() để huấn luyện model. Chúng cũng nhận đầu vào là một DataFrame nhưng kết quả được trả ở đầu ra là 1 model object. Hiện tại spark hỗ trợ khá nhiều các lớp model cơ bản trong machine learning. Các lớp model xuất hiện trong Esimator bao gồm:

Đối với bài toán phân loại: LogisticRegression, DecisionTreeClassifier, RandomForestModel, GBTClassifier (gradient bosting tree), MultilayerPerceptronClassifier, LinearSVC (Linear Support Vector Machine), NaiveBayes.

Đối với bài toán dự báo: GeneralizedLinearRegression, DecisionTreeRegressor, RandomForestRegressor, GBTRegressor (gradient boosting Tree), AFTSurvivalRegression (Hồi qui đối với các lớp bài toán estimate survival).


<b>sources</b> <br>
https://laptrinh.vn/books/apache-spark/page/apache-spark-rdd<br>
https://mallikarjuna_g.gitbooks.io/spark/content/spark-properties.html<br>
http://itechseeker.com<br>
https://codetudau.com/xu-ly-du-lieu-voi-spark-dataframe/index.html<br>
https://helpex.vn/article/huong-dan-pyspark-dataframe-gioi-thieu-ve-dataframes-5c6b21e6ae03f628d053c29e<br>
https://towardsdatascience.com/the-most-complete-guide-to-pyspark-dataframes-2702c343b2e8<br>
https://www.udacity.com/blog/2020/08/machine-learning-for-big-data.html<br>
https://phamdinhkhanh.github.io/2019/07/15/PySparkSQL.html<br>

