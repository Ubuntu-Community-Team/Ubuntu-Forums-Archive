---
title: "How do I change a partition mount point from /tmp ?"
date: 2009-08-31
forum: General Help
---

### Post by freeicetime on 2009-08-31
Hi I'm a new ubuntu user and I installed Ubuntu 8.10 as a dual boot with WinXP. I partitioned my 500 GB hard drive into a few partitions. I gave 45 GB to / and 150 GB to /home (which I'm happy about) and mounted a 100GB partition to /tmp without really understanding what /tmp was for. That was kind of dumb. 

Now I would like to change /tmp to be on the same partition as /. (As if I had never given it a separate partition in the first place.) So I will just have one partition for /, one for swap, and one for /home.

I've already tried messing with /etc/fstab, and I've tried using gparted to unmount that 100 GB partition but I don't really know what I'm doing. Changing fstab made my computer unable to start up. (I recovered by booting from a Live CD), and gparted said it couldn't unmount the 100 GB partition.

part of my problem might be I'm not really clear about how the folders work in ubuntu. Do I mount a drive onto a folder or a folder onto a drive? Why don't partitions have letters like in windows (C: E: ...)?

---

### Post by rbc on 2009-08-31
I’ll take a shot at this, in reverse order, kind of. Linux doesn’t use drive letters, like in Windows, because Linux isn’t Windows. Sorry, I know that sounds like a smart a** answer, but it’s not meant to be, it’s simply the answer. As you pointed out, Windows uses C: D: E:, etc, and it is purely Windows jargon. The way GNU/Linux recognizes hard drives and partition actually makes much more sense, at least to me. Hard drives will be seen in two different ways:
hdx  (where x will be some letter) or
sdx

hda= ATA/IDE hard drives 
sda=SATA hard drive

Some linux distros still use hda. A few versions back, Ubuntu (or probably Debian) decided the SATA drivers worked better, so both kinds of drives are seen as SATA hard drives. 

sda is the first hard drive
sdb is the second, etc
sda1 is the first hard drive, first partition
sda2 is the first hard drive, second partition
sdb1 is the second hard drive, first partition
sdb2 is the second hard drive, second partition

OK, now your other problems……What exactly did you do when you altered fstab? This is just a guess, but I have a feeling you were trying to mount 100G partition at the same mount point as /
Here’s two other observations:
Making a separate /home partition was a great idea and may help immensely in this case if you end up having to repartition and re-install. Also, I have always had better luck with the GParted Live CD, as opposed to using GParted off the Ubuntu Live CD

---

### Post by rbc on 2009-08-31
Depending on how and where your partitions are laid out, your solution may be very simple…..backup the data on the 100G partition, delete that partition, re-size the root partition, then make the corrections to fstab. Can you post your fstab file, and a screenshot of what GParted shows?

---

### Post by freeicetime on 2009-08-31
Hi RBC,

Thanks for the reply! I attached a screen shot of gparted and below is the text from my fstab file. (the line wrapping might not work quite right.)

When I wrote my original post I was on another computer and working from memory so I got some of my partition sizes wrong. I hope it's all clear from the image what is what.

When I tried messing around with fstab, all I did was comment (#) the line referring to the tmp folder. I had hoped that if it didn't mount the sda6 partition into /tmp the os would boot up and the temp folder would just exist on the / partition (sda2) and sda6 would be free and unmounted.

Since sda6 was just the tmp folder, do I really need to back up the files? as far as I can tell I don't need anthing that's in there. It's just a temp folder and ubuntu is bound to delete all those files anyway, right? Also, do I need to resize sda2? I think the 42GB for / is enough. 

If I can get this to work, my plan is to reformat the sda6 partition as another NTFS drive for windows.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=db47a127-de48-4c93-be16-2f3e17df4a25 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=488e312f-dd1e-40fb-b90b-24265e70c98f /home           ext3    relatime        0       2
# /dev/sda6
UUID=de7a43f2-41b6-42ad-a6c0-e759096b3075 /tmp            ext3    relatime        0       2
# /dev/sda7
UUID=af56cc8b-a392-4589-bbc2-3a1054187a02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Thanks again!

---

### Post by rbc on 2009-09-01
OK. I was confused about what you wanted to accomplish. I thought you wanted to merge sda6 with sda2, so no, you do not need to resize sda2. To be honest, I have no idea why commenting out that line would be the system unbootable, unless the install process put something on that sda6 partition that is necessary to boot, although this seems unlikely to me. What data is there? And have you tried, either via fstab or manually, mounting that partition somewhere more normal, /mnt/datapartition perhaps? Another thing I just noticed, unless my tired eyes are deceiving me, GParted shows sda5 as swap, and sda7 as /home. These seemed to be reversed in fstab. Am I seeing that wrong?

---

### Post by Bucky Ball on 2009-09-01
Just delete /tmp in Gparted then create a new partition in the free space called /whatever_you_like

Change your /etc/fstab to reflect that change. There should be an entry for /tmp partition in there and just change /tmp to whatever you called your newly created partition. You may need to check you have the right UUID in there. You can do that with:

```
sudo blkid
```... in a terminal.

Delete the mount point /tmp from /media/tmp and replace with one for the new partition and you should be good to go.

```
sudo mkdir /media/whatever_you_called_it
```

---

### Post by freeicetime on 2009-09-01
Hi RBC and Bucky Ball,

Thanks for the advice. 

RBC: you were reading the gparted image correctly. What is strange about swap being on sda5 and /home being on sda7? I haven't tried mounting that drive anywhere else, but I don't know how to do that. In fact, before I can, I would need to unmount it, and when I tried that in gparted, it told me the drive was in use and it couldn't unmount.  I don't know what most of the stuff in the /tmp folder is but I can make a list of what's in it and post it.

Bucky: I haven't tried just deleting the line in fstab referring to the sda6 partition and /tmp, but I did try commenting it out. (by using the # symbol) I thought if the line wasn't there, it would just boot up and /tmp would be on the same partition as /. 

But when I tried commenting that line out,  my system wouldn't boot up properly. I got this weird error saying that as soon as Ubuntu tried starting up my session, it ended in less than 10sec. then it would ask me to log in again, and the same error would happen.

So do you guys think I should try it again? I can back up fstab, and this time delete the line that refers to mounting sda6 in /tmp. Maybe it was a problem with commenting the line out?

---

### Post by Bucky Ball on 2009-09-02
You're not quite getting me.

1/ Delete the partition in Gparted (you need to unmount it first).

2/ Create a partition in the freespace created called 'Donkey' (for instance but whatever you want).

3/ Create a directory in /media (a mount point) called Donkey (sudo mkdir /media/Donkey)

4/ Open /etc/fstab and the line referring to sda6, /tmp, CHANGE where it says /tmp to /Donkey, your new mount point. (if you are using it, you need to check the UUID is correct for you new parition with 'sudo blkid' in a terminal).

Reboot and report back. ;-)

