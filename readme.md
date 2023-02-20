# I. Cài đặt và sử dụng phầm mềm
## 1. Platform IO lập trình ESP32
**Ứng dụng trong dự án:** Lập trình vi điều khiển ESP32 cho End Devices và Gateway.

[Link hướng dẫn chi tiết](https://khuenguyencreator.com/huong-dan-cai-dat-platform-io-lap-trinh-esp32/)
## Cài đặt Visual Studio Code (VS Code)
Truy cập link: https://code.visualstudio.com/
-- Download và Cài đặt như một software bình thường.
## Cài đặt Platform IO
-- Trước khi cài Extension này, chúng ta cần cài đặt Python cho máy tính đã.

![example](1-python.png)

Truy cập link: https://www.python.org/downloads/.  
**Lưu ý**: Hãy tích chọn Add Python 3.8 to PATH để có thể run Python ở bất cứ đâu.  
-- Sau đó mở VS code, chuyển đến tab Extension, trong ô tìm kiếm gõ    **Platformio IDE**.
-- Nhấn cài đặt, sau khi cài đặt xong sẽ hiển thị như hình:

![example](download-platform.png)  
-- Restart lại VS code sau đó chờ cho tất cả các extension được load.
**Lưu ý:** máy tính bạn cần phải có mạng nhé.
## Cài đặt Driver nạp cho mạch.
-- Tùy vào trường hợp mạch bạn sử dụng IC UART nào, chúng ta sẽ cài đặt driver cho chip đó:
Thường là 2 loại:  
CP210x: [Link download và cài đặt](https://sparks.gogo.co.nz/ch340.html).  
CH340:  [Link download và cài đặt](https://sparks.gogo.co.nz/ch340.html).  
## Hướng dẫn sử dụng Platform IO lập trình ESP32
-- Tạo một dự án lập trình ESP32 với Platform IO.
Chúng ta nhấn vào biểu tượng logo của Platform io, trong tab Quick Acccess nhấn Open. Vs code sẽ mở ra trang PIO Home.  
-- Sau đó nhân vào New Project để tạo 1 dự án mới. Đặt tên dự án, Chọn KIT sử dụng, ở đây là board DOIT ESP32 DEV KIT (loại thường gặp nhất đó).  
Chọn Framwork là Arduino:

![example](3-adruino.jpg)

-- Bỏ tick Use Defaul Location, sau đó trỏ tới nơi bạn lưu project, nhấn Finish để hoàn thành.  

![example](4-location.jpg)  

-- Sau khi project được tạo, giao diện như sau:  

![example](platformio-4-742x400.jpg)

**Gồm :**
- **Phần cây thư mục dự án:** cho chúng ta thêm, sửa, xóa các file nhanh
Phần Text editor: là nơi viết code
- **Cửa sổ Terminal:** Nơi gõ các câu lênh
**Thanh công cụ:** Lần lượt là Home, Build, Upload code, Clean, Serial Monitor(màn hình serial), Terminal
- **Thư mục Src:** Chứa Source code của chương trình, đây là nơi lưu trữ code và bạn sẽ code trên đó. File thực thi chính là: main.cpp
- **Ứng dụng trong dự án:** Lập trình vi điều khiển ESP32 cho End Devices và Gateway

-- Trên thực tế, các bạn có thể Copy trực tiếp các đoạn code viết bằng Arduino IDE và Paste thẳng vào đây. Chỉ cần giữ **#include <Arduino.h>** là code cũng có thể chạy bình thường. Thế nên các dự án mà bạn viết bằng Arduino cũng đều có thể viết bằng VS code nhé.   
-- File platformio.ini là file cấu hình PlatformIO cho project của bạn. Nó hiển thị các thông tin như platform, board và framework được sử dụng. Bạn cũng có thể thêm các cấu hình khác như các thư viện được đưa vào, tùy chọn upload code, hay tốc độ truyền của Serial Monitor, đường dẫn thư viện và các cấu hình khác. Thực tế các bạn nên để nguyên.  
-- Nếu muốn thay đổi tốc độ baud của Serial Monitor có thể sử dụng lệnh: **monitor_speed = 115200**.  
-- Nếu muốn thêm đường dẫn của thư viện chúng ta dùng: lib_deps = E:/thuvien. Trong đó E:/thuvien là đường dẫn tới file thư viện bạn cài đặt.    
## Cài đặt thư viện cho Platformio   
### Sử dụng công cụ Libraly trong Platformio  
- Làm theo quy trình dưới đây nếu bạn cần cài đặt thư viện trong PlatformIO IDE.  
- Nhấp vào biểu tượng Home để chuyển đến Trang chủ PlatformIO. Nhấp vào biểu tượng Libraries trên thanh bên trái.  
- Tìm kiếm thư viện bạn muốn cài đặt. Ví dụ Adafruit_BME280 .  

![example](platfomrio-thu-vien-3-602x400.png)

-- Nhấp vào thư viện bạn muốn đưa vào dự án của mình. Sau đó, nhấp vào Add to Project.  

![example](platfomrio-thu-vien-1.png)


-- Chọn dự án bạn muốn sử dụng thư viện.

![exapmle](platfomrio-thu-vien-2-669x400.png)

-- Thao tác này sẽ thêm code định danh thư viện bằng cách sử dụng lid_depschỉ thị trên file platformio.ini . Nếu bạn mở file platformio.ini của dự án , nó sẽ trông nh thể hiện trong hình ảnh sau.  

![example](platfomrio-thu-vien-4-768x357.png)

-- Ngoài ra, trên cửa sổ thư viện, nếu bạn chọn tab Installation và cuộn một chút, bạn sẽ thấy code định danh cho thư viện. Bạn có thể chọn bất kỳ số nhận dạng nào tùy thuộc vào tùy chọn bạn muốn sử dụng. Các mã nhận dạng thư viện được đánh dấu màu đỏ.

![example](platfomrio-thu-vien-5-513x400.png)

## Build và Upload code cho ESP32 bằng Platform IO
-- Mình sẽ chọn một example huyền thoại là Blink Led trên Arduino IDE, copy đoạn code đó, sau đó paste vào VS code

![example](Screenshot_1-768x370.jpg)

Nhớ giữ lại **#include <Arduino.h>** nhé!

![example](Screenshot_2-744x400.jpg)

-- Sau đó nhấn Build để biên dịch chương trình, Khi terminal báo Success là ok. Nếu chương trình có lỗi, hãy chuển tab Problems để view lỗi nhé!  
-- Cắm mạch vào và nhấn Upload, nếu đến đoạn connecting mà vscode ko tìm thấy esp, các bạn nhấn nút BOOT trên mạch giữ 1 chút rồi nhả ra nhé. Để ESP vào chế độ Nạp.

![example](Screenshot_3-768x130.jpg)

-- Sau khi nạp xong, thì xem thành quả thôi!!!

## 3. Arduino
**Ứng dụng trong dự án:** UART để hiển thị các dữ liệu truyền nhận được giữa End Devices và Gateway, hỗ trợ mô phỏng để kiểm tra dữ liệu theo thời gian.  
[Link hướng dẫn chi tiết](https://khuenguyencreator.com/bai-1-huong-dan-cai-dat-arduino-ide-va-cach-them-thu-vien/)  
**Bước 1:** Truy cập địa chỉ này để cài đặt [Arduino IDE](https://www.arduino.cc/pro/software-arduino-pro-ide/). Đây là nơi lưu trữ cũng như cập nhật các bản IDE của Arduino. Bấm vào mục **Windows ZIP file**  như hình minh họa.  

![example](1338_81220-1431420080-0-2015-05-12-21h45-54-1-789x400.png)  

Bạn sẽ được chuyển đến một trang mời quyền góp tiền để phát triển phần mềm cho Arduino, tiếp tục bấm **JUST DOWNLOAD** để bắt đầu tải.

![example](1394_12320-1431420084-0-2015-05-12-21h46-45-701x400.png)

**Bước 2:** Sau khi download xong, các bạn bấm chuột phải vào file vừa **download arduino-1.6.4-windows.zip** và chọn **“Extract here”** để giải nén.

![example](1364_88220-1431517904-0-2015-05-13-18h50-56-411x400.png)

**Bước 3:** Copy thư mục arduino-1.6.4 vừa giải nén đến nơi lưu trữ.
**Bước 4:** Chạy file cài đặt trong thư mục arduino để cài đặt Arduino IDE và khởi động nó lên. 

![example](1398_12320-1431518163-0-2015-05-13-18h55-51-333x400.png)

Như vậy chúng ta đã cài đặt Arduino IDE xong.  

**Cài đặt Serial**
-- Cài đặt **Port** truyền nhận dữ liệu (ở đây mình đang dùng COM5) và tốc độ truyền ở **Upload Speed**.

![example](port.png)

-- Serial trên Adrunino có chế độ **Show Timestamp** để hiển thị thời gian truyền nhận đến **ms**.

![example](serialcom5.png)
# II. Triển khai dự án
## 1. Sơ đồ chân 
**-- Gateway**  

| Lora sx1278  | esp32  |
|:---:|:---:|
|3.3V|3.3V   |
| GND  |GND   |
| NSS|D5   |
| DIDO  |D2   |
| SCK  |D18   |
| MISO     |D19   |
| MOSI  |D23   |
| RST  |D14   |  

**-- Endnode**  

| Lora sx1278  | esp32  |
|:---:|:---:|
|3.3V|3.3V   |
| GND  |GND   |
| NSS|D5   |
| DIDO  |D2   |
| SCK  |D18   |
| MISO  |D19   |
| MOSI  |D23   |
| RST  |D14   |
| Data DS18B20 |D13   |
| Chân nút nhấn  |  D15 |
|  Led xanh |D25   |
|  Led vàng |D26   |
|  Led đỏ |D27 |  

## 2. Xây dựng EndNode
### 2.1 Cơ chế hoạt động  
EndNode: chủ yếu ở chế độ chỉ gửi dữ liệu, thời gian thức khoảng 2s
- Giữ nút 1 lúc > 1s thì vào chế độ: Nhận dữ liệu từ Gateway để cập nhật ngưỡng nhiệt độ
+ kiểm tra địa chỉ xem có phải gửi cho EndNode này hoặc Broadcast không, đúng mới nhận, còn không thì không nhận  
+ Dữ liệu truyền đi dạng abcdef: abc = T_Blue, def = T_Yellow  
Giả sử: nhiệt độ đo được là temp_current  
temp_current <= T_Blue:  bật đèn xanh  
T_Blue < temp_current <= T_Yellow: bật đèn vàng  
temp_current > T_Yellow: bật đèn đỏ  
- Khi nhấn nút < 1s: bắt đầu đo nhiệt độ và gửi dữ liệu lên Gateway, gửi xong vào chế độ ngủ  
+ Hiển thị Led theo ngưỡng nhiệt trong 0.5s   
### 2.2 Một số hàm quan trọng  
a) Hàm gửi dữ liệu:  
```c
void sendMessage(byte* outgoing) {
  LoRa.beginPacket();                   // bắt đầu gói tin
  LoRa.write(destination);              // thêm địa chỉ nhận
  LoRa.write(localAddress);             // thêm địa chỉ gửi
  LoRa.write(msgCount);                 // thêm chỉ số bản tin gửi đi     
  LoRa.write(payloadLenght);            // thêm độ dài bản tin gửi đi
  LoRa.write(outgoing, payloadLenght);  // thêm bản tin
  LoRa.endPacket();                     // kết thúc gói tin và gửi đi
  msgCount++;                           // tăng chỉ số bản tin
}
```  
b) Hàm đưa Endnode vào chế độ ngủ  
```c
// Vào chế độ ngủ
  Serial.println("Going to sleep now");
  esp_deep_sleep_start();
```
c) Hàm thức giấc Endnode bằng cách nhấn nút  
```c
//Cài đặt chân 15 để làm nút nhấn
  esp_sleep_enable_ext0_wakeup(GPIO_NUM_15,1); //1 = High, 0 = Low
```
d) Hàm nhận và cập nhật ngưỡng nhiệt cho Endnode
```c
// Hàm nhận dữ liệu để thay đổi ngưỡng nhiệt
void onReceive(int packetSize) {
  if (packetSize == 0) return;          // Nếu không có bản tin thì return
//Phân tích dữ liệu nhận được
  int recipient = LoRa.read();          // địa chỉ người nhận
  byte sender = LoRa.read();            // địa chỉ người gửi
  byte incomingMsgId = LoRa.read();     // chỉ số bản tin nhận
  byte incomingLength = LoRa.read();    // độ dài bản tin nhận

  Serial.println("Received from: 0x" + String(sender, HEX));
  Serial.println("Sent to: 0x" + String(recipient, HEX));
  Serial.println("Message ID: " + String(incomingMsgId));
  Serial.println("Message length: " + String(incomingLength));
  byte incomingData[4];
  int i=0;
  Serial.println("We are in the case of data receiving");    
  while (LoRa.available()) {
  incomingData[i] = LoRa.read();
  i++;
  }    
// Kiểm tra xem nếu gửi cho Endnode này hoặc Broadcast thì mới nhận
  if (recipient != localAddress && recipient != 0xFF) {   
    Serial.println("This message is not for me.");
    return;                             // skip rest of function
  }
// Nhận ngưỡng nhiệt
    T_Blue = ((incomingData[0] << 8) | incomingData[1]);
    T_Blue = T_Blue;
    T_Yellow = ((incomingData[2] << 8) | incomingData[3]);
    T_Yellow = T_Yellow;
    Serial.println("Blue Temperature Threshold: " + String (T_Blue));
    Serial.println("Yellow Temperature Threshold: " + String (T_Yellow));
  }
```
e) Hàm đưa End Node vào chế độ nhận ngưỡng nhiệt từ Gateway
```c
// Nếu vẫn đang nhấn nút thì vào chế độ nhận ngưỡng nhiệt
  while(digitalRead(btnPin) == HIGH)
  {
  Serial.println("In the case of receiving heat threshold");
	onReceive(LoRa.parsePacket()); 
  }	
```
## Xây dựng Gateway  
### 2.1 Cơ chế hoạt động  
 - Nhận dữ liêu nhiệt độ đo được từ EndNode và hiển thị lên ThingSpeak, xuất file excel
