---
title: "Cannot mount newly created LUKS filesystem"
date: 2011-06-24
forum: General Help
---

### Post by compuslave on 2011-06-24
Hi guys, I just created a LUKS filesystem following [these]("http://lifehacker.com/344935/set-up-encrypted-partitions-in-ubuntu") instructions. Everything seemed okay at first. It mounted with no problem and I moved some files there. I then unmounted it and remounted it to see if I would need to use a special command. It mounted right away and even allowed access to normal users. So, I rebooted to see if anything would change. Before I go on I should say that my partitioning scheme is weird. Not knowing any better I 'upgraded' to 11.04 when my update manager told me a new version was out. This didn't go well and I had to do a fresh install to put 10.10 back on my machine. After this the way it partitions the drive has been weird. What I had was /dev/sda1 which has my installation on it including /home. But, where it gets weird is /dev/sda2 would not manually mount. Looking at the disk in gparted it showed /dev/sda2 THEN under that, as if they were sub partitions or something, I had sda6 and sda7. I had been using 6 and 7 for various things and they mounted fine, so I decided to encrypt 7. After reboot I only have sda1. Everything else shows up as unallocated and ever way I try to mount I get device does not exist. 

I will be happy to provide any information needed. Please tell me my data is still there. I only did the procedure for sda7 but 6 has been affected as well. There is no longer a sda2 the way there was before. This always bothered me anyway since I wanted sda2 for my /home but it wanted to call it sda6 and put it under sda2 like I said, I could never fix that, now this.

---

### Post by Herman on 2011-06-25
Hello compuslave,
That's a nice tutorial, thanks for the link! After reading your post I was curious to try to find out what might have happened and I thought it would be a fun challenge to see if I can find a solution to your problem.

I decided to simulate your situation in a spare computer with a fresh installation of Ubuntu Natty Narwhal in it. I ran through each of the steps in the tutorial you linked to, and I set up an encrypted partition too, almost the same as yours except mine is /dev/sdb6, so it's in a logical partition just like yours. At first, just like you explained, I was able to mount it without any problems

Then after a reboot - nothing. I got error messages like 'unable to mount 10GB encrypted. One or more block devices are holding /dev/sdb6', and 'no such device as /dev/mapper/sdb6' and '/dev/sdb6 is not a proper LUKS volume (or something to that effect).

Unlike your description though, my extended partition, (the box the other partitions are in like your /dev/sda2), is fine. Mine's /dev/sdb2. I could see both my encypted partition and my swap area in GParted okay, except of course GParted didn't recognize the file system in my encrypted partition and that is to be expected.

Remembering that I normally run 'sudo modprobe dm-crypt' whenever I'm in a new Ubuntu installation and I'm about to start working on LUKS encrypted file systems, I decided to run that and see if it would help. At first it didn't seem to do anything and I even rebooted and still couldn't mount the encrypted file system.

In the end I repeated the entire procedure all over again from the start and created a new encrypted file system. This time for some reason it worked! I have a nice spare partition with an encrypted file system in it now it's persistent after a reboot.

I'm not sure if running 'sudo modprobe dm-crypt ' has anything to do with my success on the second try, but I suspect it might have. I will need to test again in another clean install to find out for sure. I noticed in the comments under the tutorial a person called 'jaba' posted 'modprobe dm-mod ;\
cp /etc/modules /etc/modules.OLD &&\
echo dm-mod >> /etc/modules'

Try running 'sudo modprobe dm-crypt' it won't do any harm and might help you.
```
sudo modprobe dm-crypt

```I wonder if that command is required before we can make valid LUKS encrypted partitions now? That tutorial is a few years old, and things may have changed between then and now.
For me it was okay to repeat the procedure in the tutorial because I didn't have any data yet in the encrypted partition. The problem for you with repeating the procedure is that if you do you'll lose your data because the partition will need to be reformatted. 

The other factor that's unique about your current predicament is the fact that your extended partition isn't showing. I'm just wondering if you might have accidentally typed or copied and pasted a command from that tutorial 'as is', (without changing the '2' on the end of '/dev/sda2' to a '7'by accident? If that's a possibility, (we're all human and we all make mistakes), then it could explain why your partitions seem to have disappeared.
Normally, missing partitions can be written back to the partition table by scanning with TestDisk for the start points and having TestDisk write you a new partition table.
If your missing data is valuable then TestDisk might be worth a try. There's a chance you might be able to regain access to at least some of your data with TestDisk. I'm just hoping TestDisk will still be able to recognize your partition start points.
```
sudo apt-get install testdisk
```If you have never used TestDisk before you'll need to find their website where there are some excellent illustrated tutorials.
I hope I've been of some help and I hope you have good luck regaining access to your data. Your data will still be there I'm sure, but regaining access to it might be easy or tricky, it's hard to tell at this point in time. I would need to spend a lot more time re-installing and running more experiments to learn more but for now it's night-time here and almost time for a sleep.

EDIT: In the light of more that I have learned about this subject since this reply to your post, I  don't think you should do anything yet.
It would be a good idea to read about TestDisk but not to disturb your disk or any of your partitions yet.
It would be a good idea to clone the entire disk to another same size or larger disk if you can get one, and probably work on the copy of your hard disk and no the original.

---

### Post by Herman on 2011-06-25
This morning I tried another idea.

I deleted the partitions I made yesterday and created new ones and then ran through the same commands again from the tutorial. The difference was this time I deliberately typed '/dev/sdb2' instead of '/dev/sdb6' to see what would happen when I typed each command wrong and tried to alter my extended partition rather than the logical partition within.
At every instance, I was greeted with error messages and that's what should happen, and so instead I typed the correct command and proceeded to the next command.
I deliberately made every mistake I could first before typing each command correctly.

After mounting the file system and copying in some test data, I rebooted.
... and, once again I'm not able to mount the encrypted partition to access my test data.

Even more surprisingly, (and this might be good news), my entire hard disk is coming up as unallocated space in GParted! Wow!

I was still able to boot okay, (amazingly), and blkid and fdisk still show most (but not all) of my partitions. For /dev/sdb all I can see in fdisk is the two primaries I had plus the extended.

Whatever I did has really corrupted the extended partition's [extended boot record]("http://en.wikipedia.org/wiki/Extended_boot_record") I'm guessing.

Now to see if I can recover my test data somehow, I'll try with TestDisk first and see what I can do.

If I can do it then you can too! :)

---

### Post by Herman on 2011-06-26
Thanks for your patience, I'm sorry to keep you waiting but I have zeroed the test hard disk and I want to start over from the beginning again. This time I will be closely watching which bytes are changed in the MBR, EBR and PBR at each step when the commands are typed correctly and again when they're type incorrectly to learn details about what might have gone wrong. When I have recorded the results from those tests I'll be in a better position to help you. 

If you can post the output of 'sudo fdisk -lu' and 'sudo blkid' they might help too.
Thanks.
```
sudo fdisk -lu
``````
sudo blkid
```

EDIT:
and 'grep -A 20 hashalot .bash_history' too please,
```
grep -A 20 hashalot .bash_history
```

---