If you comment out /tmp you are going get problems, as you have found. You have a partition with no reference in fstab then and the system can't deal with it.

---

### Post by jocko on 2009-09-02
> **Bucky Ball said:**
> If you comment out /tmp you are going get problems, as you have found. You have a partition with no reference in fstab then and the system can't deal with it.
fstab normally doesn't have an entry for /tmp, so /tmp is normally just a folder on the / filesystem. 
It shouldn't be a problem to comment out the /tmp line, as long as the /tmp **folder** is still there and has the correct permissions.
And there is no problem whatsoever booting a system with a partition which isn't mentioned in fstab. It will just not be automounted during boot. (But the other way around, having a line in fstab for mounting a partition that doesn't exist, or mounting a partition to a non-existing mount point, will cause boot to fail).

---

### Post by Bucky Ball on 2009-09-02
jocko, why is it then that when OP comments out the /tmp entry in fstab, his machine stalls at boot with an error message, he removes and all is good? :-k

---

### Post by jocko on 2009-09-02
> **Bucky Ball said:**
> jocko, why is it then that when OP comments out the /tmp entry in fstab, his machine stalls at boot with an error message, he removes and all is good? :-k
Beats me. But I don't have any line for /tmp in my fstab, have never had one, and my computer boots just fine.

Perhaps the /tmp folder that was previously just used as a mount point for the partition has the wrong permissions, so it can't work as a real /tmp?

---

### Post by rbc on 2009-09-02
freeicetime,
you are clearly getting much better advice from Bucky Ball and jocko, so I will bow out, but to answer your question, there is nothing wrong with swap being on sda5 and /home being on sda7. That is exactly what I would expect, however, your fstab clearly has these partitions the other way around. 

# /dev/[COLOR="Red"]sda5[/COLOR]
UUID=488e312f-dd1e-40fb-b90b-24265e70c98f [COLOR="red"]/home [/COLOR]ext3 relatime 0 2
# /dev/sda6
UUID=de7a43f2-41b6-42ad-a6c0-e759096b3075 /tmp ext3 relatime 0 2
# /dev/[COLOR="red"]sda7[/COLOR]
UUID=af56cc8b-a392-4589-bbc2-3a1054187a02 none [COLOR="red"]swap[/COLOR] sw 0 0

---

### Post by bear24rw on 2009-09-02
if you got some RAM to spare you should just through /tmp on a ramdisk.. add this line to /etc/fstab
```
tmpfs		/tmp		tmpfs	defaults,noatime,mode=1777	0	0
```

---

### Post by freeicetime on 2009-09-03
Wow, thanks for all the advice everyone! This is a lot to go thru for me and I'm just about to head out of town for an extended labour-day weekend. I won't have a chance to try out your suggestions until I get back but I'll post my results as soon as I have some to report.

talk to you next week.

Thanks again!
Freeicetime

---

### Post by Bucky Ball on 2009-09-03
Have a good one! rbc's post #11 looks promising.

---

### Post by egalvan on 2009-09-03
type this in a terminal, and post the output

```
sudo blkid
```

this will give us some more drive info.

---

### Post by BartVS on 2012-01-27
I ran into the same problem as freeicetime, a program requiring more tmp space than I had on my tmp partition. (Using Ubuntu 10.04, 1GB tmp partition with 3% usage before I run the program)

Simply commenting the /tmp mount line in /etc/fstab resulted in 
** /usr/lib/libgconf2-4/gconf-sanity-check-2 exit code 256**
when X was trying to start.

Turns out permissions on /tmp changed from
[FONT=Courier New] drwxrwxrwt /tmp[/FONT]   (when my tmp partition was mounted)
to
[FONT=Courier New] drwxr-xr-w /tmp[/FONT]  (when no longer mounting anything on /tmp)

I fixed this doing
```
[FONT=Courier New]sudo chmod 777 /tmp[/FONT]
```[FONT=Courier New]
[/FONT]and rebooting once more

/tmp is now no longer a seperate partition, but part of my / partition

Hope it helps anyone else running into this.

---

