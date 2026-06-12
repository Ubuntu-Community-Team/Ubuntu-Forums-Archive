---
title: "HDD with defective sectors"
date: 2010-05-07
forum: General Help
---

### Post by ^_Pepe_^ on 2010-05-07
Hi all,

Let me introduce my problem

I have 5 disks on my Ubuntu box.

One of them, started failing with several defective sectors, detected by palimpset. Of course, following Murphy's law, this is (was) the OS disk.

I've try a LiveCD start, and several commands.

[LIST]
[*] e2fsck -pctv /dev/sdxy, where x is the number of device, and y, the letter of each partition. Three in total (1st OS, 2nd virtual machines, 3rd backup)
[*] badblocks with several options.
[*] fsck (same as e2fsck, as I've read)
[/LIST]

But, no luck. Nothing detected. Firstly, the backup partition sudenly got "full" (no space), but with no reason.

And yesterday...the 10.04 OS...crashed :(

Ok! Really bad luck.

I've reinstalled 10.04 in a new partition on other disk, and everything is working now, but I don't want to get rid of the bad disk. 

Now, my bad disk is attached, not mounted, and ready to be fixed. I know there's nothing similar to low-level format in new disks, but I've read something about 

```
dd if=/dev/zero of=/dev/sdx count=1

```

Any additional ideas? I've tried Gparted's fix tool (fsck, I guess) but nothing detected...

Any help would be appreciated.

Cheers,
Pepe

---

### Post by marbertone on 2010-05-07
Hi,
perhaps mine won't be a technical answer, but it's based on my experience and worked for me. If you take a look around, you will see that Karmic's Palimpsest used to warn about failing hard disks ("disk has many bad sectors") even if it wasn't true. I just ignored those messages after having brought my laptop to technical assistance point and having paid 35 euros :D
Hope it could be useful, 
Mario Alberto ;)

---

### Post by sbergman on 2010-05-07
An idea: Use dd to copy an image of the disk somewhere and then use foremost to scan through the image ... you might be able to rescue some data that way.

---

### Post by dino99 on 2010-05-07
sudo apt-get install -f

sudo shutdown -F -r now (fsck on next boot)

booting with [http://partedmagic.com/](http://partedmagic.com/) will give you better chances than palimpest

may try [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by ^_Pepe_^ on 2010-05-07
Hi all,

Thanks for your comments.

Information in bad-disk is not relevant for me, so I only want to mark this bad-sectors as "bad" to avoid more strange behaviour and to use the disk, at least as a temporary file system, for torrent, Jdownloader, and so...

Actually, I don't need to force fsck's and LiveCD's because this HDD is not bootable and there's no bootable OS .

Now, I'm running a e2fsck -fcc as explained here

[http://brainstorm.ubuntu.com/idea/6972/](http://brainstorm.ubuntu.com/idea/6972/)

to see what happens.

Thanks to all again.

---

### Post by ^_Pepe_^ on 2010-05-14
Hi all,

No luck at all.

I've tried partedmagic, but no additional information added to e2fsck one.

I finally deleted the first partition (the OS one), and I'm keeping the 2nd (virtual machines) and 3rd (backup) ones.

I've no more crashes and "sudden full disks" anymore, but palimpset still warning about bad sectors.

---

### Post by psusi on 2010-05-14
Badblocks is obsolete.  Based on your screen shot, the disk found one bad sector and has already reallocated it to correct the problem.  Look at attributes 197 and 198 to see if there are any more.  Also have palimeset run the long smart test to scan the disk.  If no more turn up then the disk should be fine, but you should make a habbit of running the long smart test every week or so to make sure no more bad sectors have turned up.

---

### Post by sedawk on 2010-05-14
You can try to use command line tool smartctl to
get some diagnostics of your hard disks.

As was said above, modern disks relocate data on
bad blocks themselves - so when you try to
access bad block 4578 they might relocate you
automatically to another working block.

Actually I do not recommend to use that disk anymore,
especially if it was fine before and the number of
bad blocks will start growing.
Make a backup if needed - as you said it is the
OS disk which I think is the best thing that can happen.
A data disk with no backup and important data would
be the worst case. It is easy to reinstall the OS but it
is expensive or impossible to create some photos again.
(On the other hand some people have /home on the same
 disk as the OS and /home is not OS, it is data!).

---

