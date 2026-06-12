---
title: "Suspend Problem in Ubuntu 11.04"
date: 2011-04-27
forum: General Help
---

### Post by bhatbhai on 2011-04-27
Hi all,

I could not find a solution to this problem for 11.04, despite the numerous solutions for previous versions of Ubuntu. Anyway, I'm running Ubuntu as a 100 GB (out of 300) partition on my Sony Vaio VGN-NW265F/B, with the other 200 GB being a Windows 7 (64-bit) partition. The laptop has a 2.1 GHz Intel Dual Core processor and 4 GB of RAM. This is my first time trying Ubuntu, but this problem with suspend is preventing me from making a full transition.

Basically, when I hit Suspend (from the menu or the dedicated keyboard button), the screen goes black, then a couple lines of text show. When I turn the computer back on, it starts up as if the computer were shut down. 

Hibernate works fine, just so you know. Suspend seems to be the only problem.

Does anybody have a fix for this? And if I need to supply more information, let me know, I'm new at this.

Thanks!

---

### Post by vashfish on 2011-04-28
I'm also having a problem with suspend on my Sony Vaio. Mine's a VPCF126FM (i7 quad core with 6g ram). 

My symptoms are a bit different though. The screen goes black and everything looks like it's getting ready to sleep but it seems to get stuck in an infinite loop. The CPU fan starts spinning up to full speed and there's no way to wake it back up without holding down the power button to turn it off.

---

### Post by leviathan8 on 2011-04-28
Hello. Please open a terminal and type in:

```
sudo apt-get install uswsusp
```

then input your password and wait to finish installation. Once you're done, reboot the computer and try suspending it.

Good luck.

---

### Post by vashfish on 2011-04-28
Actually, it turns out there was a bios update available for me. After installing it, suspend seems to be working properly.

---

### Post by bhatbhai on 2011-04-28
Leviathan, I already have uswsusp installed, and the problem still persists.

Vash, was the BIOS update through Update Manager, or did you do something manually?

---

### Post by Gazz1e on 2011-04-29
I've got issues with my Acer Aspire coming out of hibernate. Looking at the forums I'm not the only one. I've gone back to 10.04.

---

### Post by leviathan8 on 2011-04-29
> **bhatbhai said:**
> Leviathan, I already have uswsusp installed, and the problem still persists.

Vash, was the BIOS update through Update Manager, or did you do something manually?

So you cannot suspend with the following command?

```
sudo s2ram -f
```

---

### Post by bhatbhai on 2011-04-29
> **leviathan8 said:**
> So you cannot suspend with the following command?

```
sudo s2ram -f
```

Correct. Even when I use that command, the laptop appears to go to sleep, but then starts up as if it were shut down.

---

### Post by saggitheman on 2011-04-29
got acer aspire 5732Z and same problem here...

---

### Post by Bnelsonmiller on 2011-04-29
My Acer Aspire D255 has the same problem. I would like to use Hibernate to save battery, but when it comes out of it, there is just a black screen with a cursor and some random lines at the top of the screen.

---

### Post by leviathan8 on 2011-04-29
> **bhatbhai said:**
> Correct. Even when I use that command, the laptop appears to go to sleep, but then starts up as if it were shut down.

I got one more option that could help.
Please enter in a tty (CTRL+ALT+F1) and log in with your current user. Once done, type "sudo service gdm stop" and input your password. Now you will no longer have a GUI, so there might be a hope if the computer has problems with video drivers. So, from the command line interface, type "sudo s2ram -f". Good luck.

---

### Post by prezument on 2011-04-29
I have the same problem, seems like a problem with the kernel.
I booted with 2.6.35-28 and it works fine, 2.6.38-8 hangs.

---

### Post by bhatbhai on 2011-04-29
Thanks for all the help so far, guys.

> **leviathan8 said:**
> I got one more option that could help.
Please enter in a tty (CTRL+ALT+F1) and log in with your current user. Once done, type "sudo service gdm stop" and input your password. Now you will no longer have a GUI, so there might be a hope if the computer has problems with video drivers. So, from the command line interface, type "sudo s2ram -f". Good luck.

I tried this out and it still resumes as if it were shut down.

How do I go about downgrading to a different kernel? And will it affect the Ubuntu 11.04 that I have installed?

---

### Post by leviathan8 on 2011-04-30
> **bhatbhai said:**
> Thanks for all the help so far, guys.



I tried this out and it still resumes as if it were shut down.

How do I go about downgrading to a different kernel? And will it affect the Ubuntu 11.04 that I have installed?

Hello. Downgrading the kernel will not affect your current version. I do not know what kernels do the Natty's repo's have, but you can research it yourself by opening Synaptic Package Manager.
Once you launched it, type in the search box:

```
2.6.35
```

If you found it, proceed by installing the following packages:

