---
title: "mounting hard disk from a live-cd"
date: 2006-06-28
forum: General Help
---

### Post by ozdevelop on 2006-06-28
If my kubuntu 6.06 system ever crashes - how would I mount the hard disk from a live-CD to recover my home directory?

---

### Post by digimars on 2006-06-28
Unless your drive gets fried, it should automagically pick it up when you boot from the liveCD and display it on the Desktop

---

### Post by kzutter on 2006-06-28
If it crashes then it might just be a moot point anyway:???: 

If it is mountable, the live cd should mount it for you automatically.

IF not, you will need to know the device and partition it is on.
An easy way to find this out if you do not know, is to look at /etc/fstab
/etc/fstab is a list of the devices the system knows about.

TIP: Backups are like GOLD when you need them!

---

### Post by ozdevelop on 2006-06-28
Thanks for the lightning-quick reply digimars!

Sorry to sound like a noob - but before, on ubuntu breezy - I had an issue where I couldnt boot into a GUI - so I put in a live-cd of knoppix - but it had no icons or entries via konqueror for any hard-disks - just the CD drive it booted from. So I had to re-install the OS again - and lost my data (which I should have backed-up but ....).

So - is what you are saying is - if I couldnt get into kubuntu KDE - if I booted from a kubuntu live-CD, I should be able to see my hda, and use k3b or similar to back-up any data I needed to save??

---

### Post by digimars on 2006-06-28
Should, yes.  But like kzutter was saying, if not check your /etc/fstab file for your particlular disk/partition that your looking for and mount that.  There is also [this]("http://www.partimage.org/Main_Page") that could help you with backing up your partitions.

I just did
```

sudo apt-get install partimage

```
and you will get the latest version.  Then just run 
```

sudo partimage

```
to use it.

---

### Post by kzutter on 2006-06-28
What I was doing was responding to your question.

If you want my advice, that's different.

My advise is to backup your important data and DO NOT rely on live-cd's. They are very handy, but handy does not cut it when your data is hosed.

---

### Post by aysiu on 2006-06-28
Just to clarify a bit...

Knoppix should automatically place all partitions and drives on the desktop. When you click on the partition, it should automount.

Now, that said, I've never known Ubuntu, Kubuntu, or Xubuntu live CDs to either have partitions automatically appear on the desktop or automatically mount with the correct permissions.

Let's assume, for the sake of this example, that your Ubuntu partition is /dev/hda1. You would know, of course, what it really is. To see your partition table, type ```
sudo fdisk -l
``` To mount it, create a mount point: ```
sudo mkdir /recovery
``` Then mount it ```
sudo mount -t ext3 /dev/hda1 /recovery
``` Then open a browser as root ```
gksudo nautilus
``` and go to the /recovery directory to get your files out. If you're using Xubuntu, do ```
gksudo thunar
``` or if you're using Kubuntu do ```
kdesu konqueror
``` As long as you're trying to recover your /home directory, consider making a separate /home partition: [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by ozdevelop on 2006-06-28
Thanks everyone for the tips and advice!

I take the (good) advice that it is best to have current backups instead of having to deal with an issue after the horse has bolted, so to speak.

As a programmer at work, I always checkin my code mods into CVS religiously - so I know I should follow the same practice at home :oops: 

Anyway - just lovin' Kubuntu 6.06!!

---

### Post by aysiu on 2006-06-28
Here's a PartImage tutorial that's Ubuntu-specific, in case you're curious:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

