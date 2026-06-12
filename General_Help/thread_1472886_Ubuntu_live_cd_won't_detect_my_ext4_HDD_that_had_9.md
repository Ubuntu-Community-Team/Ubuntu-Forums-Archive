---
title: "Ubuntu live cd won't detect my ext4 HDD that had 9.10"
date: 2010-05-04
forum: General Help
---

### Post by longanduselessname on 2010-05-04
I am trying to do a fresh install on the HDD that had 9.10, a 80GB ext4 drive. All that shows up is my other HDD, a 160 GB ext3 drive. 

Why is this happening? "ls /dev/|grep sd" only returns sda and sda1. My 80GB drive has a few partitions, one for swap for instance. 

PLEASE HELP!

Edit for clarification:
2 harddrives in 9.10: 


80 GB HDD /dev/sda
1 ext4 partition that has ubuntu installed (/dev/sda1)
1 extended partition (/dev/sda2) for swap (/dev/sda5)

160 GB HDD /dev/sdb
1 ext3 partition /dev/sdb1

Only the 160GB HDD is detected when using the liveCD (as /dev/sda and /dev/sda1). I can mount it just fine, but my 80GB HDD is not detected. After ejecting, I can boot my 80GB HDD just fine...

---

### Post by longanduselessname on 2010-05-04
I am using a 64bit LiveCD. Just to reiterate, I boot up the CD just  fine, choose either "Try it out" or  "Install Ubuntu", and for  partitioning only my 160 HDD is listed. 

If I eject the cd and boot up normally, my 80 GB boots up 9.10 just  fine. 

What is going on???

---

### Post by garvinrick4 on 2010-05-04
Boot up CD in try Ubuntu only mode (Live CD). Go to System to Administration to gparted.
Open gparted in first drop down menu in upper left that says Gparted there will be one that
says devices, what ever you have connected to your system your devices will show up there. You can see the partitions, the labels the format. And you can change anything you like in gparted. Stay focused when you screw around with your drives, read up on gparted is a good thing to do.

---

### Post by blueridgedog on 2010-05-04
While booted on the LiveCD, what is the output of:

```
sudo fdisk -l
```

?

---

### Post by longanduselessname on 2010-05-05
> **garvinrick4 said:**
> Boot up CD in try Ubuntu only mode (Live CD). Go to System to Administration to gparted.
Open gparted in first drop down menu in upper left that says Gparted there will be one that
says devices, what ever you have connected to your system your devices will show up there. You can see the partitions, the labels the format. And you can change anything you like in gparted. Stay focused when you screw around with your drives, read up on gparted is a good thing to do.


I tried this, and again, the only harddrive device detected is my 160GB HDD which has one big ext3 partition. This isn't a surprise, since AFAI(can guess) the ubiquity installer program uses gparted for partitioning. 

So only one device detected no matter how many times I refresh, just my 160 GB HDD with its ext3 partition.

---

### Post by longanduselessname on 2010-05-05
> **blueridgedog said:**
> While booted on the LiveCD, what is the output of:

```
sudo fdisk -l
```?

I am not sitting in front of the computer now, but I did that and can tell you it only mounted sda1 on /media. The rest were loopback devices or tmpfs devices to make ubuntu do its thing (or w/e). 

Really, "ls /dev/|grep sd" gives the information we need. Again, the only output from that command is "sda" and "sda1", which is my 160GB HDD with its 1 big ext3 partition.

Once I eject the livecd, I can boot up from my main 80GB HDD  ext4 ubuntu partition just fine....

---

### Post by blueridgedog on 2010-05-05
Just for curiosity then, can you post the output of the command?  The only thing I can think of at the moment is the hard drive controller isn't being recognized, but I would rather start with the basics.

---

### Post by longanduselessname on 2010-05-06
I realize now I thought you typed "df -l", not "fdisk -l". I haven't tried "fdisk"... don't know the difference but i'll find out soon enough.

Sorry for not updating, I won't be able to try "fdisk -l" again till tomorrow. FINALS WEEK WOOHOO :/

I wasn't going to mention this, because I wasn't able to double confirm it, but one time I booted the LiveCD X or ubiquity didn't start. Instead it went straight to bash prompt (or maybe I was on the 1st tty and not the 7th). 

I did the ol' "ls /dev/ |grep sd" and both HDDs came up. I had problems starting X (prob because it was already started and I was on the 1st TTY) so I rebooted. I tried it again and it didn't work. 

By tty I mean the first terminal session, or what you get when you press "alt+ctrl 1". 

TBH, I don't know what tty stands for (teletype something?) or the difference between tty and pts/X. I am a noob after all.

---

### Post by longanduselessname on 2010-05-06
> **blueridgedog said:**
> Just for curiosity then, can you post the output of the command?  The only thing I can think of at the moment is the hard drive controller isn't being recognized, but I would rather start with the basics.


I swear unto all of you, on Wednesday I tried at least four separate times, either between running the ubiquity program or the LiveCD itself, and I couldn't get my ext4 drive to be detected. 

Some strange symptoms, as compared to a coworkers installation, but the booting of the LiveCD to ubiquity menu took a LONG time on my computer. 

And yet again, today, I toss in the LiveCD to try out fdisk, it takes a LONGGG time to boot up... my hopes begin to be dashed. 

But 'lo and behold, my ext4 HDD device is detected. I am able to use ubiquity installer to format the partition and install 10.04 for a clean install.

I am a bit spooked out. I have NO idea why the HDD wasn't detected before. Could it be dying? <.< >.>

I don't think I should mark this thread as solved since the problem just sort of didn't happen. I guess I can try again...

Freaky.

---

### Post by longanduselessname on 2010-05-06
> **blueridgedog said:**
> Just for curiosity then, can you post the output of the command?  The only thing I can think of at the moment is the hard drive controller isn't being recognized, but I would rather start with the basics.


I swear unto all of you, on Wednesday I tried at least four separate times, either between running the ubiquity program or the LiveCD itself, and I couldn't get my ext4 drive to be detected. 

Some strange symptoms, as compared to a coworkers installation, but the booting of the LiveCD to ubiquity menu took a LONG time on my computer. 

And yet again, today, I toss in the LiveCD to try out fdisk, it takes a LONGGG time to boot up... my hopes begin to be dashed. 

But 'lo and behold, my ext4 HDD device is detected. I am able to use ubiquity installer to format the partition and install 10.04 for a clean install.

I am a bit spooked out. I have NO idea why the HDD wasn't detected before. Could it be dying? <.< >.>

I don't think I should mark this thread as solved since the problem just sort of didn't happen. I guess I can try again...

Freaky.

---

### Post by blueridgedog on 2010-05-08
Hmm...no telling, but many things can be off in such a new release. Or, the drive may take a long time time to come up and be recognized...just guessing.

---

