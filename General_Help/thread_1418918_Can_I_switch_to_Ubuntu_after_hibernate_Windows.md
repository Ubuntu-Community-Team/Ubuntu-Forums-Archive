---
title: "Can I switch to Ubuntu after hibernate Windows"
date: 2010-03-01
forum: General Help
---

### Post by necer_cheniki on 2010-03-01
Hello there , this is my first post here ,

I installed ubuntu with windows 7 , and I want to use the two systems , but if I want to switch from windows 7 to ubuntu , it should to restart my pc to enter to ubuntu. As you know windows 7 takes several time to start , therefore I want to hibernate windows 7 and when I restart it I found bootloader to choose witch system I want to enter , is that possible ?

what is the difference between installing ubuntu from the wubi.exe from windows , and the installation from ubuntu after restarting computer ?

THanks.

---

### Post by spiderbatdad on 2010-03-01
Windows should be shutdown cleanly before booting Ubuntu. I say that tongue in cheek because I cannot remember specific reasons, only many problems for other users in the past, such as system freezes.

Wubi installation is not as supported as well as other installation methods because fewer of us in the community use wubi...your posts sounds like you have wubi and regular Ubuntu installation.

---

### Post by necer_cheniki on 2010-03-01
> **spiderbatdad said:**
> Windows should be shutdown cleanly before booting Ubuntu. I say that tongue in cheek because I cannot remember specific reasons, only many problems for other users in the past, such as system freezes.

Wubi installation is not as supported as well as other installation methods because fewer of us in the community use wubi...your posts sounds like you have wubi and regular Ubuntu installation.

Thanks, but restarting the system is tedious. 
For wubi , I installed it from wubi.exe and I restarted my pc , where I found a list contains windows7 and utuntu , I clicked on ubuntu , so the installation process stared ,when It finished I entered to ubuntu.

---

