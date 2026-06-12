---
title: "Install MonoDevelop 1.1.14 the easy way"
date: 2006-04-03
forum: General Help
---

### Post by adamkane on 2006-04-03
Believe it or not, it is very easy to install MonoDevelop 1.1.14 on Breezy without installing any extra packages.

First download the Linux Installer for x86 to your desktop and install:
[http://www.mono-project.com/Downloads]("http://www.mono-project.com/Downloads")

```

cd ~/Desktop
wget  ftp://www.go-mono.com/archive/1.1.14/linux-installer/0/mono-1.1.14_0-installer.bin
sudo chmod +x mono-1.1.14_0-installer.bin
./mono-1.1.14_0-installer.bin

``` 
Installation proceeds and finishes.

```

cd ~/mono-1.1.14/bin
./monodevelop

``` 
Done. Easy.

For some reason, I wasn't able to install with sudo, and wasn't able to create a panel launcher. I don't know why. If someone figures it out, please share.

---

### Post by SreckoMicic on 2006-04-06
I have done as you sad but monodevelop doesn't start, when initializing it crash.:(

---

### Post by adamkane on 2006-04-09
I added the sudo chmod +x step. The installation should work now.

This thread is meant for Breezy users, who want to try the latest versions of MonoDevelop.

---

### Post by jdmpike on 2006-04-10
I followed your steps, but I am having the following errors...

```
System.Runtime.Remoting.RemotingException: Tcp transport error.

Server stack trace: 
in <0x0008f> System.Runtime.Remoting.Channels.Tcp.TcpMessageIO:ReceiveMessageStatus (System.IO.Stream networkStream, System.Byte[] buffer)
in <0x0017b> System.Runtime.Remoting.Channels.Tcp.TcpClientTransportSink:ProcessMessage (IMessage msg, ITransportHeaders requestHeaders, System.IO.Stream requestStream, ITransportHeaders responseHeaders, System.IO.Stream responseStream)
in <0x0023a> System.Runtime.Remoting.Channels.BinaryClientFormatterSink:SyncProcessMessage (IMessage msg)

Exception rethrown at [0]: 
 ---> System.Runtime.Remoting.RemotingException: Connection closed
in <0x0006d> System.Runtime.Remoting.Channels.Tcp.TcpMessageIO:StreamRead (System.IO.Stream networkStream, System.Byte[] buffer, Int32 count)
in <0x00044> System.Runtime.Remoting.Channels.Tcp.TcpMessageIO:ReceiveMessageStatus (System.IO.Stream networkStream, System.Byte[] buffer)--- End of inner exception stack trace ---

in <0x0008f> System.Runtime.Remoting.Channels.Tcp.TcpMessageIO:ReceiveMessageStatus (System.IO.Stream networkStream, System.Byte[] buffer)
in <0x0017b> System.Runtime.Remoting.Channels.Tcp.TcpClientTransportSink:ProcessMessage (IMessage msg, ITransportHeaders requestHeaders, System.IO.Stream requestStream, ITransportHeaders responseHeaders, System.IO.Stream responseStream)
in <0x0023a> System.Runtime.Remoting.Channels.BinaryClientFormatterSink:SyncProcessMessage (IMessage msg)
```

---

### Post by mriya3 on 2006-04-13
The installer works greate but in order to make Monodevelop runnable from the icon in the install directory I had to add the path definition (like the one added to ~/.bash_profile by the installer) in the <install directory>/bin/monodevelop script.

;) ;) ;)

---

### Post by kalamar on 2006-04-13
[QUOTE=jdmpike]I followed your steps, but I am having the following errors...

```
System.Runtime.Remoting.RemotingException: Tcp transport error.

Server stack trace: 
in <0x0008f> System.Runtime.Remoting.Channels.Tcp.TcpMessageIO:ReceiveMessageStatus (System.IO.Stream networkStream, System.Byte[] buffer)
in <0x0017b> System.Runtime.Remoting.Channels.Tcp.TcpClientTransportSink:ProcessMessage (IMessage msg, ITransportHeaders requestHeaders, System.IO.Stream requestStream, ITransportHeaders responseHeaders, System.IO.Stream responseStream)
in <0x0023a> System.Runtime.Remoting.Channels.BinaryClientFormatterSink:SyncProcessMessage (IMessage msg)

Exception rethrown at [0]: 
 ---> System.Runtime.Remoting.RemotingException: Connection closed
in <0x0006d> System.Runtime.Remoting.Channels.Tcp.TcpMessageIO:StreamRead (System.IO.Stream networkStream, System.Byte[] buffer, Int32 count)
in <0x00044> System.Runtime.Remoting.Channels.Tcp.TcpMessageIO:ReceiveMessageStatus (System.IO.Stream networkStream, System.Byte[] buffer)--- End of inner exception stack trace ---

in <0x0008f> System.Runtime.Remoting.Channels.Tcp.TcpMessageIO:ReceiveMessageStatus (System.IO.Stream networkStream, System.Byte[] buffer)
in <0x0017b> System.Runtime.Remoting.Channels.Tcp.TcpClientTransportSink:ProcessMessage (IMessage msg, ITransportHeaders requestHeaders, System.IO.Stream requestStream, ITransportHeaders responseHeaders, System.IO.Stream responseStream)
in <0x0023a> System.Runtime.Remoting.Channels.BinaryClientFormatterSink:SyncProcessMessage (IMessage msg)
```[/QUOTE]


I'm getting the exact same error.
what did you do to make it run?

---

### Post by adamkane on 2006-04-21
The TCP errors are over my head. How are you guys connected to the internet? Do you have a home network?

---

