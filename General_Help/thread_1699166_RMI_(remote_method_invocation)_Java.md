---
title: "RMI (remote method invocation) Java"
date: 2011-03-03
forum: General Help
---

### Post by Stijn_Vdd on 2011-03-03
Hi,

First of all, my English isn't that good, so i'll try to write without spelling errors.

I Followed following tutorial for setup a RMI connection ([http://download.oracle.com/javase/1.5.0/docs/guide/rmi/hello/hello-world.html#4](http://download.oracle.com/javase/1.5.0/docs/guide/rmi/hello/hello-world.html#4))

The first time when i ran the client and the server (on the same computer) it all worked fine.
The second time that i tried to run the server following error occurd:

> java -classpath out example.hello.Server
Server exception: java.rmi.ServerException: RemoteException occurred in server thread; nested exception is: 
    java.rmi.UnmarshalException: error unmarshalling arguments; nested exception is: 
    java.lang.ClassNotFoundException: example.hello.Hello
java.rmi.ServerException: RemoteException occurred in server thread; nested exception is: 
    java.rmi.UnmarshalException: error unmarshalling arguments; nested exception is: 
    java.lang.ClassNotFoundException: example.hello.Hello
    at sun.rmi.server.UnicastServerRef.oldDispatch(UnicastServerRef.java:413)
    at sun.rmi.server.UnicastServerRef.dispatch(UnicastServerRef.java:267)
    at sun.rmi.transport.Transport$1.run(Transport.java:177)
    at java.security.AccessController.doPrivileged(Native Method)
    at sun.rmi.transport.Transport.serviceCall(Transport.java:173)
    at sun.rmi.transport.tcp.TCPTransport.handleMessages(TCPTransport.java:553)
    at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.run0(TCPTransport.java:808)
    at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.run(TCPTransport.java:667)
    at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1110)
    at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:603)
    at java.lang.Thread.run(Thread.java:636)
    at sun.rmi.transport.StreamRemoteCall.exceptionReceivedFromServer(StreamRemoteCall.java:273)
    at sun.rmi.transport.StreamRemoteCall.executeCall(StreamRemoteCall.java:251)
    at sun.rmi.server.UnicastRef.invoke(UnicastRef.java:377)
    at sun.rmi.registry.RegistryImpl_Stub.bind(Unknown Source)
    at example.hello.Server.main(Server.java:64)
Caused by: java.rmi.UnmarshalException: error unmarshalling arguments; nested exception is: 
    java.lang.ClassNotFoundException: example.hello.Hello
    at sun.rmi.registry.RegistryImpl_Skel.dispatch(Unknown Source)
    at sun.rmi.server.UnicastServerRef.oldDispatch(UnicastServerRef.java:403)
    at sun.rmi.server.UnicastServerRef.dispatch(UnicastServerRef.java:267)
    at sun.rmi.transport.Transport$1.run(Transport.java:177)
    at java.security.AccessController.doPrivileged(Native Method)
    at sun.rmi.transport.Transport.serviceCall(Transport.java:173)
    at sun.rmi.transport.tcp.TCPTransport.handleMessages(TCPTransport.java:553)
    at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.run0(TCPTransport.java:808)
    at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.run(TCPTransport.java:667)
    at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1110)
    at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:603)
    at java.lang.Thread.run(Thread.java:636)
Caused by: java.lang.ClassNotFoundException: example.hello.Hello
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:264)
    at sun.rmi.server.LoaderHandler.loadProxyInterfaces(LoaderHandler.java:728)
    at sun.rmi.server.LoaderHandler.loadProxyClass(LoaderHandler.java:672)
    at sun.rmi.server.LoaderHandler.loadProxyClass(LoaderHandler.java:609)
    at java.rmi.server.RMIClassLoader$2.loadProxyClass(RMIClassLoader.java:646)
    at java.rmi.server.RMIClassLoader.loadProxyClass(RMIClassLoader.java:311)
    at sun.rmi.server.MarshalInputStream.resolveProxyClass(MarshalInputStream.java:255)
    at java.io.ObjectInputStream.readProxyDesc(ObjectInputStream.java:1548)
    at java.io.ObjectInputStream.readClassDesc(ObjectInputStream.java:1510)
    at java.io.ObjectInputStream.readOrdinaryObject(ObjectInputStream.java:1749)
    at java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1346)
    at java.io.ObjectInputStream.readObject(ObjectInputStream.java:368)
    ... 12 more
First i thought it was because the name "Hello" already was registered to the rmiregistry, But trying with "Hallo2" didn't work.

Does someone know a possible solution ?

Kind regards!

---

