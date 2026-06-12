---
title: "New to Linux,need help."
date: 2010-01-14
forum: General Help
---

### Post by Rossg on 2010-01-14
As the title says, I'm pretty much completely new to Ubuntu,I've only used it once before but I didn't want to learn to use it at the time and just used Windows.Now I really want to learn but I keep running into problem after problem with Linux and I'm pretty much lost. If someone could give me a link to a beginers guide or something to help me out that would be great.
Thanks in advance.

---

### Post by audiomick on 2010-01-14
What are you having problems with?

---

### Post by Grenage on 2010-01-14
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

---

### Post by muteXe on 2010-01-14
Yea, are you actually having problems or do you just need a beginners intro into linux?

---

### Post by Rossg on 2010-01-14
Well, it's a bit of a list but I'll start from the beginning.The first problem I ran into was with my graphics card. I was trying to install the drivers for it and when I did I would get past the login screen to a screen with 'Input not Supported' on it. After booting in recovery mode and doing the automatic graphic fix (I think that's what it was called) I got my screen back.After some searching, I found some answers, but none that I understood.Great.So, hoping that maybe upgrading to the newest stable version of Ubuntu(I'm using 9.04) would magically cure this problem I tried upgrading to 9.10. In the middle of the upgrade I start getting all these error messages telling me that a bunch of files can't be updated, I paniced because I thought I was going to get some unholy mess of a half upgraded screwed up OS.I figured I would be better off reinstalling Ubuntu 9.04 altogether and starting over(probably not the best idea).Well I did that but I must have accidentally partitioned the disk instead of formatting it, because I had two copies of Linux on my HDD.After I realized this, I reinstalled again but this time using the whole disk.But now when I try to boot up I get GRUB Error 15, which I read up on a bit, but frankly have no idea what I'm reading(I'm using a Live CD right now).
Oh and also my 1TB External HDD is acting up now . It shows on the desktop as two devices, so I'm guessing it somehow got partitioned in this whole mess.The device showing up that I think is the partitioned part of my external shows up as 2.5 GB and has folders named bin,boot,cdrom,dev and a bunch of other folders as well. I don't know what this stuff is but you guys probably do.Basically I'm in way over my head and I need a lot of help.:confused:

---

### Post by mk1w86 on 2010-01-14
> **Rossg said:**
> Well, it's a bit of a list but I'll start from the beginning.The first problem I ran into was with my graphics card. I was trying to install the drivers for it and when I did I would get past the login screen to a screen with 'Input not Supported' on it. After booting in recovery mode and doing the automatic graphic fix (I think that's what it was called) I got my screen back.After some searching, I found some answers, but none that I understood.Great.So, hoping that maybe upgrading to the newest stable version of Ubuntu(I'm using 9.04) would magically cure this problem I tried upgrading to 9.10. In the middle of the upgrade I start getting all these error messages telling me that a bunch of files can't be updated, I paniced because I thought I was going to get some unholy mess of a half upgraded screwed up OS.I figured I would be better off reinstalling Ubuntu 9.04 altogether and starting over(probably not the best idea).Well I did that but I must have accidentally partitioned the disk instead of formatting it, because I had two copies of Linux on my HDD.After I realized this, I reinstalled again but this time using the whole disk.But now when I try to boot up I get GRUB Error 15, which I read up on a bit, but frankly have no idea what I'm reading(I'm using a Live CD right now).
Oh and also my 1TB External HDD is acting up now . It shows on the desktop as two devices, so I'm guessing it somehow got partitioned in this whole mess.The device showing up that I think is the partitioned part of my external shows up as 2.5 GB and has folders named bin,boot,cdrom,dev and a bunch of other folders as well. I don't know what this stuff is but you guys probably do.Basically I'm in way over my head and I need a lot of help.:confused:

I think the best thing to do would be to reinstall Ubuntu from scratch with any external hard drives disconnected. ;)

If you want to use Ubuntu 9.10 (which might work with your graphics card) I recommend you do a fresh install.

---

### Post by Rossg on 2010-01-14
I think a fresh install without the external would be good too, but what can I do about the 2.5 GB that are floating around?Is the stuff in there safe to delete ?I can't just format the external, because there's other peoples data on there, not to mention all my music.

---

### Post by khelben1979 on 2010-01-14
First, you need to calm down a bit, then have a look at [this video]("http://www.youtube.com/watch?v=qFTtKnoVutk"). Take your time and watch closely what he does.

There are other videos available as well if the above is not what you're looking for.

---

### Post by mk1w86 on 2010-01-14
> I think a fresh install without the external would be good too, but what can I do about the 2.5 GB that are floating around?

As long as it is not your personal data and you're going to do a fresh install of Ubuntu all that stuff should be safe to delete although you might want to get Ubuntu up and running first then sort out your external hard drive. :D

---

### Post by Rossg on 2010-01-14
Okay, I'm going to try a fresh install of 9.04 now, without my external hooked up.I'll post when It's finished.Thanks everyone

---

### Post by audiomick on 2010-01-14
Starting over is probably a good idea.

If you are interested in 9.10, burn a live cd and boot into the "try without changing" option to see how well your system runs with it.

It would make the install simpler, perhaps, to unplug the external HDD during your install. That would avoid having grub, the bootloader, on the wrong HD, or accidently installing to the wrong HD. This only leaves the problem of integrating the external HD later on.

The Grub error 15 _might_ have to do with having more than one disk, and the multiple install attempts.

from the Grub2 documentation
> File Not Found (Error 15)

This error is the result of a GRUB 2 installation to /boot but a Master Boot Record ( MBR ) which still contains Grub legacy. This can happen if you don't select your drive when running sudo update-from-grub-legacy. Shortly after starting this command the user will be asked to select the device (sda, sdb, etc). Highlight the drive and press the space bar to select it when presented with this screen. Failure to select a drive will result in an Error 15.

To recover from this error, GRUB 2 must be reinstalled. Go to Reinstalling from the LiveCD for instructions.



As you may be aware, 9.04 used grub legacy and 9.10 grub2.

What you can do right away from the live cd is go to
system> administration> gparted and have a look at what partitions are now on your HDD's.

If you have all your stuff backed up, you could use the opportunity to re-partition the external HDD the way you want it.

For info about partitioning, look here
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
don't be thrown by the windows references, the partitioning advice from the various links applies for linux only installs as well.

If you have stuff on your original install that you want to save, you could perhaps save it to the external HDD before you start re-installing (if it hasn't already all been overwritten)

---

### Post by mick222 on 2010-01-14
have a look at this guide it might help
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
Especially the part on partitioning

---

### Post by Rossg on 2010-01-14
Okay so I've done the fresh install,no GRUB Error, but now I can't seem to find my HDD. Before it was listed under 'Places' as 197 GB media.Now it isn't. Any idea what thats about?

---

### Post by audiomick on 2010-01-14
you had it disconnected during the install?
can you see it with
```
sudo fdisk -l
```

---

### Post by Rossg on 2010-01-14
Yes, I can see it when I do that but I still don't see it in 'Places' and I know I did before. BTW I'm talking about my internal HDD, not my external which I didn't have plugged in during installation..

Anyways, my graphics card seems to be working now even though I didn't upgrade or do anything differently :confused:.Still no HDD in 'Places' though.

---

### Post by mk1w86 on 2010-01-14
Could you please post the output of:

```
sudo fdisk -l
```

When you say 'internal HDD', I assume it is the one Ubuntu is installed on?

---

### Post by Rossg on 2010-01-14
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45019fd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24041   193109301   83  Linux
/dev/sda2           24042       24792     6032407+   5  Extended
/dev/sda5           24042       24792     6032376   82  Linux swap / Solaris
ross@ross-desktop:~$ 


And yes, I'm talking to the HDD Linux is installed on.

---

### Post by audiomick on 2010-01-14
> Before it was listed under 'Places' as 197 GB media.Now it isn't. Any idea what thats about?

actually, that sounds more like an external drive or some plug in thing.
The drive that you are installed to should be turning up as something like "personal directory" (sorry, mine is called  "persönlicher Ordner". I have actually no idea what it is called in an english install...) for your home folder, and "file system" or maybe "computer" to get to /

What have you got in "places"?

---

### Post by t0p on 2010-01-14
> **Rossg said:**
> Before it was listed under 'Places' as 197 GB media.Now it isn't. Any idea what thats about?

You're talking about your internal HDD, the one you have Ubuntu installed on, yes?

Before, when you were running from a live cd, the HDD would have been listed uder Places as 197 GB Media, as you say; when you were running from the live cd, you weren't runing Ubuntu from that HDD, therefore Ubuntu saw it as an "external" drive.

But now you have Ubuntu running from the HDD, it's no longer seen as an external drive.  So, when you click on Places, you'll see "Home folder" - that's your home directory at /home/username, on the HDD.  Also under Places is "Computer" -  click on that, then select "Filesystem" and you'll see the contents of the HDD.

---

### Post by Rossg on 2010-01-15
Well t0p that makes the answer seem obvious haha, thank you. 

Now, for some reason, Ubuntu keeps freezing every ten seconds or so. I got rid of the drivers for my graphics card because I thought that may be causing it, but it's still happening.I'm going to look around for other people who have had this problem, but if anyone knows what it might be I would appreciate the help:D

---

### Post by Rossg on 2010-01-16
Okay now some strange things are happening.For one, some of the small icons in the panel are missing.For example the icon that would be next to the package manager isn't there. When I start When I start Ubuntu up, none of them are there, but then everything will freeze up for a few seconds and they show up.This is a very annoying  problem. Also, when I came to the forums to post this, nothing I typed showed up in the reply box.I tryed to use the text editor, to copy and paste my message but when I typed, all that came up was rectangles.I'm writing all of this in a firefox address bar.This is getting a tad ridiculous.

---

### Post by Pikestaff on 2010-01-16
What sort of graphics card are you using?  You may need to enable the correct drivers.

This is how you would install Nvidia drivers, for example: [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by Rossg on 2010-01-16
It's the GeForce 7600 GS. The driver I'm using is the NVIDIA accelerated graphics driver(version 180).

---

### Post by Rossg on 2010-01-16
Okay, so now I'm starting to think it may have something to do with my HDD.I keep hearing clicking noises that I didn't hear when I ran Windows.I looked this up and I've found it's happened to alot of laptops, but I'm not on a laptop.Anyone else experience this?

---

### Post by Pikestaff on 2010-01-16
> **Rossg said:**
> Okay, so now I'm starting to think it may have something to do with my HDD.I keep hearing clicking noises that I didn't hear when I ran Windows.I looked this up and I've found it's happened to alot of laptops, but I'm not on a laptop.Anyone else experience this?

In the weeks before my hard drive died on my desktop computer, I heard a lot of whirring, grinding noises.  But I know the "death noises" are different from drive to drive.  So, it's possible.  Though, I'm not sure why you would have those issues on Linux and not Windows, unless it's just bad timing.

---

### Post by Rossg on 2010-01-17
I've tried with two different HDDs and both are clicking. As of right now, I've got four HDDS , two with Ubuntu (with both clicking) one with Windows XP Pro (no clicking) and one with no OS on it.I tried installing Ubuntu on the only one without an OS, but I get an error when installing.So unless both HDDs happen to be dying at the same time, I think it's got something to do with Ubuntu.

---

### Post by Rossg on 2010-04-26
Hello again Ubuntu community, I'm back for more help.Actually I'm back for the same help I needed since my last post.My HDD has finally failed (kind of?) and still clicks.What I mean by it 'kind of' failed is that it kind of sort of works sometimes.Sometimes Ubuntu boots, but sometimes it doesn't.Which is not good.Anyway, I'll chalk that up to my HDD and I've since ordered a new one.ANYWAY, I want to make sure this installation isn't going to cause my new HDD to click every so often and my system to hang From what I've been reading this is my heads parking.I don't know what I can do to prevent this.Can anyone explain why it keeps happening?I really would like to keep using Ubuntu but it always seems to be giving me trouble :p

---

### Post by mcoleman44 on 2010-04-26
Im not sure how many times youve installed Ubuntu but if you partition your hardrive to many times it will probably fail. This happened to me and I had to get
a new hard drive. 
Its more common on larger hard drives though. As long as you are careful as to how many times you partition your drive you will be fine. I would advise you to use lucid By the way. Im thinking It will support your hardware better.

---

### Post by mcoleman44 on 2010-04-26
And when I say to many times I dont mean 10 or 15, I mean like 30 and 40.

---

### Post by Rossg on 2010-04-26
I've actually partitioned/formatted the disk a few times because I was having trouble getting ubuntu to dual boot with windows but it was nowhere near 30 or 40 times.Also,I plan on installing Lucid when my new HDD comes in the mail.I just want to make sure it's not going to start clicking and causing more trouble

---

### Post by mcoleman44 on 2010-04-26
I wouldnt worry about it. You should be fine

---

### Post by Rossg on 2010-04-26
Thankyou! But if I need to comeback here for more help with this problem, I'm holding you accountable! ;D
Thanks again.

---

### Post by mcoleman44 on 2010-04-26
Ok haha, sounds like a fair deal.

---

