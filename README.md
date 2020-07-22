# Tạo chú thích cho ảnh 

Tạo các chú thích cho ảnh có thể giúp cho việc tìm kiếm ảnh hoặc tổ chức các ảnh vào các album chung.

## Các bước thực hiện 

### 1 Dataset

Tập dữ liệu được sử dụng là tập [Flickr8k](http://academictorrents.com/details/9dea07ba660a722ae1008c4c8afdd303b6f6e53b). Dữ liệu bao gồm 8000 ảnh trong đó có 6000 ảnh train set, 1000 ảnh validation set, 1000 ảnh test set.

### 2. Các bước chi tiết 
 
### 2.1. Preprocess text 

Loại bỏ các kí tự đặc biệt (#,&,%), chuyển chữ hoa thành chữ thường, loại bỏ các chữ số.

Loại bỏ đi các từ có df <= 10

Thêm các từ  startseq và endseq vào các caption.
### 2.2. Prerocess image

Sư dụng pretrain model inceptionv3 loại bỏ đi lớp softmax cuối cùng để trích xuất tính năng của ảnh (vector này có số chiều 2048)

### 2.3. Word embedding
Quá trình này sử dụng pretrain [Glove word](https://nlp.stanford.edu/projects/glove/) 

### 2.4. Caption generator

Với m ảnh mới ta sẽ bắt đầu chuỗi với 'startseq' rồi sau đó cho vào model để dự đoán từ tiếp theo. Ta thêm từ
vừa được dự đoán vào chuỗi và tiếp tục cho đến khi gặp 'endseq' là kết thúc hoặc đến khi chuỗi có độ dài max (ở trong bài là 34 từ)

### Link tham khảo [Image Captioning with Keras](https://towardsdatascience.com/image-captioning-with-keras-teaching-computers-to-describe-pictures-c88a46a311b8)