```
linux-headers-2.6.35-xx
linux-headers-2.6.35-xx-generic-yyy
linux-image-2.6.35-xx-generic-yyy
```

xx represents the patch version. yyy represents the pae (physical address extension), if the machine has 4 GiB RAM memory installed and a 32 bit CPU architecture chosen for your version, then you must install this. If you do not have 4 GiB RAM or you own a 64 bit version, exclude the "-pae".

To make things easier for you to understand, I have took a picture of the packages needed to be installed from the command line.

[IMG]http://i.imgur.com/JAyTl.png[/IMG]

Note that the patch version may differ (in my case it is -22) and also remember that the linux-headers **MUST** match with the linux image patch version.

Good luck.

---

### Post by bhatbhai on 2011-04-30
Thanks for the information!

Unfortunately, my Synaptic Package Manager is not finding any of these old kernels. Is there any way to update the list so that it shows old kernels?

---

### Post by leviathan8 on 2011-04-30
Hello. 

As mentioned earlier, I have no idea of what kernels are available in 11.04. I am going to test out the new version in a virtual machine in a couple days. I will come back with info once I'm done, but in the meantime you could ask here on forums.

Have a nice day.

---

### Post by lostgate68 on 2011-04-30
> **Bnelsonmiller said:**
> My Acer Aspire D255 has the same problem. I would like to use Hibernate to save battery, but when it comes out of it, there is just a black screen with a cursor and some random lines at the top of the screen.

I encountered the similar problem too, but with a pixelated drawing on the screen.  Without seeing the login screen, I entered my username/passwd and that worked.  This is on a Lenovo R61.

---

### Post by bhatbhai on 2011-05-02
Anybody else have a solution to this?

---