### Post by spiderbatdad on 2010-03-01
Just found this in the wubi faq. [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

> 
Any gotcha?

Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


How about running full desktop version of ubuntu from a virtual machine like vmware on w7...though I must admit I have never before advised anything other than the opposite senario.

---

### Post by necer_cheniki on 2010-03-01
thank you , I think that the best solution is installing Ubuntu in separated partition on my disk.
thanks again for the help.

---

### Post by velle frak on 2010-03-01
About the hibernate: I've done it on several occasions, and never had problems. I run Xubuntu alongside Windows XP, both hibernated, and no problems so far.

---

### Post by necer_cheniki on 2010-03-01
> **velle frak said:**
> About the hibernate: I've done it on several occasions, and never had problems. I run Xubuntu alongside Windows XP, both hibernated, and no problems so far.

how did you do it ?  for me I am using win7 and when I put it in hibernation mode , I can't see choice menu , when I restart my pc.

---

### Post by velle frak on 2010-03-01
> **necer_cheniki said:**
> how did you do it ?  for me I am using win7 and when I put it in hibernation mode , I can't see choice menu , when I restart my pc.

I see. After hibernating Windows XP, GRUB bootloader still loads on my laptop. If I choose Windows XP in the bootloader, Windows XP wakes up. If I choose ubuntu, ubuntu wakes up.

In short, hibernating does not affect the bootloader I use. Maybe a Windows 7 issue? I don't have any experiences using Windows 7 (yet).

---

### Post by 10101011 on 2010-03-01
> **velle frak said:**
> In short, hibernating does not affect the bootloader I use. Maybe a Windows 7 issue? I don't have any experiences using Windows 7 (yet).

I believe that's because you are using a normal install of Ubuntu, while the OP is using wubi, which installs Ubuntu into a file in the windows filesystem which was made to look like a partition.

As far as I know, booting into Ubuntu while windows has hibernated works fine in a normal installation (meaning: not wubi), except that you can't mount the windows partition, so you can't access the files on that partition.

---

### Post by oldfred on 2010-03-01
You can mount the windows partition but if you change anything that the hibernation depends on will corrupt the windows partition. If you mount it read only you should be ok. That is why it has worked for some, but I have heard of others who "forgot" that they had hiberated and messed up their windows partition. It may just require chkdsk but may cause bigger problems. Use at your own risk.

On my portable Ubuntu boots completely slightly quicker than XP comes out of hibernation (about 1 Min.) Windows takes about 3 min to boot. I now have not booted windows on the portable since the first of the year.

---

### Post by penguinv on 2010-03-01
Here's a limit I have found in using the WUBI.

If you boot in one system than you cannot access the files on the same partition in the other system.

IF you boot (any system) from another drive | partition then you can only access the Windows files and not the Ubuntu files.

A related note about using Windows partitions and Ubuntu partitions and being able to read them. Of course, now Ubuntu can read and write from and to a NTFS drive/partition, but as usual Windows does not have the ability to read a Linux formatted partition. I've heard that there is a Windows program that will allow one to read ext2|3 files. Using that will allow access to your files from either system.

---

### Post by oldfred on 2010-03-01
I have seen instructions on how to boot from grub2 or mount the root.disk as a loop device. I have not saved the instructions as I do not use wubi.

---

### Post by velle frak on 2010-03-01
> **10101011 said:**
> I believe that's because you are using a normal install of Ubuntu, while the OP is using wubi, which installs Ubuntu into a file in the windows filesystem which was made to look like a partition.

As far as I know, booting into ubuntu while windows has hibernated works fine in a normal installation (meaning: not wubi), except that you can't mount the windows partition, so you can't access the files on that partition.

Correct. Haven't tried out the wubi thing, didn't even know there is such a thing (I'm fairly new to ubuntu ;) ).

Anyway, my ubuntu setup is on several partitions, not in files in the windows file system.

---

### Post by Mark Phelps on 2010-03-01
I have a multi-OS setup including Win7 and the default action on resume from Hibernation is to boot directly into Win7 -- there is no menu displayed, and as far as I can tell, no way to force one.

---

### Post by locombian on 2010-03-10
Hello

I accidentally did what was advised here  not to do; boot into ubuntu after hibernating windows, I can not boot windows and it freezes , ubuntu seems to be working fine. 

Is there anything i can do within ubuntu without losing any data i stored in windows,

---

### Post by Mark Phelps on 2010-03-11
Are you asking if you can repair Windows from inside Ubuntu -- after doing something you were advised NOT to do??

Are you surprised that the answer is NO?

I didn't catch which version of Windows you're running, but if it's Vista or Win7 you will need to boot from Vista/Win7 DVD and run Startup Repair several time to get boot capability back.

---

### Post by penguinv on 2010-03-14
> **locombian said:**
> Hello

I accidentally did what was advised here  not to do; boot into ubuntu after hibernating windows, I can not boot windows and it freezes , ubuntu seems to be working fine. 

Is there anything i can do within ubuntu without losing any data i stored in windows,

Hi, This will be simple because I'm not a linux guru at all but a beginner like yourself. As I understand it this is what you want:

1. you want to not lose your windows data.
Answer: boot from a livecd not your hard drive. Have a flash drive or a cd IN A DIFFERENT DRIVE (whatever is possible) and copy the data that is in the Windows area to that media. 
Voila, you are backed up.

That answers your question. The assumption you made is that you were going to do it from the Ubuntu boot off the grub partition. That was srong. You do it from an Ubuntu boot off some other drive be it another HD or the liveCD.

Now it is very interesting to note that when you dont boot from the wubi-Ubuntu - It is impossible to access your data in the wubi-Ubuntu part of the Windows disk. You have been warned, in case that comes up for you. Externally your data is completely hidden afaik.

In my lief, I just keep switching drives. I am getting a big one as a "final solution" and will partition it and not use wubi again. I have heard of a windows program that will allow you to see the data that is on an Ubuntu partition.

Best of luck to you and KIS! (keep it simple)


.. and while you are waiting,  :popcorn:

---

### Post by bredsj on 2010-03-14
I've read this thread but don't see the real solution to my problem, which is very similar to that described here.

My laptop has WinXP and Ubuntu 9.10 installed with Ubuntu as the default operating system. 

I was working in WinXP and closed the laptop, which I have done many times before. When I opened it again it was in the Ubuntu OS. No problem, I restart and then Windows is gone from GRUB!!!

Now to repair GRUB is a huge issue for me!

Any one that can help, it will be appreciated

---

### Post by oldfred on 2010-03-14
Boot problems are rarely the same issue unless there is a common bug. It is usually better to start a new thread so the title highlights your issue and those most familiar with that type if issue will respond.

Welcome to the forums.

If you have a new install of karmic have you tried sudo update-grub? If grub is working then it sounds more like a windows issue. If the update-grub does not find windows, describe any boot errors and post the results of this script in a new thread.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by bredsj on 2010-03-14
> **oldfred said:**
> Boot problems are rarely the same issue unless there is a common bug. It is usually better to start a new thread so the title highlights your issue and those most familiar with that type if issue will respond.

Welcome to the forums.

If you have a new install of karmic have you tried sudo update-grub? If grub is working then it sounds more like a windows issue. If the update-grub does not find windows, describe any boot errors and post the results of this script in a new thread.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

Thank you very much, that done the trick. I've learned a new Linux command as I do everyday. Slowly but surely I'll get there!

---

### Post by corruptmbr on 2010-03-29
This is the same problem I was also facing. Normally I never shutdown my windows 'coz of multiple 'u know what' issues. But now when I wanted to bootup my ubuntu, i'm not even seeing a grub menu at all. Instead it just restores the win hibernate data. 

The issue seems to be fairly simple. Apparently I used the Wubi to install my Ubuntu. It looks like the MBR is of windows loader and which is the chainloads the grub. So, once you hibernate and tries to wake up to Ubuntu, the win loader doesn't like to load the Grub. Solution also should be simple as to rewrite the MBR with GRUB loader and from grub you might need to point to windows loader (NTLDR) and wubi loader. 

I did some googling and now I know with a 'Super Grub disk' I could do this. But I have not tried it yet. The reason is simple I am using my official laptop and a whole lot of data. I don't want to get anything messed up on this. 

If anybody has already tried something like tthis.. please post it here.. So that someof us can proceed with that. 

thanks,
Joe

---

### Post by oldfred on 2010-03-29
While I have seen where it may be possible to use grub to directly boot wubi, it is designed to use teh windows boot loader and then chainboot grub into wubi.

I do not know if this is the same problem or not but it would be worthwhile to update anyway.
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

