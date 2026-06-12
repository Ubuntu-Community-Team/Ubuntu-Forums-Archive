---
title: "Problem with ubuntu 10.4 ..."
date: 2010-06-13
forum: General Help
---

### Post by fairbird on 2010-06-13
Hi every body ...
 
I was download last verison of ubuntu 10.04 from this link
 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
and i was got this file image ....
 
 
[IMG]http://img101.imageshack.us/img101/7269/13062010054532.jpg[/IMG]
then i was burned on cd ... but does't work install ... i don't know what is problem ?
 
here picture for cd content after burned image ..
 
[IMG]http://img411.imageshack.us/img411/636/13062010054509.jpg[/IMG]
 
any one can help me ?
 
 
Regards

---

### Post by howefield on 2010-06-13
What doesn't work, when you put the CD into the drive, does it boot at all ?

---

### Post by CharlesA on 2010-06-13
Bad burn maybe, check the MD5SUM of the ISO before burning.

---

### Post by spiky001 on 2010-06-13
Have you set the bios to boot from cd

---

### Post by fairbird on 2010-06-13
Thank you to all ....
 
> 
What doesn't work, when you put the CD into the drive, does it boot at all ?

 
I want to install ubuntu from windows same as last one ubuntu 9.10 .
 
> Bad burn maybe, check the MD5SUM of the ISO before burning. 
 
i was burned by _InfraRecorder  _
and how to check iso ??
 
> Have you set the bios to boot from cd 
 
bios boot from cd and i want to install from inside windows .
 
Regards

---

### Post by techunit on 2010-06-13
Ok what you go to do is tell me what version of windows your using cause it looks like vista and XP mixed to together.... sorry but it doesn't look like windows. You should be using Imgburn to burn Iso Images To CDs because it is very relyable. I had trouble installing it inside windows before I tryed imggburn.

---

### Post by bcbc on 2010-06-13
You don't need to burn it to cd to install with wubi (although I recommend creating an install cd anyway as you'll probably need it to troubleshoot at some point).

Just put wubi.exe and the .iso you downloaded in the same directory and run wubi.exe. By the way, if wubi.exe doesn't like the .iso it will download another.

---

### Post by fairbird on 2010-06-13
> Ok what you go to do is tell me what version of windows your using cause it looks like vista and XP mixed to together.... sorry but it doesn't look like windows. You should be using Imgburn to burn Iso Images To CDs because it is very relyable. I had trouble installing it inside windows before I tryed imggburn. 
 
I was also burned iso file by _ultraiso _and same problem i got . and i use only xp windows .
 
> You don't need to burn it to cd to install with wubi (although I recommend creating an install cd anyway as you'll probably need it to troubleshoot at some point).
 
Just put wubi.exe and the .iso you downloaded in the same directory and run wubi.exe. By the way, if wubi.exe doesn't like the .iso it will download another.
 
from where can i get wubi.exe and please can you give my more details about how to downloaded in the same directory and run wubi.exe ?
 
Thank you all

---

### Post by howefield on 2010-06-13
> **fairbird said:**
> from where can i get wubi.exe and please can you give more details about how to downloaded in the same directory and run wubi.exe ?

It is on your burned Ubuntu CD, see the image in your first post.

You only want wubi if you want to do a wubi install, which means installing Ubuntu as a file on your windows file system as opposed to a full installation on it's own partition. The main benefit being that removal can be done via control panel.

There are several disadvantages to this method including reliability and speed. Not recommended as a way to run Ubuntu long term.

---

### Post by fairbird on 2010-06-13
> It is on your burned Ubuntu CD, see the image in your first post.

You only want wubi if you want to do a wubi install, which means installing Ubuntu as a file on your windows file system as opposed to a full installation on it's own partition. The main benefit being that removal can be done via control panel.

There are several disadvantages to this method including reliability and speed. Not recommended as a way to run Ubuntu long term.
 
I was downloded wubi.exe from here
 
