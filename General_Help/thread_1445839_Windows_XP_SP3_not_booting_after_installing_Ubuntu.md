---
title: "Windows XP SP3 not booting after installing Ubuntu 10.04"
date: 2010-04-03
forum: General Help
---

### Post by T-z3P on 2010-04-03
Hi all , I need a little help . I'm trying to set up my laptop to dual-boot Windows XP SP3 and Ubuntu 10.04 , but no success :
> Windows could not start because the following file is missing or corrupt :
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file.

---

### Post by prodigy_ on 2010-04-03
Read [this](http://support.microsoft.com/kb/314477) and follow the instructions.

---

### Post by T-z3P on 2010-04-03
Thank you . What I did :
1. Edited boot.ini from 
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```
to
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```
2. Copy-Pasted "ntoskrnl.exe" and "hal.dll" from my Desktop PC to my Laptop .

---

### Post by texstar420 on 2010-05-20
Hello I am new here and new to Ubuntu. I was wondering if I should  download the files you said you copied from your other computer because  only have a vista laptop to copy the files from. Or can I use the vista  lapy to copy the hal.dll file and ntoskrnl.exe.

{Edited}
I am referring to step:
2. Copy-Pasted "ntoskrnl.exe" and "hal.dll" from my Desktop PC to my Laptop .
of T-z3p's process. Where did he get those files from? I know he said he got them from his desktop and put them on his laptop. But I can't do this so can I download these files?


------------------------------------------------------------------
> 
**Re: Windows XP SP3 not booting after installing Ubuntu 10.04**             
                                                                Thank you .  What I did :
1. Edited boot.ini from 
     Code:
     [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
to
     Code:
     [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
2. Copy-Pasted "ntoskrnl.exe" and "hal.dll" from my Desktop PC to  my Laptop .
                                                                                                                                                  [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=9069289")

---

### Post by oldfred on 2010-05-20
texstar420 welcome to the forums.

Since you have Vista and this thread is about XP, I do not think anything here applies to you. It would be best to start your own thread with more explanation of what the problem is or search the forum for those who have Vista.

In your new thread post this so we can have a better idea of your configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by texstar420 on 2010-05-20
Sorry to confuse you I do have xp on my desktop but I was saying I only have a laptop with vista on it and could I copy the hal.dll file from there or should I download it from somewhere. Where would I download it.

Thanks!

---

### Post by oldfred on 2010-05-21
The problem usually is not a missing hal.

Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
Error message: "Windows could not start because of a computer disk hardware configuration problem"
[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)
Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

---

### Post by texstar420 on 2010-05-21
Thanks oldfred those seem like some helpful sites. But here's the latest issue.

Ubuntu (which I now love) works great on my computer (which is no surprise) after I did the dual boot the other night. 

To give you a little background on my pc... I have a desktop with 2 hard drives, one is my media and backup drive that is 1 tb harddrive not partitioned the other is my main drive which is a 1tb harddrive partitioned in this order (C : 500gb for windows xp, (I : 470gb for backup and media. K: 20gb for Ubuntu.

For some reason my C: drive is now listed as E: in the recovery console and my I: drive is listed as C: . I don't know if this is what is causing windows not to load. Maybe I have to find a way to make the E: drive C: again.  But what could have happened to change the drive letters?
When I was installing ubuntu I don't remember deleting any partitions and I made the partition in ubuntu. I didn't delete the SDA 1 which I saw somebody ask in another forum, but maybe I did and just didn't realize it. Cause when grub loads windows xp has (sda2) at the end of it. Oh I don't know what sda stands for anyway.

What I have done so far:
-I have tried to use the windows xp disk to load the recovery console and fixboot which didn't work.
-Tried to but new copy of hal.dll from disk. still get message after reboot that it is missing or corrupt. I know my disk copy is good also.
-Tried to the bootcfg /rebuild command then deleted old boot.ini and copy a new boot.ini from the windows xp disk...didn't work. After I reboot and choose windows from the grub screen says the hal.dll message.

---note boot.ini is show up on my 470gb drive

-tried editing in Ubuntu my boot.ini file that is on my 470gb disk and placing it on the 500gb C: drive. ....didn't work

I am almost ready to wipe my old xp partition and reinstall windows on it because I feel like I have tried everything to get it to work again. I just don't get it. Any help would be great.
I would like to have windows for gaming, school because there are some programs I have to use like microsoft visual studio 2010 for my vb.net class, and also because I don't know what I am doing in linux yet. So I have to have windows for now.
I hope me being very descriptive will be enough for someone to help me find a solution. 

Things I will try tonight include check boot order in bios, oldfreds links.

Thanks in advance.

---

### Post by oldfred on 2010-05-21
I am not sure what you  have done now. Without the boot info script we are not able to see what is where on your system.

It still would be best to start your own thread. Only those looking for answers look at solved threads, so you will not get any extra help here.

With two drives I always like to separate the windows on one drive and Ubuntu on the other since windows does not play well with anyone else.  Many like to make every drive bootable as a just in case one drive dies, you can still boot the other.

---

### Post by texstar420 on 2010-05-21
thanks oldfred I think I will just back up and reinstall linux on a separate drive like us say and windows on another. I am tired of messing with it all. I have learned my lesson well. thanks everyone for your help.


[COLOR=Red][solved][/COLOR]

---

### Post by T-z3P on 2010-07-16
Hi again . I have another problem I think . I tryed to install ubuntu on another laptop and I get the same error :
> Windows could not start because the following file is missing or corrupt  :
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file.I tryed to follow my own method (that with boot.ini , ntoskrnl.exe and hal.dll) , but is not working .

PS : I don't know why, but boot.ini is not on "C:\" drive . It's on the third partition...

PS2 : Here is a screenshot of my partitions .

[[IMG]http://i32.tinypic.com/j6haah_th.png[/IMG]]("http://i32.tinypic.com/j6haah.png")

---

### Post by drs305 on 2010-07-16
I don't know enough about Windows to help with a solution, but you will probably get more responses if you remove "SOLVED" from this thread.

You can do that the same way you marked it solved, via the "Thread Tools" link at the top right of the original post. Best of luck.

---

### Post by T-z3P on 2010-07-16
Thank you for response . What I did (I know is kinda n00bish , but it worked) :
- I pop-in my Windows CD and waited until the box with partitions showed up
- There I saw that the Windows partition is the partition with number **4** , so I edited boot.ini from 
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(**2**)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(**2**)\WINDOWS="Microsoft Windows XP  Professional" /noexecute=optin /fastdetect 
```to
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(**4**)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(**4**)\WINDOWS="Microsoft Windows XP  Professional" /noexecute=optin /fastdetect 
```

---

