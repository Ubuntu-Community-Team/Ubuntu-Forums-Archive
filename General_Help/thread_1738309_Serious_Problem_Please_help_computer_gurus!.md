---
title: "Serious Problem?? Please help computer gurus!"
date: 2011-04-24
forum: General Help
---

### Post by SL1DEmemphis on 2011-04-24
I am trying to boot up my computer which has the Ubuntu 11 beta AMD 64bit, but before I can reach the login screen I get a black screen with the word  "Killed"  in the top left-hand corner.  If I attempt the recovery boot I get different messages.  I am no expert, so if anyone can help me decipher this you would have my thanks.

[IMG]http://a8.sphotos.ak.fbcdn.net/hphotos-ak-snc6/217692_1679559638026_1508580008_31284745_1786349_n.jpg[/IMG]

[IMG]http://a5.sphotos.ak.fbcdn.net/hphotos-ak-snc6/222465_1679558397995_1508580008_31284742_5739400_n.jpg[/IMG]

---

### Post by SL1DEmemphis on 2011-04-24
Sorry, I forgot my specs

AMD Phenom II 965
ASUS M4a78t-e motherboard
OCZ Vertex II 30gb SSD (OS)
WD 750Gb HDD
ASUS Xonar D2 (audio)
ATI Radeon 5850 
4x2gb OCZ 1600 memory

---

### Post by Sun.Dial on 2011-04-24
Hi, I found a useful script for boot debugging by meierfra, post the o/p.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Regards,
Sun

---

### Post by SL1DEmemphis on 2011-04-24
I don't think I can do that, I cannot enter the OS to open a terminal.  Also, I am pretty new to linux, so all of this is a new language to me. I have always been a Windows user, I'm in new territory.

---

### Post by Sun.Dial on 2011-04-24
Oh sorry, you need to boot up using the Ubuntu live cd, then go to the terminal window to run that script file...I'm a beginner of sorts too, but I've just done this and it has been very helpful. Good luck. Sun

---

### Post by Horseboy on 2011-04-24
It seems like it's saying GRUB isn't installed Oo

I think this is more than likely a BIOS issue. Mess around with the power management settings in your BIOS setup, I used to get similar messages because of it.

---

### Post by KegHead on 2011-04-24
Hi!

I can't tell if you're booting from a hd, stick or cd?

Would it possible to reinstall?

KegHead

---

### Post by SL1DEmemphis on 2011-04-24
I trying to boot from my SSD which has ubuntu on it.  it worked for 24hrs, froze in the middle of a youtube video, now I cant get back to the os

---

### Post by SL1DEmemphis on 2011-04-24
Also, If I try to boot from disk, I get the same message.  I can't even get to the installation menu to reformat.

---

### Post by KegHead on 2011-04-24
Hi!

On start up can you access your bios?

KegHead

---

### Post by SL1DEmemphis on 2011-04-24
> **Horseboy said:**
> It seems like it's saying GRUB isn't installed Oo

I think this is more than likely a BIOS issue. Mess around with the power management settings in your BIOS setup, I used to get similar messages because of it.

I'll give this a try, but I have tried resetting my bios by taking out the battery with no luck.  I haven't had this problem before and I have been running this pc for around a year.

---

### Post by SL1DEmemphis on 2011-04-24
> **KegHead said:**
> Hi!

On start up can you access your bios?

KegHead

Yes, I can access the bios.

---

### Post by KegHead on 2011-04-24
Hi!

You might try some of your settings.

KegHead

---

### Post by SL1DEmemphis on 2011-04-24
> **KegHead said:**
> Hi!

You might try some of your settings.

KegHead

I'm sorry I don't know what you mean?

---

### Post by KegHead on 2011-04-24
Hi!

When you access your bios..there are a number of settings etc.

Does something look out of place or wrong?

KegHead

---

### Post by SL1DEmemphis on 2011-04-24
> **KegHead said:**
> Hi!

When you access your bios..there are a number of settings etc.

Does something look out of place or wrong?

KegHead

Not sure, I'll have to get back to you.  I'm on another pc at another house.  I'm just going to take more pictures of the screen :D

---

### Post by KegHead on 2011-04-24
Hi!

By any chance did you overclock?

Also, have you tried 32 bit Ubuntu on this machine?

KegHead

---

