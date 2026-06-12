---
title: "Very strange connection issue with java"
date: 2012-03-29
forum: General Help
---

### Post by false_chicken on 2012-03-29
I have been writing a java app that simply opens a socket and waits on a specified port for a connection. I have an android app that I threw together to communicate with it. All to learn java and both using a simple socket connection. Its been working well until last night I did an update with the update manager now my phone cannot communicate with the program. Sounds odd I know. I can run the server on my Windows 7 side, my netbook (Also running Xubuntu 11.10) and another Windows 7 computer in my house. The app I wrote for my phone can talk to all those other computers when running the server but not when I run it on my primary computer running Xubuntu 11.10. 

I do not understand what could be wrong. My phone can ping my PC and my PC can ping my phone. It makes no sense. When I found out it stopped working I was about to update my netbook as well via the update manager but now I don't think so. I hope this is not too vague. Any suggestions? Thanks.

3.0.0-17-generic-pae #30-Ubuntu SMP Thu Mar 8 17:53:35 UTC 2012 i686 athlon i386 GNU/Linux

[]("http://dl.dropbox.com/u/9159394/source.tar.gz")

---

### Post by Gremlinzzz on 2012-03-29
I'm sure it was the update.
When you update some things like driver or pluging  need to be reinstalled.

---

### Post by ofnuts on 2012-03-29
> **false_chicken said:**
> I have been writing a java app that simply opens a socket and waits on a specified port for a connection. I have an android app that I threw together to communicate with it. All to learn java and both using a simple socket connection. Its been working well until last night I did an update with the update manager now my phone cannot communicate with the program. Sounds odd I know. I can run the server on my Windows 7 side, my netbook (Also running Xubuntu 11.10) and another Windows 7 computer in my house. The app I wrote for my phone can talk to all those other computers when running the server but not when I run it on my primary computer running Xubuntu 11.10. 

I do not understand what could be wrong. My phone can ping my PC and my PC can ping my phone. It makes no sense. When I found out it stopped working I was about to update my netbook as well via the update manager but now I don't think so. I hope this is not too vague. Any suggestions? Thanks.

3.0.0-17-generic-pae #30-Ubuntu SMP Thu Mar 8 17:53:35 UTC 2012 i686 athlon i386 GNU/Linux

An update of what? The phone or the Linux PC? What says "netstat" on the computer that doesn't answer? Do you see the port listed?

---

### Post by Gremlinzzz on 2012-03-29
Its been working well until last night I did an update with the update manager now my phone cannot communicate with the program.I did get the feeling the update was the cause.It is a strange issue  the port you used is not being received by Xubuntu,maybe its something to do with Xubuntu security-firewall etc.

---

### Post by false_chicken on 2012-03-29
> **ofnuts said:**
> An update of what? The phone or the Linux PC? What says "netstat" on the computer that doesn't answer? Do you see the port listed?

An update to the computer. I wish I knew all the packages that where updated. But it was fairly recent. I update whenever the update manager asks. And as for the ports I have tried many none work. This makes absolutely no sense to me. I mean I am new to java and programming in general and I know my code may not be elegant but I know it works. It works on every other PC in my house except fully up to date linux machines. Just installed Mint 11 on an extra hard drive and fully updated. Same result. So I know it is affecting Xubuntu and Mint when updated to the latest. 

I am going to try to update my netbook (Xubuntu) and see if it stops working. I cannot get a very good diagnostic as my application just throws a null pointer exception :/. Which doesn't do much for figuring out the issue. But I can use iptraf and see that there is a connection being made. Its like the jre is not establishing the connection properly or something but it works everywhere else (On other computers). And I can do everything else on the PC. I can ping it, Access my shared files, get on the net, etc. so its not being blocked by anything.

Update: I do not see it in netstat. But I also do no see it when I run it on the netbook yet it works. 

Update 2: I have found that for some reason my updated computer (Running Mint right now) refuses connection. I wrote another simple desktop app to try to connect without my phone and I get connection refused when I try to connect to the server when running on my PC. But the same thing on my un-updated netbook works fine. So something is blocking it with the latest updates... How odd. Also I have found that I cannot just use the the lo adapter on my pc. If I try to connect that way (127.0.0.1) I still get refused. But I can run the client and server locally on my netbook and connect either way lo or over the network. This is so puzzling >_>.


