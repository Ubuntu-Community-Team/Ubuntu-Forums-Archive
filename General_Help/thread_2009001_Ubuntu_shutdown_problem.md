---
title: "Ubuntu shutdown problem"
date: 2012-06-23
forum: General Help
---

### Post by dane131 on 2012-06-23
Hallo,

I have ubuntu 12.04 LTS installed on my 64bit desktop computer.When I  press shutdown and the pc turns off the keyboard and mouse lights are still on.When i choose to first logout and then shutdown only the mouse light remains on.Any help?

Thanks in advance

---

### Post by Redblade20XX on 2012-06-23
Try typing these commands in the terminal and tell us what happens. I'm getting to old to remember which one works on Ubuntu as I use several distros.

```
sudo halt
```

If that doesn't work try,

```
sudo shutdown
```

-Red

---

### Post by dane131 on 2012-06-24
Hallo,

I tried both of the commands and the system crashed at the ubuntu splash screen [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by Shadius on 2012-06-24
> **dane131 said:**
> Hallo,

I tried both of the commands and the system crashed at the ubuntu splash screen [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

I usually use 
```
sudo shutdown -P now
```

That'll shut down the system immediately, hence the *now*. You can read the man page of the shutdown command for more information.

---

### Post by dane131 on 2012-06-24
> **Shadius said:**
> I usually use 
```
sudo shutdown -P now
```That'll shut down the system immediately, hence the *now*. You can read the man page of the shutdown command for more information.

The -P parameter turned off the pc but the initial problem still remains (keyboard and mouse lights are still on)

---

### Post by Shadius on 2012-06-24
Which version of Ubuntu are you using and what is your kernel? 

You can do in Terminal: 
```
uname -r
```
to show the kernel release.

---

### Post by dane131 on 2012-06-24
> **Shadius said:**
> Which version of Ubuntu are you using and what is your kernel? 

You can do in Terminal: 
```
uname -r
```to show the kernel release.
 
I am using ubuntu 12.04 LTS 64 bit

kernel release :3.2.0-25-generic

---

### Post by Shadius on 2012-06-24
Kind of stumped now. Have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1399730"). Some useful suggestions there. Sorry I couldn't be of more help. ](*,)

---

### Post by dane131 on 2012-06-24
I checked the thread..I tried to suspend the pc instead of shutting it down and the pc remained on power with a black screen but **the usb devices were turned off.**..

The other strange thing about my pc are the multiple entries of the operating systems in the grub ..for example,i have two entries for ubuntu in the grub...i don't know if this is somehow related

Finally my system is using :AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ × 2 

Just gave sou some info which may be irrelevant but i am so frustrated with this problem!

---

### Post by Shadius on 2012-06-25
> **dane131 said:**
> I checked the thread..I tried to suspend the pc instead of shutting it down and the pc remained on power with a black screen but **the usb devices were turned off.**..

The other strange thing about my pc are the multiple entries of the operating systems in the grub ..for example,i have two entries for ubuntu in the grub...i don't know if this is somehow related

Finally my system is using :AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ × 2 

Just gave sou some info which may be irrelevant but i am so frustrated with this problem!

Two entries of Ubuntu, or do you mean one that's regular Ubuntu and another with the recovery console? If so, that's normal. 

Okay, so suspending the PC shuts down the USB devices, while shutting down the PC, keeps the USB devices powered. Very strange! ](*,) :confused: I came across a bug report which was solved by upgrading the kernel, but I don't know if that's the problem in your case. Maybe someone else will know more about this. I'm stumped.

---

### Post by dane131 on 2012-06-25
> **Shadius said:**
> Two entries of Ubuntu, or do you mean one that's regular Ubuntu and another with the recovery console? If so, that's normal. 

Okay, so suspending the PC shuts down the USB devices, while shutting down the PC, keeps the USB devices powered. Very strange! ](*,) :confused: I came across a bug report which was solved by upgrading the kernel, but I don't know if that's the problem in your case. Maybe someone else will know more about this. I'm stumped.

