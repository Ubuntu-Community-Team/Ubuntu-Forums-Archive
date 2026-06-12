---
title: "Can I take  a snapshot of my installation"
date: 2010-10-14
forum: General Help
---

### Post by Gudjon on 2010-10-14
Hello,

Would like to make an installation with a number of programs.
I would like to take a snapshot ( backup ) of my installation and being able to restore that later.

How can I take a snapshot, is it possible to 'save' everything to an ISO and burn
to a CD ?

I am using version 10.10.

regards, Gudjon

---

### Post by Jahid65 on 2010-10-14
you can use remastersys. This tool copies a to z of your current ubuntu installation.
[http://sourceforge.net/projects/remastersys/files/remastersys-ubuntu-karmic-lucid/remastersys_2.0.17-1_all.deb/download](http://sourceforge.net/projects/remastersys/files/remastersys-ubuntu-karmic-lucid/remastersys_2.0.17-1_all.deb/download) download the deb package

If you don't want to add your home folder run this in terminal
```
sudo remastersys dist
```
It may takes 20-25 minutes to complete. After that you find your ISO in File System>home>remastersys 

Or If you are looking something like acronis type tool, then you use partimage(for ext3) or clonezilla (ext3, ext4) or fsarchiver(for ext4). 1st & last one are on the repo.

---

### Post by Gudjon on 2010-10-21
HI Jahid!

I do not find any good guide for that program.
Is there any ?

which library do you mean when pointing to -> After that you find your ISO in File System>home>remastersys

regards, G

---

### Post by perspectoff on 2010-10-21
No question. Remastersys is the easiest and best.

Remastersys has a full wiki. I've used it many, many times. It's really easy.

I must say that I've had good luck with fsarchiver, too. The nice thing about fsarchiver is that your system can be reinstalled to a completely different partition size or even to a completely different filesystem (i.e. to ext4 from ext3, for example).

fsarchiver has saved me when doing major moves, for this reason.

fsarchiver is available as a Debian/Ubuntu package, but i don't think you can use it from a running OS.

For that reason I have used it from the Knoppix-based SystemRescueCD (although I think there are a few Ubuntu-based RescueCDs that also use it as well).

There is a broad list of options at

[http://ubuntuguide.org/wiki/Ubuntu:All#System_Backup_and_Recovery](http://ubuntuguide.org/wiki/Ubuntu:All#System_Backup_and_Recovery)

and

[http://kubuntuguide.org/All#System_Backup_and_Recovery](http://kubuntuguide.org/All#System_Backup_and_Recovery)

---

