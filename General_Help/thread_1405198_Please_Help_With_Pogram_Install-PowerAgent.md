---
title: "Please Help With Pogram Install-PowerAgent"
date: 2010-02-12
forum: General Help
---

### Post by seahuston on 2010-02-12
Hi All,

I've just gotten Ubuntu 9.10 and am dual booting it with Windows 7. I am working towards only using 7 for Solidworks(a CAD type program that doesnt look to work with Ubuntu). 
The only other thing I have been needing 7 for is this program called PowerAgent. Its a program which imports data from a cycling computer(odometer/speedometer type thing) and allows you to view your rides and send them to others, like a coach.
There is a build for linux but I cant find any way to install it. The download page is here:
[http://www.saris.com/t-powerAgentDownload.aspx](http://www.saris.com/t-powerAgentDownload.aspx)
I download the linux pack and extracted it. I followed the instructions for making sure the poweragent file in bin was set to execute and when i went to run it nothing happened. I tried running it in the terminal but that just opened for a split second and then closed. I tried opening one of the included .exe files and got this.
Archive:  /home/seahuston/Downloads/poweragent_7.4.5.6_linux-x86/poweragent/bin/poweragent.exe
[/home/seahuston/Downloads/poweragent_7.4.5.6_linux-x86/poweragent/bin/poweragent.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/seahuston/Downloads/poweragent_7.4.5.6_linux-x86/poweragent/bin/poweragent.exe or
          /home/seahuston/Downloads/poweragent_7.4.5.6_linux-x86/poweragent/bin/poweragent.exe.zip, and cannot find /home/seahuston/Downloads/poweragent_7.4.5.6_linux-x86/poweragent/bin/poweragent.exe.ZIP, period.

Also, I tried the windows version with Wine and the program installed but the USB drivers (the bike computer connects by USB) did not work.

So, I am hoping that someone would be able to help out. This would be a huge help for me and I would greatly appreciate anyone that can help install the Linux version or get the program working some how.

Thanks!

---

### Post by Amzo2 on 2010-02-12
Follow these steps in a terminal, it worked for me.

```
cd ~/
wget http://www.saris.com/download/PA745/poweragent_7.4.5.6_linux-x86.tar.gz
tar -zxf poweragent_7.4.5.6_linux-x86.tar.gz
cd poweragent/
cd bin
chmod a+x poweragent
./poweragent
```

---

### Post by seahuston on 2010-02-12
Hi,

Thank you very much for the quick reply. I tried using your mentioned steps and had good luck until the final step (I believe the executing of the executible). I recived this error Cannot find java. Please use the --jdkhome switch.
I figured this would be a problem with Java so I (re?)installed java. This install went fine but I still could get poweragent to work.
Any suggestions?

---

### Post by seahuston on 2010-02-13
So,

I figured it out by doing some searching and some trial and error. I havent tried the connection yet since I am away from home at the moment. Apparently I need to locate the Java directory when running poweragent. below is the command I used in the terminal

~/poweragent/bin$ ./poweragent --jdkhome /usr/java/jre1.6.0_18

My last question is where should I located the poweragent folder and the java folder. I am still a bit new to the linux file management.

---

### Post by Amzo2 on 2010-02-13
You could just make a launcher on your desktop and keep the folder where it is, or you could create a symbolic link to /usr/bin/.

---

### Post by seahuston on 2010-02-13
I made a launcher on my desktop but I dont really want to have a mess of files everywhere.
Thanks for all your help!

---

### Post by seahuston on 2010-02-13
So, 
I think I spoke to soon.
When I went to download data I got an error saying that the USB drivers need to be reinstalled. I downloaded them but didnt know what to do next. Here is the error:

Communication Error
 

Message:
    java.lang.UnsatisfiedLinkError: /tmp/libd2xx-linux.so: /tmp/libd2xx-linux.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
Level:
    SEVERE
Stack Trace:
    java.lang.ClassLoader$NativeLibrary.load(Native Method)
    java.lang.ClassLoader.loadLibrary0(Unknown Source)
    java.lang.ClassLoader.loadLibrary(Unknown Source)
    java.lang.Runtime.load0(Unknown Source)
    java.lang.System.load(Unknown Source)
    com.cycleops.d2xx.Library.loadLibrary(Unknown Source)
    com.cycleops.d2xx.D2xx. (Unknown Source)
    com.cycleops.jpowertap.Manager.getConnectedDevices(Manager.java:120)
    com.cycleops.devicemanager.DeviceManager.getSelectedDevice(DeviceManager.java:52)
    com.cycleops.devicemanager.DeviceManager.getSelectedDevice(DeviceManager.java:41)
    com.cycleops.devicemanager.DownloadDeviceAction.performAction(DownloadDeviceAction.java:83)
    org.openide.util.actions.CallableSystemAction$1.run(CallableSystemAction.java:118)
    org.netbeans.modules.openide.util.ActionsBridge.doPerformAction(ActionsBridge.java:77)
    org.openide.util.actions.CallableSystemAction.actionPerformed(CallableSystemAction.java:114)
    javax.swing.AbstractButton.fireActionPerformed(Unknown Source)
    javax.swing.AbstractButton$Handler.actionPerformed(Unknown Source)
    javax.swing.DefaultButtonModel.fireActionPerformed(Unknown Source)
    javax.swing.DefaultButtonModel.setPressed(Unknown Source)
    javax.swing.plaf.basic.BasicButtonListener.mouseReleased(Unknown Source)
    java.awt.AWTEventMulticaster.mouseReleased(Unknown Source)
    java.awt.AWTEventMulticaster.mouseReleased(Unknown Source)
    java.awt.Component.processMouseEvent(Unknown Source)
    javax.swing.JComponent.processMouseEvent(Unknown Source)
    org.openide.awt.ToolbarButton.processMouseEvent(ToolbarButton.java:61)
    java.awt.Component.processEvent(Unknown Source)
    java.awt.Container.processEvent(Unknown Source)
    java.awt.Component.dispatchEventImpl(Unknown Source)
    java.awt.Container.dispatchEventImpl(Unknown Source)
    java.awt.Component.dispatchEvent(Unknown Source)
    java.awt.LightweightDispatcher.retargetMouseEvent(Unknown Source)
    java.awt.LightweightDispatcher.processMouseEvent(Unknown Source)
    java.awt.LightweightDispatcher.dispatchEvent(Unknown Source)
    java.awt.Container.dispatchEventImpl(Unknown Source)
    java.awt.Window.dispatchEventImpl(Unknown Source)
    java.awt.Component.dispatchEvent(Unknown Source)
    java.awt.EventQueue.dispatchEvent(Unknown Source)
    org.netbeans.core.TimableEventQueue.dispatchEvent(TimableEventQueue.java:104)
    java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source)
    java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source)
    java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
    java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    java.awt.EventDispatchThread.run(Unknown Source)

---