No,the two entries of the grub are duplicate entries for the regular ubuntu.I also have duplicate entries for Windows 7 in the grub.Thanks for your help anyway!

---

### Post by Shadius on 2012-06-25
> **dane131 said:**
> No,the two entries of the grub are duplicate entries for the regular ubuntu.I also have duplicate entries for Windows 7 in the grub.Thanks for your help anyway!

Now that is strange. Were both operating systems installed twice? I've had an experience when I installed Windows XP Professional twice and ended up with two entries. I wonder if GRUB has messed up...

---

### Post by nipunshakya on 2012-06-25
okay buddy... its time you update your grub first if you want to get rid of your double entries...
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
run it in live cd mode and fix your grub issue  if u wish to..

---

### Post by Shadius on 2012-06-25
Also, which version of Ubuntu are you using? I remember older versions of Ubuntu used to have kernel updates in the GRUB menu. Also, do you know if you have a recovery partition for Windows? That's the only reason I can think of for having duplicate entries for Windows. 

Something like:
> Ubuntu, Linux 2.6.32-25-generic
Ubuntu, Linux 2.6.32-25-generic (recovery mode)
Ubuntu, Linux 2.6.32-24-generic
Ubuntu, Linux 2.6.32-24-generic (recovery mode)
Windows 7 (loader) (on/dev/sda1)
Windows 7 (loader) (on/dev/sda2)

Notice that the Ubuntu entries have updated kernel entries with the Linux 2.6.32-[COLOR="Red"]24[/COLOR] versus the Linux 2.6.32-[COLOR="Red"]25[/COLOR]. The duplicate entries for the Windows 7 could be your Windows Recovery Partition. 

We meet again WinuxUser):P

---

### Post by dane131 on 2012-06-26
> **Shadius said:**
> Also, which version of Ubuntu are you using? I remember older versions of Ubuntu used to have kernel updates in the GRUB menu. Also, do you know if you have a recovery partition for Windows? That's the only reason I can think of for having duplicate entries for Windows. 

Something like:


Notice that the Ubuntu entries have updated kernel entries with the Linux 2.6.32-[COLOR=Red]24[/COLOR] versus the Linux 2.6.32-[COLOR=Red]25[/COLOR]. The duplicate entries for the Windows 7 could be your Windows Recovery Partition. 

We meet again WinuxUser):P

Hallo Shadius,

In the atatchments i have:

1. a picture of my disk volumes
2. a picture of the grub

*The final entry of the grub picture says : windows7 (loader) on dev/sda2 and links to the same OS as the previous entry.

Maybe i will try the link that WinuxUser posetd.

---

### Post by nipunshakya on 2012-06-26
There is nothing wrong with your ubuntu's appearance on the grub... its totally fine with that... only thing mistaken is your windows' entry....

---

### Post by Shadius on 2012-06-26
> **dane131 said:**
> Hallo Shadius,

In the atatchments i have:

1. a picture of my disk volumes
2. a picture of the grub

*The final entry of the grub picture says : windows7 (loader) on dev/sda2 and links to the same OS as the previous entry.

Maybe i will try the link that WinuxUser posetd.

As WinuxUser said, your GRUB is fine. I don't see any duplicate entries for Ubuntu there. I do see what appears to be a System Recovery partition from your screenshot of the disk drives though. That would account for the second entry for Windows, *sda2*. I think *sda1* is your regular OS.

---

### Post by YannBuntu on 2012-06-27
Hello
I confirm that GRUB is fine.
For information, the 2nd Windows entry was created by Boot-Repair, in order to allow you to access Windows in case the 1st entry was blocked by a bootsector problem.

Concerning your reboot/shutdown problem, this is a problem I have seen many times on this forum, but I have never seen any standard solution.

Some solved the problem by using:
```
sudo poweroff
```
or 
```
sudo reboot
```

Sometimes it was due to a bug (eg [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/858122](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/858122)).

Some recommend to remove "quiet splash" from GRUB options to see if any error message. Some recommend to add a "reboot=***" kernel option to GRUB...

Good luck!

---

