---
title: "Can't access CD/DVD drive in Ubuntu 10.04 Virtualbox"
date: 2011-12-20
forum: General Help
---

### Post by linuxspy007 on 2011-12-20
Hi,

I'm running Ubuntu 10.04 VM Oracle Virtualbox and I can no longer access the CD/DVD drive.  I pop in an audio CD and it doesn't seem to mount....Previously, I would put it in and a music player came up automatically ...Now it says something like can't find /dev/sr0. (Note: I had just recently re-copied my Ubuntu VM data from a 32 GB container into a 80 GB container using gparted and clonezilla - this is when I had the CD issue - it occurs now in both VMs - the 32 [the original] and 80GB [the copy] ones).

How do I fix this?

From other threads I found it might be helpful to post this info:
=======================================
lshw -C disk
WARNING: you should run this program as super-user.
  *-cdrom                 
       description: DVD reader
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/VBOXADDITIONS_4.1.6_74713
       capabilities: audio dvd
       configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
=======
Also, when I tried to mount /dev/sr0 I got a msg saying it was already mounted in Vbox guest additions.

---

### Post by jualin on 2011-12-20
I am assuming that you are running Ubuntu in a virtual machine from Windows. Check under the Virtual Machine settings that you have your [CD/DVD drive enabled ]("http://grok.lsu.edu/Article.aspx?articleId=13783"). Hope this helps.

---

### Post by linuxspy007 on 2011-12-20
Yes, I am running it over Vista....Thank you...I hate to ask this - but I don't see that option anywhere (I am running Oracle Virtualbox 4.1.6) and I've been looking - are we talking about the same Virtual Box?

---

### Post by QIII on 2011-12-20
Heck.  Scratch all of that.  I'm just a doddering old fool.

Check the manual at ...

download.**virtualbox**.org/**virtualbox**/UserManual.pdf

---

### Post by linuxspy007 on 2011-12-21
No, thank you - wish you hadn't erased it since what you told me worked.....many thanks!  I thought I just had to have the *GuestAdditions.iso mounted - but now I remember I only installed it ages ago (VBox 4.0)  for USB support...I must have forgot to add the CD drive and when I did the copy it didn't take.

One curiosity I had - in my cd ripping program on Ubuntu I noticed it had "/dev/cdrom" as the default path to the CD drive - I had to change it to "/dev/sr1" to get it to work again - should my system have a "/dev/cdrom" path "registered"?

---

