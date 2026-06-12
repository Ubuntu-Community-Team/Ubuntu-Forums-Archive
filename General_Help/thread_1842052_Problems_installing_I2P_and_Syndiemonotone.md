---
title: "Problems installing I2P and Syndie/monotone"
date: 2011-09-10
forum: General Help
---

### Post by pyromaniacwolf1994 on 2011-09-10
Hey everyone I'm having problems installing monotone/Syndie and I2P everytime I try to install I get this error 

Failed to start org.hsqldb.Server.
See log file '/var/log/hsqldb.log'.
invoke-rc.d: initscript hsqldb-server, action "start" failed.
dpkg: error processing hsqldb-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 hsqldb-server
E: Sub-process /usr/bin/dpkg returned an error code (1)




so....suggestions?

---

### Post by pyromaniacwolf1994 on 2011-09-10
Okay I just checked the file mentioned in the error message /var/log/hsqldb.log and here's what it says: 

[Server@95fd19]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@95fd19]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@95fd19]: Startup sequence initiated from main() method
[Server@95fd19]: Loaded properties from [/var/lib/hsqldb/server.properties]
[Server@95fd19]: Initiating startup sequence...
[Server@95fd19]: [Thread[HSQLDB Server @95fd19,5,main]]: run()/openServerSocket(): 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:353)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.hsqldb.HsqlSocketFactory.createServerSocket(Unknown Source)
	at org.hsqldb.Server.openServerSocket(Unknown Source)
	at org.hsqldb.Server.run(Unknown Source)
	at org.hsqldb.Server.access$000(Unknown Source)
	at org.hsqldb.Server$ServerThread.run(Unknown Source)
[Server@95fd19]: Initiating shutdown sequence...
[Server@95fd19]: Shutdown sequence completed in 4 ms.
[Server@95fd19]: 2011-09-10 15:04:15.409 SHUTDOWN : System.exit() was not called
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@1f934ad]: Startup sequence initiated from main() method
[Server@1f934ad]: Loaded properties from [/var/lib/hsqldb/server.properties]
[Server@1f934ad]: Initiating startup sequence...
[Server@1f934ad]: [Thread[HSQLDB Server @1f934ad,5,main]]: run()/openServerSocket(): 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:353)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.hsqldb.HsqlSocketFactory.createServerSocket(Unknown Source)
	at org.hsqldb.Server.openServerSocket(Unknown Source)
	at org.hsqldb.Server.run(Unknown Source)
	at org.hsqldb.Server.access$000(Unknown Source)
	at org.hsqldb.Server$ServerThread.run(Unknown Source)
[Server@1f934ad]: Initiating shutdown sequence...
[Server@1f934ad]: Shutdown sequence completed in 3 ms.
[Server@1f934ad]: 2011-09-10 15:04:18.241 SHUTDOWN : System.exit() was not called
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@1f934ad]: Startup sequence initiated from main() method
[Server@1f934ad]: Loaded properties from [/var/lib/hsqldb/server.properties]
[Server@1f934ad]: Initiating startup sequence...
[Server@1f934ad]: [Thread[HSQLDB Server @1f934ad,5,main]]: run()/openServerSocket(): 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:353)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.hsqldb.HsqlSocketFactory.createServerSocket(Unknown Source)
	at org.hsqldb.Server.openServerSocket(Unknown Source)
	at org.hsqldb.Server.run(Unknown Source)
	at org.hsqldb.Server.access$000(Unknown Source)
	at org.hsqldb.Server$ServerThread.run(Unknown Source)
[Server@1f934ad]: Initiating shutdown sequence...
[Server@1f934ad]: Shutdown sequence completed in 4 ms.
[Server@1f934ad]: 2011-09-10 15:06:30.058 SHUTDOWN : System.exit() was not called
[Server@1f14ceb]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@1f14ceb]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@1f14ceb]: Startup sequence initiated from main() method
[Server@1f14ceb]: Loaded properties from [/var/lib/hsqldb/server.properties]
[Server@1f14ceb]: Initiating startup sequence...
[Server@1f14ceb]: [Thread[HSQLDB Server @1f14ceb,5,main]]: run()/openServerSocket(): 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:353)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.hsqldb.HsqlSocketFactory.createServerSocket(Unknown Source)
	at org.hsqldb.Server.openServerSocket(Unknown Source)
	at org.hsqldb.Server.run(Unknown Source)
	at org.hsqldb.Server.access$000(Unknown Source)
	at org.hsqldb.Server$ServerThread.run(Unknown Source)
