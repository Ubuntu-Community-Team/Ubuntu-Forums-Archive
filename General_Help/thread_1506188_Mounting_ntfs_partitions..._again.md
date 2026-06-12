---
title: "Mounting ntfs partitions... again"
date: 2010-06-10
forum: General Help
---

### Post by Istrebitel on 2010-06-10
Greetings

I struggled enough with ntfs partitions on the Kubuntu, i wasnt able to find a working solution on the webs, and nobody was able to help me solve them:
[http://ubuntuforums.org/showthread.php?t=1500554](http://ubuntuforums.org/showthread.php?t=1500554)
[http://ubuntuforums.org/showthread.php?t=1496349](http://ubuntuforums.org/showthread.php?t=1496349)
[http://ubuntuforums.org/showthread.php?t=1502420](http://ubuntuforums.org/showthread.php?t=1502420)

Now i switched to Ubuntu and situation changed. there is no longer an option to mount them via file manager, but there is a "disk manager" that allows mounting them, and doesnt ask a password! 

This is really nice, if i wouldnt have to do it every time i log in!

So i thought i'll automate it by adding fstab entry. but now, the problem is back again. As soon as i add an entry to fstab, even if i add an entry with user, give user access to mountpoint etc, the disk manager then can no longer mount the disk. It would spit random errors, with ???? and with standart "you got external fuse" etc stuff. The whole hell is back again

So my only point to avoid rootpromts and errors is to never touch fstab and only mount via this System-Administration-Disk utility.

But what is this Disk utility? 
And how come can it, without having root permissions, mount a disk (it even creates a directory for mountpoint owned by my user, while i cant do it if i dont elevate to root, not to mention the ntfs 3g doesnt have internal fuse and stuff, so it 100% SHOULD NOT BE ABLE TO DO IT EVER)
And how come when i add something to fstab, this Disk Utility starts to malfunction?
And what do i do about it?

Why are they doing it so complicated, not reusing standart linux ways of doing things (fstab) but making odd constructions around it? I dont understand, it makes Ubuntu much more complicated to get used to...

---

### Post by dcstar on 2010-06-10
> **Istrebitel said:**
> Greetings

I struggled enough with ntfs partitions on the Kubuntu, i wasnt able to find a working solution on the webs, and nobody was able to help me solve them:
.......
Why are they doing it so complicated, not reusing standart linux ways of doing things (fstab) but making odd constructions around it? I dont understand, it makes Ubuntu much more complicated to get used to...

Install the **pysdm** package and it isn't "complicated".

What makes things complicated is when people insist on using either the command line or manually hacking files when perfectly good GUI tools to do the job are ignored.

---

### Post by dino99 on 2010-06-10
mountmanager is an other easy solution

---

### Post by Istrebitel on 2010-06-10
no it wont solve anything, that psy package. I already checked that. It is just a gui to /etc/fstab. i know /etc/fstab by heart now.

If i make an entry in /etc/fstab, the disk manager will stop working and start spitting errors!

I will see if mountmanager is a solution...

---

### Post by Mark Phelps on 2010-06-10
My personal view (learned from hard experience) is that it's better to NOT include NTFS partitions in your fstab.

It's all too easy to have an unclean shutdown of an NTFS partition in Linux; somewhat less likely, but still possible, in MS Windows.

When that happens, your fstab mount will fail.

IF you're routinely getting fstab mount failures, something else is at fault.  Changing the front-end which still ends up generating the same fstab entries is not going to solve the mounting problems.

---

### Post by Istrebitel on 2010-06-10
I see. I dont insist on including somethign into Fstab. It is just people offer guis to fstab saying "this will do it" while it actually wont. I only need those drives mounted and working when i boot my system and whenever i plug something in (flash, hard drive, whatever). By whichever means possible.

And i seek to clear up the confusion of disk manager not being able to mount a drive anymore if i add fstab entry about it.

---

