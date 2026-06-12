---
title: "Clone hard drive application"
date: 2009-07-27
forum: General Help
---

### Post by mrramsey on 2009-07-27
What should I look at for an application that will work like Acronis true image for windows?

An easy to use app that will clone my hard drive down to every bit of data.

I'm an Ubuntu newbie -- wow -- what a blast this software is !

---

### Post by kaibob on 2009-07-27
Have a look at:

Clonezillla
[http://www.clonezilla.org/](http://www.clonezilla.org/)

Partimage
[http://www.partimage.org/](http://www.partimage.org/)

Ghost for Linux
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

I have personally used Clonezilla, and it works well, although grub issued error messages after a restore. I have used Acronis True Image for many years, and it also works well, but you have to run it from within Windows or from a CD/DVD. Also, True Image does not work with EXT4 except on a sector-by-sector basis.

---

### Post by mrramsey on 2009-07-27
So it's actually possible to use true image? Come to think about it, I created a dual boot
system when I installed Ubuntu.

I do love the accuracy and simplicity of true image but if you think clonezilla will work just as well then I'll try it instead.

Love Ubuntu -- just as soon get rid of XP completely for this PC.

---

### Post by mrramsey on 2009-07-27
running clonezilla right now.

it's asking for my user name but not taking it ?

putting in same user name as my ubuntu login ?

---

### Post by kaibob on 2009-07-27
> **mrramsey said:**
> ...I do love the accuracy and simplicity of true image but if you think clonezilla will work just as well then I'll try it instead...
I didn't mean to imply that. I personally find True Image to be much superior to Clonezilla both as to ease of use and reliability. I especially like True Image 10, which is the one I use to backup my Windows/Linux drive. 

As an aside, I believe a clean install of Ubuntu 9.04 uses an inode size that is compatible with the latest version of True Image 2009 but not with earlier versions. There are easy workarounds for this, but I thought I should mention this.

---

### Post by mrramsey on 2009-07-27
Ok thanks for helping me with this.

Like I say running clonezilla right now but I'm stalled at the user@jaunty prompt


what do I put there for user and pass?

I keep putting in my ubuntu user but it says command not found.

thanks !

---

### Post by mrramsey on 2009-07-27
also -- I own true image home 2009.

I'll look into it but it possibly will work under Ubuntu as is somehow?

Create a boot disk with it or something?

---

### Post by mrramsey on 2009-07-27
Answering my own questions (and for the benefit of any future search) -- looks as though I can create a boot disk for backing up linux with my true image.

Since I've had excellent luck with it I'll use it.

Great !

Thanks for the help.

---

### Post by Marsolin on 2009-07-27
If you only use Acronis for cloning a drive and not the other features then the simplest method is dd.  It is using the commandline, but it's fast and easy once you get comfortable with it.

dd if=/dev/sda of=/dev/hda

if is the location of the source drive you want to clone
of is the location of the empty drive

The other apps mentioned will work as well if the commandline isn't an option or you want some of the other features.

---

### Post by scouser73 on 2009-07-27
Hey mrramsey, you should take a look at [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html").

It might be of use for you, I know it was for me, am glad you're liking Ubuntu.

---

### Post by mrramsey on 2009-07-27
FYI -- for anyone searching.

True image 2009 works perfect with Ubuntu, just load the boot disk.

It does give some elaborate warning about how the target drive may not boot but I
just ignored it and clicked OK.

Worked like a champ.

In fact, faster than it does under windows.

Case closed.

---