[Server@1f14ceb]: Initiating shutdown sequence...
[Server@1f14ceb]: Shutdown sequence completed in 4 ms.
[Server@1f14ceb]: 2011-09-10 15:13:41.709 SHUTDOWN : System.exit() was not called
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@1f934ad]: Startup sequence initiated from main() method
[Server@1f934ad]: Loaded properties from [/var/lib/hsqldb/server.properties]
[Server@1f934ad]: Initiating startup sequence...
[Server@1f934ad]: [Thread[HSQLDB Server @1f934ad,5,main]]: run()/openServerSocket(): 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:353)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.hsqldb.HsqlSocketFactory.createServerSocket(Unknown Source)
	at org.hsqldb.Server.openServerSocket(Unknown Source)
	at org.hsqldb.Server.run(Unknown Source)
	at org.hsqldb.Server.access$000(Unknown Source)
	at org.hsqldb.Server$ServerThread.run(Unknown Source)
[Server@1f934ad]: Initiating shutdown sequence...
[Server@1f934ad]: Shutdown sequence completed in 3 ms.
[Server@1f934ad]: 2011-09-10 15:13:43.747 SHUTDOWN : System.exit() was not called
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@1f934ad]: Startup sequence initiated from main() method
[Server@1f934ad]: Loaded properties from [/var/lib/hsqldb/server.properties]
[Server@1f934ad]: Initiating startup sequence...
[Server@1f934ad]: [Thread[HSQLDB Server @1f934ad,5,main]]: run()/openServerSocket(): 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:353)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.hsqldb.HsqlSocketFactory.createServerSocket(Unknown Source)
	at org.hsqldb.Server.openServerSocket(Unknown Source)
	at org.hsqldb.Server.run(Unknown Source)
	at org.hsqldb.Server.access$000(Unknown Source)
	at org.hsqldb.Server$ServerThread.run(Unknown Source)
[Server@1f934ad]: Initiating shutdown sequence...
[Server@1f934ad]: Shutdown sequence completed in 4 ms.
[Server@1f934ad]: 2011-09-10 15:14:49.708 SHUTDOWN : System.exit() was not called
[Server@1f14ceb]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@1f14ceb]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@1f14ceb]: Startup sequence initiated from main() method
[Server@1f14ceb]: Loaded properties from [/var/lib/hsqldb/server.properties]
[Server@1f14ceb]: Initiating startup sequence...
[Server@1f14ceb]: [Thread[HSQLDB Server @1f14ceb,5,main]]: run()/openServerSocket(): 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:353)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.hsqldb.HsqlSocketFactory.createServerSocket(Unknown Source)
	at org.hsqldb.Server.openServerSocket(Unknown Source)
	at org.hsqldb.Server.run(Unknown Source)
	at org.hsqldb.Server.access$000(Unknown Source)
	at org.hsqldb.Server$ServerThread.run(Unknown Source)
[Server@1f14ceb]: Initiating shutdown sequence...
[Server@1f14ceb]: Shutdown sequence completed in 3 ms.
[Server@1f14ceb]: 2011-09-10 15:16:09.963 SHUTDOWN : System.exit() was not called
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@1f934ad]: Startup sequence initiated from main() method
[Server@1f934ad]: Loaded properties from [/var/lib/hsqldb/server.properties]
[Server@1f934ad]: Initiating startup sequence...
[Server@1f934ad]: [Thread[HSQLDB Server @1f934ad,5,main]]: run()/openServerSocket(): 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:353)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.hsqldb.HsqlSocketFactory.createServerSocket(Unknown Source)
	at org.hsqldb.Server.openServerSocket(Unknown Source)
	at org.hsqldb.Server.run(Unknown Source)
	at org.hsqldb.Server.access$000(Unknown Source)
	at org.hsqldb.Server$ServerThread.run(Unknown Source)