Application source:
[http://dl.dropbox.com/u/9159394/source.tar.gz](http://dl.dropbox.com/u/9159394/source.tar.gz)

---

### Post by Gremlinzzz on 2012-03-29
I'm using Xubuntu 11.10 and i believe the last update i received a Kernel update.3.0.0-17-generic

---

### Post by ofnuts on 2012-03-29
> **false_chicken said:**
> An update to the computer. I wish I knew all the packages that where updated. But it was fairly recent. I update whenever the update manager asks. And as for the ports I have tried many none work. This makes absolutely no sense to me. I mean I am new to java and programming in general and I know my code may not be elegant but I know it works. It works on every other PC in my house except fully up to date linux machines. Just installed Mint 11 on an extra hard drive and fully updated. Same result. So I know it is affecting Xubuntu and Mint when updated to the latest. 

I am going to try to update my netbook (Xubuntu) and see if it stops working. I cannot get a very good diagnostic as my application just throws a null pointer exception :/. Which doesn't do much for figuring out the issue. But I can use iptraf and see that there is a connection being made. Its like the jre is not establishing the connection properly or something but it works everywhere else (On other computers). And I can do everything else on the PC. I can ping it, Access my shared files, get on the net, etc. so its not being blocked by anything.

Update: I do not see it in netstat. But I also do no see it when I run it on the netbook yet it works. 

Update 2: I have found that for some reason my updated computer (Running Mint right now) refuses connection. I wrote another simple desktop app to try to connect without my phone and I get connection refused when I try to connect to the server when running on my PC. But the same thing on my un-updated netbook works fine. So something is blocking it with the latest updates... How odd. Also I have found that I cannot just use the the lo adapter on my pc. If I try to connect that way (127.0.0.1) I still get refused. But I can run the client and server locally on my netbook and connect either way lo or over the network. This is so puzzling >_>.


Application source:
[http://dl.dropbox.com/u/9159394/source.tar.gz](http://dl.dropbox.com/u/9159394/source.tar.gz)
A NullPointerException usually says a lot in the stack trace... 

Looks like some firewall problem. What says:
```
[FONT=monospace]sudo ufw status
```[/FONT]
and
```
sudo iptables --list
```

---

### Post by false_chicken on 2012-03-30
> **ofnuts said:**
> A NullPointerException usually says a lot in the stack trace... 

Looks like some firewall problem. What says:
```
[FONT=monospace]sudo ufw status[/FONT]
```and
```
sudo iptables --list
```

Thanks for the reply!

ufw: Status: inactive

Iptables:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination


Application source:
[http://dl.dropbox.com/u/9159394/source.tar.gz](http://dl.dropbox.com/u/9159394/source.tar.gz)

---

### Post by ofnuts on 2012-03-30
> **false_chicken said:**
> Thanks for the reply!

ufw: Status: inactive

Iptables:

OK, so not a firewall problem. Next step, show source code, and show stack trace for the NullPointerExeception...

---

### Post by ofnuts on 2012-03-30
.

---

### Post by false_chicken on 2012-03-30
> **ofnuts said:**
> OK, so not a firewall problem. Next step, show source code, and show stack trace for the NullPointerExeception...


Server code:

```
private void Listen()
    {
        while (true)
        {
            
            while (!stopRequested)
            {
                
                try {
                    serverSock = new ServerSocket(port);
                    incomingSocket = serverSock.accept();
                    reader = new BufferedReader(new InputStreamReader(incomingSocket.getInputStream()));
                    message = reader.readLine();
                } catch (IOException e) {
                    e.printStackTrace();
                }
                
                try {
                    reader.close();
                    incomingSocket.close();
                    serverSock.close();
                } 
                catch (IOException e) 
                {
                    e.printStackTrace();
                }
                
                if (message != null)
                {
                    SplitMessage(message); //Split the password from the requested key
                    ParseInput(splitMessage); //Parse input which in turn passes the desired key to the input handler.
                }
                else
                {
                    //MainWindow.logger.LogMessage(4, "Message contained nothing.");
                }
            }
```Client:

```
try {
                    socket = new Socket("127.0.0.1", 6666);
                } catch (UnknownHostException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                } catch (IOException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
                DataOutputStream output = null;
                try {
                    output = new DataOutputStream(socket.getOutputStream());
                } catch (IOException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
                BufferedWriter writer = new BufferedWriter(new OutputStreamWriter(output));
                try {
                    writer.write("PASSWORD-KEY"); //Test message
                } catch (IOException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
                try {
                    writer.close();
                    socket.close();
                    output.close();
                
                } catch (IOException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
            }    
```Stack trace:
```

java.net.ConnectException: Connection refused
    at java.net.PlainSocketImpl.socketConnect(Native Method)
    at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:327)
    at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:193)
    at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:180)
    at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:384)
    at java.net.Socket.connect(Socket.java:546)
    at java.net.Socket.connect(Socket.java:495)
    at java.net.Socket.<init>(Socket.java:392)
    at java.net.Socket.<init>(Socket.java:206)
    at com.seriouspineapple.dcc.DesktopCommandController$2.actionPerformed(DesktopCommandController.java:59)
    at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:2012)
    at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2335)
    at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:404)
    at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:259)
    at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:253)
    at java.awt.Component.processMouseEvent(Component.java:6268)
    at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
    at java.awt.Component.processEvent(Component.java:6033)
    at java.awt.Container.processEvent(Container.java:2045)
    at java.awt.Component.dispatchEventImpl(Component.java:4629)
    at java.awt.Container.dispatchEventImpl(Container.java:2103)
    at java.awt.Component.dispatchEvent(Component.java:4455)
    at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4633)
    at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4297)
    at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4227)
    at java.awt.Container.dispatchEventImpl(Container.java:2089)
    at java.awt.Window.dispatchEventImpl(Window.java:2517)
    at java.awt.Component.dispatchEvent(Component.java:4455)
    at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:649)
    at java.awt.EventQueue.access$000(EventQueue.java:96)
    at java.awt.EventQueue$1.run(EventQueue.java:608)
    at java.awt.EventQueue$1.run(EventQueue.java:606)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
    at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:116)
    at java.awt.EventQueue$2.run(EventQueue.java:622)
    at java.awt.EventQueue$2.run(EventQueue.java:620)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:619)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
    at com.seriouspineapple.dcc.DesktopCommandController$2.actionPerformed(DesktopCommandController.java:69)
    at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:2012)
    at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2335)
    at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:404)
    at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:259)
    at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:253)
    at java.awt.Component.processMouseEvent(Component.java:6268)
    at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
    at java.awt.Component.processEvent(Component.java:6033)
    at java.awt.Container.processEvent(Container.java:2045)
    at java.awt.Component.dispatchEventImpl(Component.java:4629)
    at java.awt.Container.dispatchEventImpl(Container.java:2103)
    at java.awt.Component.dispatchEvent(Component.java:4455)
    at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4633)
    at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4297)
    at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4227)
    at java.awt.Container.dispatchEventImpl(Container.java:2089)
    at java.awt.Window.dispatchEventImpl(Window.java:2517)
    at java.awt.Component.dispatchEvent(Component.java:4455)
    at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:649)
    at java.awt.EventQueue.access$000(EventQueue.java:96)
    at java.awt.EventQueue$1.run(EventQueue.java:608)
    at java.awt.EventQueue$1.run(EventQueue.java:606)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
    at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:116)
    at java.awt.EventQueue$2.run(EventQueue.java:622)
    at java.awt.EventQueue$2.run(EventQueue.java:620)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:619)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

```There is a link in my previous post for the full source if desired. The NullPointerException seems to follow because of the connection being refused in the first place.

Its very strange to me. As said before it works on Windows 7 64-bit and any version of Linux (Ubuntu based) that I have tested pre-recent update. I just tested my Mint media center that was updated last night. Doesn't work there anymore either :/. Thanks for the help.

---

