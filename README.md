利用commons-fileupload,

~~~
<!-- 操作excel -->
			<dependency>
				<groupId>org.apache.poi</groupId>
				<artifactId>poi-ooxml</artifactId>
				<version>4.0.1</version>
			</dependency>
	
			<!-- 操作word -->
			<dependency>
				<groupId>org.apache.poi</groupId>
				<artifactId>poi-scratchpad</artifactId>
				<version>4.0.1</version>
				<optional>true</optional>
			</dependency>	
			
			<!-- 操作pdf -->
			<dependency>
				<groupId>org.apache.pdfbox</groupId>
				<artifactId>pdfbox</artifactId>
				<version>2.0.14</version>
			</dependency>		
~~~
第一个问题：上传用的springmvc，springmvc本身在处理请求时，会有一步操作，就是判断请求是否是上传请求，如果是就封装解析为一个上传请求，其中已经对数据做了一层处理，如果我用commons-fileupload，无法获取到数据。
第二个问题：由于tomcat默认上传文件大小限制为2M，一旦上传超过这个限制，tomcat直接断了连接，这样前端无法获取到后台返回的错误。
第三个问题：获取页数，对于word文档的限制条件比较大，如果是wps创建的.doc和.docx，则无法获取到确定的页数。如果word中有图片，也无法获取到准确的页数。
第四个问题：删除存储系统中的文件。保存都会面对不同的存储系统，需要SPI自己定义实现。