+ Kiểm tra xem dữ liệu có phải được gửi từ 10 địa chỉ Endnode đã cấp trước không, nếu đúng thì mới nhận, còn không thì không nhận  
+ Kiểm tra địa chỉ xem có phải gửi cho Gateway hoặc Broadcast không  
+ Kiểm tra xem có phải chỉ số bản tin mới không ( tránh trường hợp tấn công bản tin gây treo hệ thống ).  
=> Các điều kiện kiểm tra đúng thì mới nhận gói tin.  
+ Có dữ liệu nhiệt độ mới thì đẩy lên ThingSpeak để hiển thị và xuất file Excel.  
- Tạo Web Server để cập nhật ngưỡng nhiệt  
+ Có hiển thị nhiệt độ mới nhận được từ Endnode  
+ Nhận dữ liệu cập nhật ngưỡng từ Web Server,khi ngưỡng nhiệt độ thay đổi thì mới gửi xuống EndNode để thay đổi ngưỡng.  
+ Dữ liệu truyền đi dạng abcdef: abc = temp_blue, def = temp_yellow  
### 2.2 Một số hàm quan trọng  
a)  Gateway: Hàm kiểm tra và nhận dữ liệu từ Endnode   
```c
//Nhan du lieu tu End Node
void onReceive(int packetSize) {
  
  if (packetSize == 0) return;          // Nếu không có bản tin thì return

  // read packet header bytes:
  int recipient = LoRa.read();          // địa chỉ người nhận
  byte sender = LoRa.read();            // địa chỉ người gửi
  byte incomingMsgId = LoRa.read();     // chỉ số bản tin nhận
  byte incomingLength = LoRa.read();    // độ dài bản tin nhận

  Serial.println("Received from: 0x" + String(sender, HEX));
  Serial.println("Sent to: 0x" + String(recipient, HEX));
  Serial.println("Message ID: " + String(incomingMsgId));
  Serial.println("Message length: " + String(incomingLength));
  Serial.println();


  byte incomingData[4];
  int i=0;

// Data từ EndNode (10 Endnode)
// Kiểm tra xem dữ liệu có phải được gửi từ 10 địa chỉ này không, có phải là chỉ số bản tin mới không  
// Nếu đúng thì mới nhận, còn không thì không nhận
// Kiểm tra địa chỉ
  if ( sender == 0x2 || sender == 0x3 || sender == 0x4 || sender == 0x5 || sender == 0x6 
       || sender == 0x7 || sender == 0x8 || sender == 0x9 || sender == 0x10 || sender == 0x11 ) {                  
// Kiểm tra chỉ số bản tin
    if(pre_incomingMsgId < incomingMsgId)
    {
    pre_incomingMsgId = incomingMsgId;
    Serial.println("In the case of data receiving");    
    while (LoRa.available()) {
    incomingData[i] = LoRa.read();
    i++;
    } 
    }   
  }
  
// Nếu dữ liệu không phải cho Gateway hoăc Broadcast thì sẽ không nhận
  if (recipient != localAddress && recipient != 0xFF) {   // check xem co phai gui cho minh k : 0xFF: broadcast
    Serial.println("This message is not for me.");
    return;                             // skip rest of function
  }

// Demo data from End Node 0x2
  if (sender == 0x2) {                                                                               
    temperature = ((incomingData[0] << 8) | incomingData[1]);
    temperature = temperature/10;
    Serial.println("Nhiet do la");
    Serial.println(temperature);
    // gửi nhiệt độ lên thinkspeak
  if (client.connect(server1, 80)) // "184.106.153.149" or api.thingspeak.com
   {
      String postStr = apiKey;
      postStr += "&field1=";
      postStr += String(temperature);
      postStr += "\r\n\r\n\r\n\r\n";
    
      client.print("POST /update HTTP/1.1\n");
      client.print("Host: api.thingspeak.com\n");
      client.print("Connection: close\n");
      client.print("X-THINGSPEAKAPIKEY: " + apiKey + "\n");
      client.print("Content-Type: application/x-www-form-urlencoded\n");
      client.print("Content-Length: ");
      client.print(postStr.length());
      client.print("\n\n");
      client.print(postStr);
      //client.stop();
 
    }    
  }
}
```
b) Hàm nhận ngưỡng nhiệt và gửi xuống Endnode  
```c
// Hàm nhận ngưỡng nhiệt và gửi xuống Endnode
void temperature_threshold()
{
// Chuỗi nhận được là string inputMessage ="abcdec" abc:T_blue, def: T_yellow
// Kiểm tra xem có dữ liệu mới từ Web Server không, nếu có thì mới gửi, không thì thoát
  if(inputMessage.equals(pre_outgoing)) return;
  else
  {
  pre_outgoing = inputMessage;
  int result = inputMessage.toInt (); 
  int temp_blue = result/1000;
  int temp_yellow = result%1000;
  Data[0] = temp_blue >> 8; 
  Data[1] = temp_blue;
  Data[2] = temp_yellow >> 8; 
  Data[3] = temp_yellow;
  sendMessage(Data);
  }
}
```



