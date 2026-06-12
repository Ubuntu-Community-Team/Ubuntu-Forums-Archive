---
title: "Ubuntu 12.04 - Lotus Notes Not Rendering?"
date: 2012-04-29
forum: General Help
---

### Post by A4orce84 on 2012-04-29
Hello Everyone,

I am trying to get Lotus Notes 8.5.x working in Ubuntu. I had it working in Ubuntu 11.04/11.10, with a hack with some older files, but trying to get it to work in 12.04 isn't working correctly.

It fires up, but when clicking on any email, the body is displayed in a black/grey box.

Has anyone figured out how to get this working correctly? In addition, my Sametime IMs do not work either.  =(

Thanks,

--Asif

---

### Post by oasit on 2012-04-29
Hello Asif

I had the same problem with a fresh installed 12.04.
To fix this problem you have to create and install the gdk-fix as described in steps 9+10 here [http://usablesoftware.wordpress.com/2011/10/10/install-lotus-notes-8-5-3-en-on-ubuntu-11-04-64bit/](http://usablesoftware.wordpress.com/2011/10/10/install-lotus-notes-8-5-3-en-on-ubuntu-11-04-64bit/)

I have attached the compiled libnotesgtkfix.so and notes-wrapper for your convenience.

Regards
Miguel

---

### Post by A4orce84 on 2012-04-29
Thanks oasit, few questions though:

1. Does it matter I am running 32bit version of Ubuntu 12.04?

2. Reading the instructions, I'm a bit confused. Do I drop both these files in "/opt/ibm/lotus/notes" and start the notes-wrapper?

Sorry I'm being a bit difficult, just never had to do so much tweaking before.

Thanks in advance!

---

### Post by oasit on 2012-04-30
> 1. Does it matter I am running 32bit version of Ubuntu 12.04?Its better if you run a 32bit Version because Notes officially supports only 32bit.
With 32bit you can omit steps 4-7 (see [http://usablesoftware.wordpress.com/2011/10/10/install-lotus-notes-8-5-3-en-on-ubuntu-11-04-64bit/#comment-498](http://usablesoftware.wordpress.com/2011/10/10/install-lotus-notes-8-5-3-en-on-ubuntu-11-04-64bit/#comment-498)).


> 2. Reading the instructions, I'm a bit confused. Do I drop both these files in "/opt/ibm/lotus/notes" and start the notes-wrapper?Mostly ;-) I suggest to to the following:


[LIST=1]
[*]Download attachment and extract it.
[*]Open a Terminal
[*]cd to the extracted folder.
[*]Now do
```
chmod +x notes-wrapper
sudo cp notes-wrapper libnotesgtkfix.so /opt/ibm/lotus/notes/
sudo sed -i 's/..\/notes %F/..\/notes-wrapper %F/g' /usr/share/applications/LotusNotes8.5.desktop
```
[/LIST]

Start Notes. Rendering issues should have gnone.

Regards
Miguel

---

### Post by A4orce84 on 2012-04-30
When doing the commands I see the following:

```

aahmad@aahmad-LT:~/Downloads/sgh-lotus-notes_gtk2.23.3-2028e8e$ chmod +x notes-wrapper
aahmad@aahmad-LT:~/Downloads/sgh-lotus-notes_gtk2.23.3-2028e8e$ ll
total 32
drwxrwxr-x 2 aahmad aahmad 4096 Apr 29 16:56 ./
drwxr-xr-x 4 aahmad aahmad 4096 Apr 29 17:58 ../
-rw-rw-r-- 1 aahmad aahmad 1078 May 24  2011 libnotesgtkfix.c
-rwxrwxr-x 1 aahmad aahmad 6835 Apr 29 16:56 libnotesgtkfix.so*
-rw-rw-r-- 1 aahmad aahmad  145 May 24  2011 Makefile
-rwxr-xr-x 1 aahmad aahmad   78 May 24  2011 notes-wrapper*
-rw-rw-r-- 1 aahmad aahmad  866 May 24  2011 README
aahmad@aahmad-LT:~/Downloads/sgh-lotus-notes_gtk2.23.3-2028e8e$ sudo cp notes-wrapper libnotesgtkfix.so /opt/ibm/lotus/notes/
[sudo] password for aahmad: 
aahmad@aahmad-LT:~/Downloads/sgh-lotus-notes_gtk2.23.3-2028e8e$ sudo sed -i 's/..\/notes %F/..\/notes-wrapper %F/g' /usr/share/applications/LotusNotes8.5.desktop
sed: can't read /usr/share/applications/LotusNotes8.5.desktop: No such file or directory



```


Not sure about the last command as you can see, I got a "No such file or directory" error.

In addition, my sametime chat windows are still busted. Any clue on that?

Thanks.

---

### Post by oasit on 2012-04-30
>  In addition, my sametime chat windows are still busted. Any clue on that?This is because the last command failed.
It seems your desktop-file to start Notes has an other name.


Go to /usr/share/applications and look for the desktop entry of Notes.
Replace the red part in 
```
sudo sed -i 's/..\/notes %F/..\/notes-wrapper %F/g' [COLOR=Red]/usr/share/applications/LotusNotes8.5.desktop[/COLOR]
``` with the path to your Notes-Starter.


Regards
Michael

---

### Post by A4orce84 on 2012-04-30
Finally got the command to work, Sametime and rendering still is busted unfortunately.

Any other thoughts?

--Asif

---

### Post by oasit on 2012-04-30
> **A4orce84 said:**
> Finally got the command to work, Sametime and rendering still is busted unfortunately.

What happens if you start Notes with this command in Terminal?
```
/opt/ibm/lotus/notes/framework/../notes-wrapper
```If its the same there are maybe some depencies missing.
Try
```
sudo apt-get -y install libgnomeprintui2.2-0 ia32-libs-multiarch  ttf-xfree86-nonfree t1-xfree86-nonfree libgnomevfs2 libgnome2-0  libgnomeui
```Regards
Michael

---

### Post by alktlr on 2012-05-01
Opening a sametime window gives the following stack trace. I'm on LN 8.5 and 64 bit. Except for sametime LN is useable.

```
2012/05/01 15:20:58.938 WARNING null ::class.method=com.ibm.collaboration.realtime.browser.Browser.<init>() ::thread=main ::loggername=com.ibm.collaboration.realtime.browser

        java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
        at java.lang.reflect.Constructor.newInstance(Unknown Source)
        at com.ibm.collaboration.realtime.browser.Browser.<init>(Unknown Source)
        at com.ibm.collaboration.realtime.chatwindow.ui.BrowserChatTranscript.createControl(Unknown Source)
        at com.ibm.collaboration.realtime.chatwindow.ImChatWindowHandler.initWindow(Unknown Source)
        at com.ibm.collaboration.realtime.chatwindow.ImChatController.handleCreateChatHandler(Unknown Source)
        at com.ibm.collaboration.realtime.chatwindow.ImChatEventHandler.guiHandleMessageEvent(Unknown Source)
        at com.ibm.collaboration.realtime.magiccarpet.MessageEventGuiAdapter$_MessageEventHandler.run(Unknown Source)
        at org.eclipse.swt.widgets.RunnableLock.run(Unknown Source)
        at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Unknown Source)
        at org.eclipse.swt.widgets.Display.runAsyncMessages(Unknown Source)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
        at org.eclipse.ui.internal.Workbench.runEventLoop(Unknown Source)
        at org.eclipse.ui.internal.Workbench.runUI(Unknown Source)
        at org.eclipse.ui.internal.Workbench.access$4(Unknown Source)
        at org.eclipse.ui.internal.Workbench$5.run(Unknown Source)
        at org.eclipse.core.databinding.observable.Realm.runWithDefault(Unknown Source)
        at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Unknown Source)
        at org.eclipse.ui.PlatformUI.createAndRunWorkbench(Unknown Source)
        at com.ibm.rcp.personality.framework.internal.RCPApplication.run(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at org.eclipse.equinox.internal.app.EclipseAppContainer.callMethodWithException(Unknown Source)
        at org.eclipse.equinox.internal.app.EclipseAppHandle.run(Unknown Source)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(Unknown Source)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(Unknown Source)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(Unknown Source)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at org.eclipse.equinox.launcher.Main.invokeFramework(Unknown Source)
        at org.eclipse.equinox.launcher.Main.basicRun(Unknown Source)
        at org.eclipse.equinox.launcher.Main.run(Unknown Source)
        at com.ibm.rcp.core.internal.launcher.Main.startLaunch(Unknown Source)
        at com.ibm.rcp.core.internal.launcher.Main.main(Unknown Source)
        at com.ibm.rcp.core.internal.launcher.Main.run(Unknown Source)
Caused by: org.eclipse.swt.SWTError: XPCOM error -2147467259
        at org.eclipse.swt.browser.Mozilla.error(Unknown Source)
        at org.eclipse.swt.browser.Mozilla.create(Unknown Source)
        at org.eclipse.swt.browser.Browser.<init>(Unknown Source)
        ... 42 more
2012/05/01 15:20:58.946 WARNING null ::class.method=com.ibm.collaboration.realtime.magiccarpet.MessageEventGuiAdapter$_MessageEventHandler.run() ::thread=main ::loggername=com.ibm.collaboration.realtime.magiccarpet

        java.lang.NullPointerException
        at com.ibm.collaboration.realtime.browser.swt.BrowserService.addLocationListener(Unknown Source)
        at com.ibm.collaboration.realtime.browser.Browser.addLocationListener(Unknown Source)
        at com.ibm.collaboration.realtime.chatwindow.ui.BrowserChatTranscript.createControl(Unknown Source)
        at com.ibm.collaboration.realtime.chatwindow.ImChatWindowHandler.initWindow(Unknown Source)
        at com.ibm.collaboration.realtime.chatwindow.ImChatController.handleCreateChatHandler(Unknown Source)
        at com.ibm.collaboration.realtime.chatwindow.ImChatEventHandler.guiHandleMessageEvent(Unknown Source)
        at com.ibm.collaboration.realtime.magiccarpet.MessageEventGuiAdapter$_MessageEventHandler.run(Unknown Source)
        at org.eclipse.swt.widgets.RunnableLock.run(Unknown Source)
        at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Unknown Source)
        at org.eclipse.swt.widgets.Display.runAsyncMessages(Unknown Source)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
        at org.eclipse.ui.internal.Workbench.runEventLoop(Unknown Source)
        at org.eclipse.ui.internal.Workbench.runUI(Unknown Source)
        at org.eclipse.ui.internal.Workbench.access$4(Unknown Source)
        at org.eclipse.ui.internal.Workbench$5.run(Unknown Source)
        at org.eclipse.core.databinding.observable.Realm.runWithDefault(Unknown Source)
        at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Unknown Source)
        at org.eclipse.ui.PlatformUI.createAndRunWorkbench(Unknown Source)
        at com.ibm.rcp.personality.framework.internal.RCPApplication.run(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at org.eclipse.equinox.internal.app.EclipseAppContainer.callMethodWithException(Unknown Source)
        at org.eclipse.equinox.internal.app.EclipseAppHandle.run(Unknown Source)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(Unknown Source)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(Unknown Source)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(Unknown Source)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at org.eclipse.equinox.launcher.Main.invokeFramework(Unknown Source)
        at org.eclipse.equinox.launcher.Main.basicRun(Unknown Source)
        at org.eclipse.equinox.launcher.Main.run(Unknown Source)
        at com.ibm.rcp.core.internal.launcher.Main.startLaunch(Unknown Source)
        at com.ibm.rcp.core.internal.launcher.Main.main(Unknown Source)
        at com.ibm.rcp.core.internal.launcher.Main.run(Unknown Source)
```

---

### Post by A4orce84 on 2012-05-01
So to give answers to your responses:

Running the following command fires up Notes as usual:
/opt/ibm/lotus/notes/framework/../notes-wrapper

This is the following that is printed out in the terminal
```

aahmad@aahmad-LT:~$ /opt/ibm/lotus/notes/framework/../notes-wrapper

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes:4829): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

(notes:4829): Gdk-CRITICAL **: IA__gdk_x11_atom_to_xatom_for_display: assertion `atom != GDK_NONE' failed
05/01/2012 10:15:37.05 AM [04829:00002--1282987264] DeskClientOpenInt> Calling CreateProgramRCP pszRCPCmdLine[/authenticate ] bDeskProvisioningRestart [0]
05/01/2012 10:15:37.06 AM [04829:00002--1282987264] DeskClientOpenInt> Executed CreateProgramRCP

2012/05/01 10:15:37.875 CONFIG eclipse.buildId=client_620_20081114-0851
java.fullversion=J2RE 1.6.0 IBM J9 2.4 Linux x86-32 jvmxi3260ifx-20081002_23977 (JIT enabled, AOT enabled)
J9VM - 20081002_023977_lHdSMr
JIT  - r9_20080415_1520ifx7
GC   - 20080415_AA
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  -dir ltr -NPARAMS "/authenticate" -RPARAMS -personality com.ibm.rcp.platform.personality -product com.ibm.rcp.personality.framework.RCPProduct:com.ibm.notes.branding.notes -plugincustomization /opt/ibm/lotus/notes/framework/rcp/plugin_customization.ini
Command-line arguments:  -os linux -ws gtk -arch x86 -dir ltr -NPARAMS "/authenticate" -RPARAMS -personality com.ibm.rcp.platform.personality -product com.ibm.rcp.personality.framework.RCPProduct:com.ibm.notes.branding.notes -data /home/aahmad/lotus/notes/data/workspace -plugincustomization /opt/ibm/lotus/notes/framework/rcp/plugin_customization.ini ::class.method=com.ibm.rcp.core.internal.logger.frameworkhook.writeSession() ::thread=Start Level Event Dispatcher ::loggername=com.ibm.rcp.core.internal.logger.frameworkhook

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(notes2:4836): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

(notes:4829): Gdk-CRITICAL **: IA__gdk_x11_atom_to_xatom_for_display: assertion `atom != GDK_NONE' failed

```



I tried running your command for the dependencies, but got the following error:
```
aahmad@aahmad-LT:~$ sudo apt-get -y install libgnomeprintui2.2-0 ia32-libs-multiarch  ttf-xfree86-nonfree t1-xfree86-nonfree libgnomevfs2 libgnome2-0  libgnomeui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgnomevfs2
E: Unable to locate package libgnomeui
aahmad@aahmad-LT:~$ 

```

Finally, I thought I'd attach an image of what I'm actually seeing when I double click on an email. Please note this rendering issues does not happen with ALL emails, only some of them:

[IMG]http://img.photobucket.com/albums/v405/A4orce84/Screenshotfrom2012-05-01101425.png[/IMG]


Thank you for your time and help so far, it is greatly appreciated!


--Asif

---

### Post by oasit on 2012-05-01
Hello Asif

```
Running the following command fires up Notes as usual:
```So notes-wrapper seems to work.

```
Please note this rendering issues does not happen with ALL emails, only some of them
```Thanks for the screenshot. I had exactly the same behaviour.



```
E: Unable to locate package libgnomevfs2
E: Unable to locate package libgnomeui

```I had the same problem. Try to get the packages from a mirror server and install manually.

I got mine from here:

[LIST]
[*][http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu//pool/main/g/gnome-vfs/libgnomevfs2-common_2.24.4-1ubuntu2_all.deb](http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu//pool/main/g/gnome-vfs/libgnomevfs2-common_2.24.4-1ubuntu2_all.deb)
[*][http://ubuntu.mirrors.tds.net/pub/ubuntu//pool/main/libg/libgnomeui/libgnomeui-0_2.24.5-2ubuntu2_i386.deb](http://ubuntu.mirrors.tds.net/pub/ubuntu//pool/main/libg/libgnomeui/libgnomeui-0_2.24.5-2ubuntu2_i386.deb)
[/LIST]

I hope this resolves your issues.

Regards
Miguel

---

### Post by A4orce84 on 2012-05-01
Hey Miguel,

Looks like I already had those packages. I tried reinstalling it through gdebi this time, but there is no change unfortunately.  =(


--Asif

---

### Post by oasit on 2012-05-02
Asif

```
but there is no change unfortunately.  =(
```It maybe helps to try it from scratch.
Follow this guide: [http://usablesoftware.wordpress.com/2012/04/23/quick-n-dirty-install-guide-lotus-notes-8-5-x-on-ubuntu-12-04-32bit/](http://usablesoftware.wordpress.com/2012/04/23/quick-n-dirty-install-guide-lotus-notes-8-5-x-on-ubuntu-12-04-32bit/)

If the rendering issue stays, do the libnotesgtkfix/notewrapper thing (see comment #4).

Regards
Miguel

---

### Post by princefarhaan on 2012-05-05
Assalamalaikum Asif,

Paste these three files in the /opt/ibm/lotus/notes folder and change their permissions to 755 and then start lotus notes... worked for me on a 32 bit 12.04 machine.

There is also a fourth file that is required but I am not able to attach it here because of the file size contraint, you can search for and download - libgtk-x11-2.0.so

---

### Post by fakrulalam on 2012-05-07
Solution works like charm. Thanks Asif for your solution.

---

### Post by cutechaps on 2012-05-08
Asif

I too have same problem can you upload the remaining one .so file or can you get me link to download. I tried to download it from couple of sites no luck still I am unable to view some of the mails it is blank screen.

Required File: libgtk-x11-2.0.so.0

Thanks in advance


I am running LN 8.5.1 on Ubuntu 12.04 AMD 64.

---

### Post by Balix83 on 2012-06-11
> **oasit said:**
> Hello Asif

I had the same problem with a fresh installed 12.04.
To fix this problem you have to create and install the gdk-fix as described in steps 9+10 here [http://usablesoftware.wordpress.com/2011/10/10/install-lotus-notes-8-5-3-en-on-ubuntu-11-04-64bit/](http://usablesoftware.wordpress.com/2011/10/10/install-lotus-notes-8-5-3-en-on-ubuntu-11-04-64bit/)

I have attached the compiled libnotesgtkfix.so and notes-wrapper for your convenience.

Regards
Miguel



I used your compiled gtk-fix.
This is working perfectly :)
Thanks a lot Miguel !!

---

### Post by shammydog on 2012-09-03
Miguel,
  Your instructions in post #4 worked great!  Thanks for the post.

---

### Post by shammydog on 2012-09-03
SOLVED:  I spoke too soon.  Everything is rendering fine after applying Miguel's fix ... except for attachments.  I cannot open or view attachments.  I can save them and open them from the filesystem, but clicking open from within a Notes document does not work.  Any ideas while I continue to investigate?

After posting this problem, I found the solution in this writeup:
[http://usablesoftware.wordpress.com/2012/05/04/install-lotus-notes-8-5-3-on-ubuntu-12-04-64bit/](http://usablesoftware.wordpress.com/2012/05/04/install-lotus-notes-8-5-3-on-ubuntu-12-04-64bit/)
Much more detail than you need for getting Lotus Notes running on a 32-bit Ubuntu 12.04 (Mint 13 in my case but same diff).  Just follow Miguel's post #4 above, then you may need this code below to get attachments to work

```

sudo mv /opt/ibm/lotus/notes/openwith /opt/ibm/lotus/notes/openwith.bak
sudo ln -s /usr/bin/gnome-open /opt/ibm/lotus/notes/openwith

```

---

### Post by matsbekman on 2013-08-13
Just installed Notes 9 on Ubuntu 64 without problems.
Installing it completely with no errors in the operating system


[http://iwonthemove.wordpress.com/tag/ubuntu-64-bit-lotus-notes/](http://iwonthemove.wordpress.com/tag/ubuntu-64-bit-lotus-notes/)


For reading on how to


This is my companys blog on wordpress and it is written by me

---

