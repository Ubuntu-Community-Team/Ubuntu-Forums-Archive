---
title: "New laptop hdd - how to clone?"
date: 2010-01-19
forum: General Help
---

### Post by Roasted on 2010-01-19
I'm familiar with cloning, but my cloning needs this time are a bit different than what I'm used to.

When I clone before, I use FOG for mass deployment or Clonezilla LiveCD for 1 to 1 backups. However, both pieces of software grab the used bytes, zip them into a compressed package, and then they're ready for re-deployment.

I have a laptop with a 160gb hdd. I now have a new 250gb hdd on my desk.

On my laptop I have XP Pro SP3 and several split up Ubuntu 9.10 64 bit partitions.

What do I need to do to copy the entire contents as is to the 250gb drive, and thereby put the 250gb drive inside my laptop, and have it boot just fine?

I can deal with partition resizing later, that's not an issue. I just need to get the as-is contents of the 160 on the 250.

What you say, dudes?

---

### Post by tom4everitt on 2010-01-19
I think you should be able to use the good old dd command. 
[http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)

If you can somehow connect and mount your new hard drive to your current system, you can simply run:

dd if=/dev/sda of=/dev/sdb

presuming your old drive is mounted as sda and the new one sdb. Be terribly careful with this command though, it will erase your entire hard drive without asking if you do wrong :) I've done this myself, its very annoying ;)


EDIT:
The reason this should work is that all information about the partition layout etc is stored at the beginning of the hard drive, so therefore it won't matter that the drive you want to move stuff to is bigger. I haven't tried this myself, but I've heard about people who've done it.

---

### Post by Dragonbite on 2010-01-19
If you have a network server with enough space on the hard disk or a USB external drive you can use Clonezilla to turn the laptop's existing partition/drive into an image, on the extra hard drive, switch hard drives, then use Clonezilla to move the partition image on the external drive onto the new laptop hard drive.

---

### Post by Roasted on 2010-01-20
Yeah - Clonezilla is a good idea. I use it a lot. I don't know why I didn't think of it, but we have a physical DD cloner at work, so I just used that and targeted the 160 as master and new drive as client. Then used GParted to expand the partition accordingly.

We're rockin and rollin now. Thanks guys.

---

### Post by bpalone on 2010-01-20
You can use GParted live CD and copy your partitions over to the  new drive. You can resize them with it as well.  The worst that you will have to do is re-install Grub.  I have used this method several times.

---

### Post by Roasted on 2010-01-20
> **bpalone said:**
> You can use GParted live CD and copy your partitions over to the  new drive. You can resize them with it as well.  The worst that you will have to do is re-install Grub.  I have used this method several times.

Didn't have to reinstall grub. Everything worked fine.

The only thing is, the unallocated partition was a primary. I was kind of confused on how to add it to /home, because it wouldn't let me add it. So I had to add the unallocated space to the extended linux partition set, THEN expand /home.

Took a few mins of confusion and 1 or 2 minutes in the Ubuntu IRC to ask questions, but they helped me out and we're good to go. It's nice having extra space. :)

---

### Post by bpalone on 2010-01-20
Glad that it worked well.  I mentioned Grub re-installation because I have had to do it a few times.  Most of the time all is OK after the move.

Enjoy the room.  Just don't go on a downloading binge, or you will back where you were. ;)

---

### Post by Roasted on 2010-01-20
> **bpalone said:**
> Glad that it worked well.  I mentioned Grub re-installation because I have had to do it a few times.  Most of the time all is OK after the move.

Enjoy the room.  Just don't go on a downloading binge, or you will back where you were. ;)

In my case, it's an imaging binge. It's my work laptop, and I use FOG on Ubuntu to image Windows workstations. I hardly even have 50 songs on this laptop... everything else is work stuff. 

7 schools, many labs in each, several different configurations in each, elementary, middle, high, cadd lab, business lab, office lab, typing lab, graphics lab, etc. Before you know it your hard drive is full of zipped image files.

---