[http://mirrors.gigenet.com/ubuntu/10.04/](http://mirrors.gigenet.com/ubuntu/10.04/)
 
and i but it in the iso file but nothing done a problem still .

---

### Post by medic2000 on 2010-06-13
Yes wubi is a bad choice. Boot your computer from cd with the Ubuntu Cd and choose to make a partition near Windows(not deleting windows) but before make a copy of important files in case of something happens. Then enjoy your 'real ubuntu'. When you missed the Windows reboot and choose Windows at the start of the computer. 

Welcome to the dual-boot technology, everyone happy!

---

### Post by iNsOmNiOuS on 2010-06-13
There is no need to download wubi.exe !

In windows, insert the burnt CD into your CD drive. Wait a bit for it to load, then go to My Computer, right click on D : (Or Whatever drive it is for your CD drive) and click explore. 

Now search in the root folder of the CD for wubi.exe. It should be there. To start the installation, just double click it :)

---

### Post by bcbc on 2010-06-13
Go to [http://wubi-installer.org/](http://wubi-installer.org/)

Click on Download now. Save it. Run it.

If you want it to run quickly, take the ubuntu .iso (not individual files, but the 750MB .iso file, and place it in the same folder as wubi.exe). If you downloaded the correct .iso for your machine, then it will use it and run faster. But this is not necessary. 

I also recommend reading this before you use wubi:  [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Edit: also, as insomnious said, if have a correctly burned install cd (which it sounds like you don't from your earlier post, but if you  do) then just pop it in the cd tray and you'll get a window popup. I think the first button is to install wubi.

---

### Post by fairbird on 2010-06-13
> 
Yes wubi is a bad choice. Boot your computer from cd with the Ubuntu Cd and choose to make a partition near Windows(not deleting windows) but before make a copy of important files in case of something happens. Then enjoy your 'real ubuntu'. When you missed the Windows reboot and choose Windows at the start of the computer. 
 
Welcome to the dual-boot technology, everyone happy!

 
Already when i want boot from cd doesn't booted and i'm sure a bios is boot frome cd :confused:
 
> There is no need to download wubi.exe !
 
In windows, insert the burnt CD into your CD drive. Wait a bit for it to load, then go to My Computer, right click on D : (Or Whatever drive it is for your CD drive) and click explore. 
 
Now search in the root folder of the CD for wubi.exe. It should be there. To start the installation, just double click it 
 
I was tried before double click .... but i got black screen ( dos screen ) few second and disappear .
 
> Go to [[COLOR=#000000]http://wubi-installer.org/[/COLOR]]("http://wubi-installer.org/")
 
Click on Download now. Save it. Run it.
 
If you want it to run quickly, take the ubuntu .iso (not individual files, but the 750MB .iso file, and place it in the same folder as wubi.exe). If you downloaded the correct .iso for your machine, then it will use it and run faster. But this is not necessary. 
 
I also recommend reading this before you use wubi: [[COLOR=#000000]https://wiki.ubuntu.com/WubiGuide[/COLOR]]("https://wiki.ubuntu.com/WubiGuide")
 
Edit: also, as insomnious said, if have a correctly burned install cd (which it sounds like you don't from your earlier post, but if you do) then just pop it in the cd tray and you'll get a window popup. I think the first button is to install wubi. 
 
i do what you said but same problem .
 
I think iso file did not downloaded correctly ... how i can check and prepare it ?
 
i was test iso file by Virtual Machines program and i got this error ... see pic.
 
[IMG]http://img72.imageshack.us/img72/6358/14062010043309.jpg[/IMG]

---

### Post by bcbc on 2010-06-13
Edit: sorry misunderstood. I thought you said you were trying to install wubi under a virtual machine.

I'll go and test that link again.

---

### Post by bcbc on 2010-06-13
> **fairbird said:**
> i do what you said but same problem .

wubi.exe - from that link I provided - works fine for me.

---

### Post by fairbird on 2010-06-14
@bcbc
 
> wubi.exe - from that link I provided - works fine for me. 
 
Thank you very very .... you are right ... i was changed again and fixed .... [COLOR=#000][SIZE=5]It works perfectly[/SIZE][/COLOR] .
 
 
and thank you for every one help my .
 
Regards

---