[Server@1f934ad]: Initiating shutdown sequence...
[Server@1f934ad]: Shutdown sequence completed in 3 ms.
[Server@1f934ad]: 2011-09-10 15:19:54.229 SHUTDOWN : System.exit() was not called
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@1f934ad]: Startup sequence initiated from main() method
[Server@1f934ad]: Loaded properties from [/var/lib/hsqldb/server.properties]
[Server@1f934ad]: Initiating startup sequence...
[Server@1f934ad]: [Thread[HSQLDB Server @1f934ad,5,main]]: run()/openServerSocket(): 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:353)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.hsqldb.HsqlSocketFactory.createServerSocket(Unknown Source)
	at org.hsqldb.Server.openServerSocket(Unknown Source)
	at org.hsqldb.Server.run(Unknown Source)
	at org.hsqldb.Server.access$000(Unknown Source)
	at org.hsqldb.Server$ServerThread.run(Unknown Source)
[Server@1f934ad]: Initiating shutdown sequence...
[Server@1f934ad]: Shutdown sequence completed in 3 ms.
[Server@1f934ad]: 2011-09-10 15:21:26.727 SHUTDOWN : System.exit() was not called
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@1f934ad]: Startup sequence initiated from main() method
[Server@1f934ad]: Loaded properties from [/var/lib/hsqldb/server.properties]
[Server@1f934ad]: Initiating startup sequence...
[Server@1f934ad]: [Thread[HSQLDB Server @1f934ad,5,main]]: run()/openServerSocket(): 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:353)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.hsqldb.HsqlSocketFactory.createServerSocket(Unknown Source)
	at org.hsqldb.Server.openServerSocket(Unknown Source)
	at org.hsqldb.Server.run(Unknown Source)
	at org.hsqldb.Server.access$000(Unknown Source)
	at org.hsqldb.Server$ServerThread.run(Unknown Source)
[Server@1f934ad]: Initiating shutdown sequence...
[Server@1f934ad]: Shutdown sequence completed in 4 ms.
[Server@1f934ad]: 2011-09-10 15:21:28.356 SHUTDOWN : System.exit() was not called
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@1f934ad]: Startup sequence initiated from main() method
[Server@1f934ad]: Loaded properties from [/var/lib/hsqldb/server.properties]
[Server@1f934ad]: Initiating startup sequence...
[Server@1f934ad]: [Thread[HSQLDB Server @1f934ad,5,main]]: run()/openServerSocket(): 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:353)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.hsqldb.HsqlSocketFactory.createServerSocket(Unknown Source)
	at org.hsqldb.Server.openServerSocket(Unknown Source)
	at org.hsqldb.Server.run(Unknown Source)
	at org.hsqldb.Server.access$000(Unknown Source)
	at org.hsqldb.Server$ServerThread.run(Unknown Source)
[Server@1f934ad]: Initiating shutdown sequence...
[Server@1f934ad]: Shutdown sequence completed in 3 ms.
[Server@1f934ad]: 2011-09-10 15:27:45.312 SHUTDOWN : System.exit() was not called
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@1f934ad]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@1f934ad]: Startup sequence initiated from main() method
[Server@1f934ad]: Loaded properties from [/var/lib/hsqldb/server.properties]
[Server@1f934ad]: Initiating startup sequence...
[Server@1f934ad]: [Thread[HSQLDB Server @1f934ad,5,main]]: run()/openServerSocket(): 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:353)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.hsqldb.HsqlSocketFactory.createServerSocket(Unknown Source)
	at org.hsqldb.Server.openServerSocket(Unknown Source)
	at org.hsqldb.Server.run(Unknown Source)
	at org.hsqldb.Server.access$000(Unknown Source)
	at org.hsqldb.Server$ServerThread.run(Unknown Source)
[Server@1f934ad]: Initiating shutdown sequence...
[Server@1f934ad]: Shutdown sequence completed in 3 ms.
[Server@1f934ad]: 2011-09-10 15:30:27.936 SHUTDOWN : System.exit() was not called

---

