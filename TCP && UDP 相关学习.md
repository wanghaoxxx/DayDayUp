# TCP && UDP 相关学习

### TCP 三次握手
* TCP 协议提供可靠的连接服务。采用三次握手才能建立一个连接。
	* 第一次握手：建立连接时，客户端发送syn包到服务器，自己进入SYN_SEND 状态 SYN:同步序列编号（Synchronize Sequence Numbers),(SYN=1,seq=J)
	* 第二次握手：服务器收到syn包，确认客户端syn包，同时自己也发送一个SYN+ACK包，此时服务器进入SYN_RECV 状态。(SYN=1,ACK=1,ack=J+1,seq=K)
	* 第三次握手：客户端收到服务器的SYN+ACK包，向服务器发送确认包ACK。放完毕后客户端服务器进入ESTABLISHED状态，完成三次握手，可以开始传输数据。(ACK=1,ack=K+1)
	* Seq序号 ：发送方赋值，Ack 确认序号 接受方赋值，只有对应的标识位为1时才有效。
* 可靠性
	*  TCP之所以可靠是因为有报文验证机制。TCP报文格式中有Seq字段标识报文序号。

	
	
### TCP 四次挥手

* TCP 是全双工的，因此每个方向必须要单独进行关闭。当一方完成发送数据时发送一个FIN来终止这一方向的连接，收到FIN只代表不会再收到数据了，但是依然能发送数据，直到这一方向也发送了FIN。首先进行关闭的一方将执行关闭，然后另外一方收到FIN的再执行关闭。
* 为什么建立连接是三次握手，而关闭连接却是四次挥手呢？
  * 这是因为服务端在LISTEN状态下，收到建立连接请求的SYN报文后，把ACK和SYN放在一个报文里发送给客户端。而关闭连接时，当收到对方的FIN报文时，仅仅表示对方不再发送数据了但是还能接收数据，己方也未必全部数据都发送给对方了，所以己方可以立即close，也可以发送一些数据给对方后，再发送FIN报文给对方来表示同意现在关闭连接，因此，己方ACK和FIN一般都会分开发送。
* 客户端主动关闭的情况
	* 第一次：client发送FIN 
	* 第二次：server收到FIN，发送一个ACK到Client
	* 第三次：server 发送FIN。
	* 第四次：client 收到FIN，并发送ACK。
	* client 关闭，server关闭
### 差错控制
* 

	