### Post by SL1DEmemphis on 2011-04-24
> **KegHead said:**
> Hi!

By any chance did you overclock?

Also, have you tried 32 bit Ubuntu on this machine?

KegHead

I was not overclocked in linux.  I have in win7 before I replaced it with ubuntu.  Of course I had to reformat and install linux because Win7 blue screened before it would get to the OS too.  But I had been overclocked for a good while.  So IDK why that would be the cause? [I used TurboV to overclock in Win7)

Also, no I didnt use 32bit ubuntu.

---

### Post by KegHead on 2011-04-24
Hi!

Just curious, I heard thru the grapevine that overclocking causes voltage issues, etc.

kegHead

---

### Post by SL1DEmemphis on 2011-04-24
Yes, it can.  I tried to make sure there weren't any issues like that.  I didn't really up volts much if any at all.

---

### Post by Krytarik on 2011-04-24
It seems like it's a disk failure, or at least a needed file system check.

- boot into a LiveCD
- use GParted (System -> Administration) to check your system partition, you may need to disable your swap partition, if you have one, either can be done via the right-click menu in GParted.

- you can also use "fsck" to check your system partition, but the same is true about the swap partition:
[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)
- you can also use this command to disable your swap partition:
```
sudo swapoff -a
```Hope it helps!

---

### Post by SL1DEmemphis on 2011-04-24
> **Krytarik said:**
> It seems like it's a disk failure, or at least a needed file system check.

- boot into a LiveCD
- use GParted (System -> Administration) to check your system partition, you may need to disable your swap partition, if you have one, either can be done via the right-click menu in GParted.

- you can also use "fsck" to check your system partition, but the same is true about the swap partition:
[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)
- you can also use this command to disable your swap partition:
```
sudo swapoff -a
```Hope it helps!

Im starting to think its my motherboard.  I tried another hard drive and I can't even boot from the linux CD to format and install.  looks like Ill be getting a new board.

---

### Post by Krytarik on 2011-04-24
> **SL1DEmemphis said:**
> Im starting to think its my motherboard.  I tried another hard drive and I can't even boot from the linux CD to format and install.  looks like Ill be getting a new board.
I would try different connectors/cables first.

---

### Post by Horseboy on 2011-04-25
> **SL1DEmemphis said:**
> I'll give this a try, but I have tried resetting my bios by taking out the battery with no luck.  I haven't had this problem before and I have been running this pc for around a year.

A BIOS reset isn't what I was talking about, when your computer starts you should be able to get into the BIOS setup. From there have a look at the power management and give us a picture of it.

---

### Post by SL1DEmemphis on 2011-05-08
> **Horseboy said:**
> A BIOS reset isn't what I was talking about, when your computer starts you should be able to get into the BIOS setup. From there have a look at the power management and give us a picture of it.

So, I don't know what is going on, but today I booted the computer up and it went straight to the OS... after 2 weeks of giving me hell.  I didn't do anything more since the last time I messed with it.  I wanted to know whats going on.   Let me get some pictures of my bios though.

---

### Post by SL1DEmemphis on 2011-05-08
heres my power settings
[IMG]http://a2.sphotos.ak.fbcdn.net/hphotos-ak-snc6/230995_1702135002396_1508580008_31316870_4942969_n.jpg[/IMG]
[IMG]http://a5.sphotos.ak.fbcdn.net/hphotos-ak-ash4/227991_1702134402381_1508580008_31316869_663011_n.jpg[/IMG]

---

### Post by Telengard C64 on 2011-05-08
> **SL1DEmemphis said:**
> I tried another hard drive and I can't even boot from the linux CD to format and install.  looks like Ill be getting a new board.

It might be more economical to replace the drives and connectors before buying a new motherboard.

Random boot failures can also be caused by badly installed heat sink and fan, ill configured BIOS, power fluctuations, bad memory, and any number of other things.

---

### Post by SL1DEmemphis on 2011-05-09
> **Telengard C64 said:**
> It might be more economical to replace the drives and connectors before buying a new motherboard.

Random boot failures can also be caused by badly installed heat sink and fan, ill configured BIOS, power fluctuations, bad memory, and any number of other things.

You're right, its now come to random boot failures.  This is frustrating!  I tried different Sata cables in different ports, I've reset the heatsink, checked all connections. I guess Ill try switching out the memory with some others sticks i have.  Ill be back for updates.

---

