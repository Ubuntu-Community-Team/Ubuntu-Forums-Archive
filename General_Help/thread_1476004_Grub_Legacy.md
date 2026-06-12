---
title: "Grub Legacy"
date: 2010-05-07
forum: General Help
---

### Post by sp3kter on 2010-05-07
Hello, 

I'm new to Ubuntu and have run into what seems to be a rather serious problem. I had to re-install my Windows..this obviously made my 'Choose Operating System Option Screen' disappear(Grub-Legacy I think?) 

Being very new to Ubuntu,I couldn't do much more than try and restore my Grub by using 'Auto Super Grub Disk' method. 
Tried versions 1.9 and 1.9 alternate to no avail. [Stopped responding midway into the installations.] 

Relevant Details 

1.Ubuntu ver is 9.04 (64 bit) 

2.Win7 working and it's on a separate partition.

3.Can't tell by name/not sure how to determine which drive my Ubuntu install is on (unless I can see all the drives listed.) 

I can't remember much more than the Ubuntu installation requiring 2 partitions,one for the OS itself and another 4 gb partition to act as virtual memory(if not mistaken.) 
I have another 5, 200 gb partitions all dedicated to Windows. 

(The only way I can tell my Ubuntu Partitions apart from the Win7 ones is from the space they take up.) 
I have important work related files on all the remaining disks so trying to go about this cautiously. 

I've gone through a few articles regarding this online,but could make no head or tail of them. 
Being a total Ubuntu newbie,I'd be very grateful if someone could please provide a detailed solution. 

Hoping to resolve this at the earliest. 

Thanks!

---

### Post by sp3kter on 2010-05-07
[Edited]

---

### Post by dino99 on 2010-05-07
[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by sp3kter on 2010-05-07
Hey,thanks for the link.

"if you still have other distro installed (windows, ...), after reboot with ubuntu, open a terminal (alt+f2) and run:

sudo grub-mkconfig && update-grub

on next reboot you will see grub menu to choose on which distro you want to boot. "


So that's all I have to do?

Do I just copy paste this at one go into the terminal? 

'sudo grub-mkconfig && update-grub'

or sudo grub-mkconfig

and then sudo update-grub  ?


Sorry if by any chance that sounded ridiculous,but still haven't quite got a hang of Ubuntu yet.

---

### Post by WorMzy on 2010-05-07
In bash (the standard terminal) the && operator just makes the commands run subsequently. As long as the first command doesn't fail, the second command will run immediately after it.

It doesn't matter which way you do the commands. Either 'sudo grub-mkconfig && sudo update-grub' or 'sudo grub-mkconfig' then 'sudo update-grub' will have the same effect in the end. :)

---

### Post by sp3kter on 2010-05-07
Hey,

Thanks for your reply Wormzy.


This is the outcome of the command :


ubuntu@ubuntu:~$ sudo grub-mkconfig && sudo update-grub
sudo: grub-mkconfig: command not found

What must be done next? :-s

[Running this after booting into Ubuntu using the installer CD.(Live Session?)]

---

### Post by WorMzy on 2010-05-07
This link might help:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by sp3kter on 2010-05-07
Thanks once again.

I've gone through that page atleast a hundred times over the last 2 days. :p

Did try a few of the automatic methods.None of them seemed to work(probably some compatibility issues with Win7.)

The rest of the methods which include commands,go way above my head since it involves specifying partition details about my Linux install.
Absolutely unsure about what needs to be done.


"**For Grub Legacy**

 1) Boot off the 9.04 LiveCD 
2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub &#8220;prompt&#8221;, and the next 3 commands will be executed there. _**Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where grub is installed by default. If yours differs, adjust accordingly. **_

sudo grub

> root (hd0,0)

> setup (hd0)

> exitGrub has now been reinstalled to your MBR. "



This bit seems to be the solution to my problem.Could you please guide me so that I may find out for certain if/what needs to be entered in place of :

root (hd0,0)

> setup (hd0) 

(I mean in respect to the command itself and specifying the partitions.)

How should I go about that?

Thanks again.

---

### Post by WorMzy on 2010-05-07
I believe you can run (inside grub, using the ">" prompt) 'find /boot/grub/stage1', which should tell you where your grub is installed. The first number is the disk number, and the second number is the partition number, both start at 0. So (hd0,2) is disk one, partition three.

---

### Post by sp3kter on 2010-05-07
Please bear with me going on regarding this,very new to the OS.

'I believe you can run (inside grub, using the ">" prompt) 'find  /boot/grub/stage1'

How and where do I enter that command?
In a little more details if you can(absolute noob,didn't really  understand a single word of that.) :|

Thanks yet again.

---

### Post by WorMzy on 2010-05-07
After the "sudo grub" command.

So you boot the 9.04 cd. Open a terminal. Type 'sudo grub'. Type 'find /boot/grub/stage1'. Then do 'root (hd0,0)', 'setup (hd0)', and 'exit', changing the "hd0,0" and "hd0" to what ever find found. :)

---

### Post by oldfred on 2010-05-07
this link has instruction for windows, grub legacy and now grub2. With 9.04 you need grub legacy.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by sp3kter on 2010-05-07
Wow!

Worked like a charm.
Really needed to have that up and running urgently.
Thanks for your patience and the detailed instructions WorMzy,oldfred and Dino99.
Words will prove inadequate to let you know how grateful I am,so a simple 'thank you!'

:)

---