### Post by gonzalez.rod.a on 2011-05-03
seems like is a very nasty bug. :(:(:(

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/772834]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/772834")

---

### Post by prezument on 2011-05-03
2.6.39-0 still doesn't fix this.
I'll just keep using an older kernel and wait for a fix.

---

### Post by leviathan8 on 2011-05-03
> **leviathan8 said:**
> Hello. 

As mentioned earlier, I have no idea of what kernels are available in 11.04. I am going to test out the new version in a virtual machine in a couple days. I will come back with info once I'm done, but in the meantime you could ask here on forums.

Have a nice day.

Hello. I have installed 11.04 and it seems that they haven't got any other kernels but the 2.6.38. I am afraid that you are stuck with this problem for a while.

---

### Post by prezument on 2011-05-03
> **leviathan8 said:**
> Hello. I have installed 11.04 and it seems that they haven't got any other kernels but the 2.6.38. I am afraid that you are stuck with this problem for a while.

If you upgraded you should have the older one installed (unless you removed it).
In the Grub version of 11.04 booting with another kernel is done under 'older linux versions' in the boot menu (or 'other'? don't remember correctly).

If you don't have older kernels installed you can install them manually.
[http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/)

---

### Post by bhatbhai on 2011-05-03
> **prezument said:**
> If you upgraded you should have the older one installed (unless you removed it).
In the Grub version of 11.04 booting with another kernel is done under 'older linux versions' in the boot menu (or 'other'? don't remember correctly).

If you don't have older kernels installed you can install them manually.
[http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/)

Thanks for all the responses, again. 

I just installed 2.6.35 with the help of the link posted, and I seem to be getting SOME progress. When I hit a key while it is suspended, a black screen comes up and says something about resuming. But then it fails, it it goes back to the standard boot-up procedure.

Oh well. I guess I'm going to go back to 2.6.39 and just hope for some updates unless somebody else has a fix.

---

### Post by Jordanbadangayon on 2011-05-05
me too.. i hope an update will fix this. Some of my issues with my Vaio were actually fixed by an update..

---

### Post by Ghouli on 2011-05-06
Same problem here, but on desktop PC with Asus P5N-E Sli motherboard, clean install without dualboot.

---

### Post by Willynux on 2011-05-07
I have this problem too (suspend = shut down) on a Vaio VGN-FW270AE Ubuntu 11.04.
Is it really a kernel problem? This makes me think again that updates should have bug fixes rather than new features.

---

### Post by mijodo on 2011-05-10
[cross posting from another similar thread...]

Possible solution...

I have a similar issue: my laptop goes into suspend mode correctly but  when I try to wake it, it does a full reboot instead of resuming.

After hunting around on the web and trying several solutions, I found one that works for my PC.

The following solution was intended for 10.10, but it also works for me in 11.04:

[http://www.michali.org/ubuntu/sony-v...on-ubuntu-1010]("http://www.michali.org/ubuntu/sony-vaio-fw490j/73-suspendresume-on-ubuntu-1010")

Note: you must do a full reboot after running update-grub before suspend will start working.

Note: while this fixes suspend on my PC, it does *not* fix hibernate.

Note: I have a Sony Viao VGN-SR21M, running 11.04, 64 bit, alternate installer.
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10795319")                                                                                    [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10795319")

---

### Post by fragment137 on 2011-05-10
I have a similar problem on an ASUS G51Jx-A1 running Linux Mint 10...

I went buzzing around on the Mint forums, but can't hunt anything solutions down...

I can't suspend/hibernate at all... Suspend causes the screen to shut off and that's it, the rest of the system seems to be running completely... Hibernate will cause the same conditions, but when I do a hard reboot in order to get the computer running again, Mint starts in a "resumed" state...


Very confusing and annoying, cause I'm on and off with my laptop all day, and having a suspend/hibernate function is key for me.

I still have Windows installed for certain compatibility issues but I'd prefer to minimalise my usage of it.

current kernel that i have installed on Mint 10: 2.6.35-22-generic

---

### Post by whitepine on 2011-05-10
I have this problem in Ubuntu 11.04.  The computer seems to suspend properly, but hangs when coming out of suspend.  I tried uninstalling the nvidia driver 270.41.06 and using the nouveau driver instead.  It came out of suspend just fine, so I'm waiting for a new nvidia driver.  Perhaps, an older driver would work?

---

### Post by jasiok on 2011-05-11
> **leviathan8 said:**
> Hello. Please open a terminal and type in:

```
sudo apt-get install uswsusp
```then input your password and wait to finish installation. Once you're done, reboot the computer and try suspending it.

Good luck.

Worked for me on Samsung N230 - thanks for the post - now wakes up as quick as it did on windows which came  preloaded on it

---

### Post by Jordanbadangayon on 2011-05-11
> **mijodo said:**
> [cross posting from another similar thread...]

Possible solution...

I have a similar issue: my laptop goes into suspend mode correctly but  when I try to wake it, it does a full reboot instead of resuming.

After hunting around on the web and trying several solutions, I found one that works for my PC.

The following solution was intended for 10.10, but it also works for me in 11.04:

[http://www.michali.org/ubuntu/sony-v...on-ubuntu-1010]("http://www.michali.org/ubuntu/sony-vaio-fw490j/73-suspendresume-on-ubuntu-1010")

Note: you must do a full reboot after running update-grub before suspend will start working.

Note: while this fixes suspend on my PC, it does *not* fix hibernate.

Note: I have a Sony Viao VGN-SR21M, running 11.04, 64 bit, alternate installer.
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10795319")                                                                                    [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10795319")
This worked on my Vaio VGN-NW20EF.  Thanks man. :D

---

### Post by bhatbhai on 2011-05-16
> **mijodo said:**
> [cross posting from another similar thread...]

Possible solution...

I have a similar issue: my laptop goes into suspend mode correctly but  when I try to wake it, it does a full reboot instead of resuming.

After hunting around on the web and trying several solutions, I found one that works for my PC.

The following solution was intended for 10.10, but it also works for me in 11.04:

[http://www.michali.org/ubuntu/sony-v...on-ubuntu-1010]("http://www.michali.org/ubuntu/sony-vaio-fw490j/73-suspendresume-on-ubuntu-1010")

Note: you must do a full reboot after running update-grub before suspend will start working.

Note: while this fixes suspend on my PC, it does *not* fix hibernate.

Note: I have a Sony Viao VGN-SR21M, running 11.04, 64 bit, alternate installer.
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10795319")                                                                                    [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10795319")

So, I tried this out, and it still didn't work at first. Then, I reinstalled 11.04 and tried this solution first without tinkering with other solutions, and it works just fine now. 

Thanks a million!

---

### Post by Willynux on 2011-05-28
There's a nice, step by step solution on the thread:
[http://ubuntuforums.org/showthread.php?t=1750304&page=2](http://ubuntuforums.org/showthread.php?t=1750304&page=2)

---

### Post by OpenSage on 2011-09-21
> **vashfish said:**
> I'm also having a problem with suspend on my Sony Vaio. Mine's a VPCF126FM (i7 quad core with 6g ram). 

My symptoms are a bit different though. The screen goes black and everything looks like it's getting ready to sleep but it seems to get stuck in an infinite loop. The CPU fan starts spinning up to full speed and there's no way to wake it back up without holding down the power button to turn it off.





I know this is a really late reply, but I think I have this issue figured out. I have had the same problem running both Ubuntu 10.10 64 bit and Ultimate Edition 9/on Ubuntu 10.10 64 bit. I came across this fix by accident. Before suspending the machine, go to a different console by pressing (CTRL+ALT+F2) all at the same time. You should be in a new console. Log into that console then press (CTRL+ALT+F7) to take you back to your Graphical User Interface and then Suspend you machine. This works for me every time. Hope this helps some people.\\:D/

---

