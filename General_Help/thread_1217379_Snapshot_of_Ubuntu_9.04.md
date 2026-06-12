---
title: "Snapshot of Ubuntu 9.04"
date: 2009-07-19
forum: General Help
---

### Post by emeraldgirl08 on 2009-07-19
I've been trying to figure out how to save the important data in Ubuntu for transferring to an external drive. I'd like to save the custom settings I have, the Apps I've installed, and the Updates so I don't have to start from scratch! 

I'll be transferring the contents of my Jaunty HDD (only has 3.1 gb in use) to a temporary partition on an external drive. The HDD that Jaunty currently resides in is going to be going through some changes and I need some disk space! I've already resized the Jaunty partition from 16 gb to 8gb with Gparted. 

It works fine as I'm using it now :D

The drive is only 40 gb and is going to be undergoing a Killdisk. After my projects I want to reinstall Jaunty back to the drive with Gparted. 

Is there an easier way of doing this???

---

### Post by ugm6hr on 2009-07-19
Never actually done this, but I have a couple of ideas:

1. Use a partition backup program to duplicate the entire partition and then restore back afterwards.  Something like PartImage would probably work.

2.  Follow:
[http://ubuntuforums.org/showpost.php?p=1521615&postcount=1](http://ubuntuforums.org/showpost.php?p=1521615&postcount=1)

Then backup your /home (files and settings) and /var/cache/apt/archives (all .debs for updates etc).  If you have any complied applications, this won't pick them up.   Additionally, you might want to keep a copy of your /etc/apt/sources.list if you have any additional repos.  Or even just backup /etc/apt/ which should save everything necessary.


I use option 2 when I purge my computer for an upgrade (except I don't bother with /var/cache/apt/archives etc).

---

### Post by emeraldgirl08 on 2009-07-19
Cool beans :D

I'll read up on the partimage. I have a couple of things on ISO from previous escapades with cloning, parting, etc. I guess partimage will be another add to my tools!

Thanks.

---

### Post by emeraldgirl08 on 2009-07-19
Okay. I found out that I have PartImage on my a SystemRescue CD I created from ISO not that long ago.

My USB drive external Hard Drives are not recognized. This is strange because when I used my Gparted CD earlier both were recognized by the LiveCD (I think that's the right word). The only thing that is recognized is the Win XP pro HDD that is inside the laptop. 

Any suggestions??? Do I need to download the PartImage by itself and run it??? I'll try that and come back with my results- in the meantime I'd like to hear from anyone who could assist.

Thanks.

---

### Post by emeraldgirl08 on 2009-07-19
I guess what I want to say is how do I get my USB drives to show up in PartImage???

One of the external drives is a 3.5 HDD so I can't fit that into my Laptop. The other is a 2.5 and that is the one with the Linux partition I want to part over to the 3.5 for after I killdisk the old drive.

---

### Post by emeraldgirl08 on 2009-07-20
Omg. I am SO seriously going to throw my lappy through the window (or er....Windows ;))

I've entered and must have rebooted PartImage so many times already! I've read some threads and have tried various things to get my Jaunty partition to go to a target partition. 

It won't go.

The instructions are very vague and probably require wearing tin foil on your head just to get it to work! Oh and a lot of the threads I've looked at are from three years ago. I think that a lot of things may have changed since then!

Is there an easier way of getting my external USB drive to show in PartImage??? The only thing I see is my primary drive.

---

### Post by eriqjaffe on 2009-07-20
You can copy or move a partition with gparted, actually.

[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)

---

### Post by emeraldgirl08 on 2009-07-20
> **eriqjaffe said:**
> You can copy or move a partition with gparted, actually.

[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)

Hmmmm... well. The thing I was concerned about was diskspace. I have partitioned 4.7 gb for this image. After reading about how PartImage could create a smaller image through zip I really wanted to do it this way. I am a little vague on Gparted. I had used it to clone a partition before but that was the extent of it. I just didn't want the free-space but only the actual Jaunty copied over to my external drive. I also want it to be a bootable copy.

So if I copy and paste this over to my external drive. I could copy and paste it back to my newly reorganized primary drive and boot from it again?

---

### Post by ugm6hr on 2009-07-20
You can use dd to copy partitions directly, but the total partition size will remain the same (i.e. no compression at all).

---

### Post by emeraldgirl08 on 2009-07-20
I followed eriq's advice and used Gparted. I didn't know you could change the size of your copy. I thought the copy would stay one size that included the freespace. The freespace is something I didn't want to copy over to the 3.5 ext. drive.

lol. This was an extremely frustrating experience! 

So I had around 7 gbs of linux (3.1 gbs was the actual linux and the rest was free-space) and copied and pasted it to the new ext.3 partition I had created for it. This partition was only 4.5 gbs. Once I pasted it I resized it (glad there was a GUI at this point- another set of codes would have done me over!) to 4.5.

The Gparted did it's thing. First it copied all 7.4 (my estimate) gbs. and *then* shrunk the copy to 4.5gb.

Now is there anyway to check this partition? I know Gparted ran through a disk check and found no errors. Before I Killdisk my 2.5 primary I would like to know that the partition is okay to Gpart back over for use. And can someone enlighten me on using the flags in Gparted?

---

