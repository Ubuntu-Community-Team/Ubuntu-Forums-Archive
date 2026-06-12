---
title: "broken screen on boot?"
date: 2012-02-03
forum: General Help
---

### Post by nehlewolf on 2012-02-03
Alright so. I have an Asus g74sx runing 64amd Ubuntu 11.10 dual booting windows 7 64b. The Ubuntu installation was installed inside windows.

For some reason after installing it a few months ago I get this weird overlay of what looks like broken font across the login screen. Its no biggie because i can press any key and the login screen reloads and the system works flawlessly. The issue however: 

[http://postimage.org/image/q50dlefqv/](http://postimage.org/image/q50dlefqv/)

Like I don't even know how to describe this.

Upon boot this has started appearing. Same in safe mode except sometimes I'm able to get to the root shell. When I press enter after this broken screen appears, I'm welcomed by a black screen and a blinking cursor.  Sometimes if I force windows to end (it has a hanging shutdown) then I will see that the disk is being fixed because windows tainted it upon retrying to boot Ubuntu,  but the bottom of the line is obviously severed as though there is a black layer in front of it.

When I shut down - pressing the power button, not holding it . An onslaught of text shows up and appears to be a dmesg dump. I've captured that as well. 
 Or at least tried to.

[http://postimage.org/image/j87kuzy9t/](http://postimage.org/image/j87kuzy9t/)

Sorry for such bad quality but its not exactly the position to take a screenshot and all I have is my tablet while my roommate is asleep.

I've tried disabling the splash screen but no avail. The system has worked fine for months under this installation  until I ran an aptitude update.

And advice and suggestions would be greatly appreciated. I'll try to buy you doughnuts when I get stateside!

---

### Post by grahammechanical on 2012-02-03
I am not dual booting with Windows or using Ubuntu inside Windows and neither do I live stateside. Send doughnuts to ....

In my opinion I would not worry about the messages that you get when you hold down the case power button to shut down. That seems normal to me.

When we shut down using the menu messages like that are hidden by the 11.10 splash screen. But switching off the power to the machine sends a shut down now signal to Ubuntu and it does not get a chance to display the usual splash screen.

What does concern me switching off the machine in that way is that you are force-closing two operating systems at the same time.

I am not an expert in this but from those messages it seems that the OS is getting the shut down signal while it is in the process of loading some things. Either that or it is starting and then stopping what it started before stopping the rest of the system.

I think that you might be creating problems rather than fixing them.

Please start again with the broken font effect. Describe what happens from machine switch on until Ubuntu loads. Please make clearer the point at which that broken font effect appears. Is it the boot screen from which you choose either Windows or Ubuntu? Is it the Ubuntu log in screen?

If it appears before you boot an OS then the issue may be with the video adapter. Make sure your machine is not over heating. If it happens at the Ubuntu log in screen then you could try re-installing the video drivers.

Regards.

---

### Post by Bucky Ball on 2012-02-03
Is this running as a virtual machine inside Windows or have you installed Wubi? Wubi designed to try out Ubuntu for awhile, not for permanent use. A hard drive install on a separate partition will yield a faster and better experience.

A Wubi install is not a dual-boot. Windows and Ubuntu (or any two operating systems) on separate partitions is a dual-boot. ;)

---

### Post by bcbc on 2012-02-04
> **grahammechanical said:**
> 
... you could try re-installing the video drivers.

Regards.

+1. 

The screen shot looks like a graphics card issue. You can probably get around it with [nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132"). That should keep you going until you get the graphics driver (re)installed. 

If you need to shutdown you should use [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot") to avoid file system corruption.

---

