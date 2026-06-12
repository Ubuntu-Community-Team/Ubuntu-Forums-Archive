---
title: "Getting &quot;busybox&quot; ubuntu installation."
date: 2011-06-07
forum: General Help
---

### Post by shooninjo on 2011-06-07
Hey. I am trying to install Ubuntu alongside Windows for programing learning, everything went fine until the installation of Ubuntu. I keep getting error messages and it end in something called "busybox". Looks like CMD. I have tried using the Iso on a cd and on a USB. Nothing works. I dont know what is wrong?

"BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) -"

Also like this: Chroot: cant execute mktemp: no such file or directory. 

After that it is like a wall of text of error messages.. :/

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **shooninjo said:**
> Hey. I am trying to install Ubuntu alongside Windows for programing learning, everything went fine until the installation of Ubuntu. I keep getting error messages and it end in something called "busybox". Looks like CMD. I have tried using the Iso on a cd and on a USB. Nothing works. I dont know what is wrong?

"BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) -"

Also like this: Chroot: cant execute mktemp: no such file or directory. 

After that it is like a wall of text of error messages.. :/

Sounds like a grub2 issue.  You may have other systems installed previous to Ubuntu.  Hang in there for a Grub specialist to read your post and provide you with help.:guitar:

---

### Post by shooninjo on 2011-06-07
> **linuxinstalledfromhdd said:**
> Sounds like a grub2 issue.  You may have other systems installed previous to Ubuntu.  Hang in there for a Grub specialist to read your post and provide you with help.:guitar:

dunno what a "grub2" is though.

---

### Post by FormatSeize on 2011-06-07
How much memory do you have?
The problem was brought up some time ago in [this thread](http://ubuntuforums.org/showthread.php?t=807345), and it turns out that a full, normal installation was being hampered by a machine with a smaller amount of memory than what Ubuntu required.

You can try the suggestion mentioned there, or you can try to install Xubuntu, which is a smaller Ubuntu. It'll still have everything you need to begin learning programming. If that doesn't work, or if you have a machine with enough memory that *should* be handling Ubuntu, then we'll see what else we can come up with.
 
As for it being an issue with Grub2, from my experience, problems with Grub normally don't yield busybox. If it did, I would not have spent 4 straight days screaming and cursing at the grub rescue prompt.

---

### Post by FormatSeize on 2011-06-07
> **shooninjo said:**
> dunno what a "grub2" is though.
The bootloader for Ubuntu is called Grub. The most recent version is Grub 2, and it is analogous to NTLDR (New Technology LoaDeR) in Windows and LILO (LInux LOader) in other Linux systems.

---

### Post by linuxinstalledfromhdd on 2011-06-07
See what I did was install windows in Virtualbox 4 inside of Ubuntu so I could wipe my entire hard drive and just have Ubuntu on there.  That's one option too.  If you wipe the entire drive (as long as you have you stuff backed up) and install Ubuntu 10.10, and then your virtualbox 4 for WinXp, you should be ok.

---

### Post by shooninjo on 2011-06-07
> **FormatSeize said:**
> How much memory do you have?
The problem was brought up some time ago in [this thread]("http://ubuntuforums.org/showthread.php?t=807345"), and it turns out that a full, normal installation was being hampered by a machine with a smaller amount of memory than what Ubuntu required.

You can try the suggestion mentioned there, or you can try to install Xubuntu, which is a smaller Ubuntu. It'll still have everything you need to begin learning programming. If that doesn't work, or if you have a machine with enough memory that *should* be handling Ubuntu, then we'll see what else we can come up with.
 
As for it being an issue with Grub2, from my experience, problems with Grub normally don't yield busybox. If it did, I would not have spent 4 straight days screaming and cursing at the grub rescue prompt.

I have a hard drive with 900+ gig, and i shrinked some of it (244 gig) to ubuntu. I am quite sure that the memory isnt the problem. It just popps up, however the installation runs smoothly until that point, after the ubuntu has done its "thing", like in the ubuntu screen. Then it comes a walll of text that eventually leads to that freaking box.

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **shooninjo said:**
> I have a hard drive with 900+ gig, and i shrinked some of it (244 gig) to ubuntu. I am quite sure that the memory isnt the problem. It just popps up, however the installation runs smoothly until that point, after the ubuntu has done its "thing", like in the ubuntu screen. Then it comes a walll of text that eventually leads to that freaking box.

Could be video driver?   

Are you using 10.10 or 11.04?

I would try again with 10.10, and see if it boots from a live disc to find out what the logs say.

---

### Post by shooninjo on 2011-06-07
> **linuxinstalledfromhdd said:**
> Could be video driver?   

Are you using 10.10 or 11.04?

I would try again with 10.10, and see if it boots from a live disc to find out what the logs say.

Never had any problem with the driver so far. 

Ive downloaded the latest, think its 11.04? Gonna download 10.10 and see. Ill write when I have it.

---

### Post by linuxinstalledfromhdd on 2011-06-07
Yeah, just see if it makes any difference or not. :guitar:

---

### Post by FormatSeize on 2011-06-07
> **shooninjo said:**
> I have a hard drive with 900+ gig, and i shrinked some of it (244 gig) to ubuntu.
Jeez... 
 
Okay. That's definitely not the problem. [I also found this]("http://ubuntuforums.org/showthread.php?t=1561735"), which is a little more recent. It contains instructions on how to go about getting the system to boot properly, but you are going to have to do a little typing, and you have to know the names of your partitions ((hdX,Y), etc), and which one is the Linux partition. It's not difficult to find your linux partition because it should contain a folder called "home".
 
Let us know how that works out for you.
 
> **linuxinstalledfromhdd said:**
> Yeah, just see if it makes any difference or not. :guitar:
 
Good call. I've tried 11.04, and it just didn't seem to function properly, and I'm thinking it's the whole Unity thing. When I try Fedora 15 (which I think has Unity, too) it just goes:
```

lol
```
Of course, I do only have 40 Gigs on my hard drive and one gig of RAM, but it does all the fancy KDE4 desktop affects seemlessly. It seems to only have a problem with Unity.

---

### Post by shooninjo on 2011-06-07
> **linuxinstalledfromhdd said:**
> Yeah, just see if it makes any difference or not. :guitar:

Soon going to install the previous version. Telling how it went asap.

---

### Post by shooninjo on 2011-06-07
The 10.10 version worked :D 

Dont know why the latest does not though..

---

### Post by linuxinstalledfromhdd on 2011-06-07
They say 11.04 doesn't have more bugs than older versions. I don't think they really know if that's true or not. How could they?

Goodluck.

---

### Post by shooninjo on 2011-06-08
> **linuxinstalledfromhdd said:**
> They say 11.04 doesn't have more bugs than older versions. I don't think they really know if that's true or not. How could they?

Goodluck.

Dont know. Think I am going to wait until a stable release or until I find someone who really knows how to fix it. Thanks for the help anyways. Running both Ubuntu and Windows now :)

---

