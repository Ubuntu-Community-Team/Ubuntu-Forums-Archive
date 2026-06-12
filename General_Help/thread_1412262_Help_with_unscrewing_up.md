---
title: "Help with unscrewing up"
date: 2010-02-21
forum: General Help
---

### Post by DeanZF on 2010-02-21
Long story short, I've just had my hard drive totally wiped and have reinstalled my 9.04 from my 9.04 CD. Glad I had it.

Now trying to get things updated. Ran Update Manager, which of course came back with a boatload of stuff to download. Sigh. Click the Install button. Message comes back saying "not enough disk space on disk '/'." It then tells me to empty trash and run sudo apt-get clean. Yeah, okay, did both of those, tried again, no help. How do I get the disk '/' (a partition??) to a respectable size and what might that size be??

Major pain of a screw up. Can't update NUTHIN and EVERYTHING is a mess. Glad I at least have my documents. No settings, but documents. Sigh.

Thanks in advance, folks.

---

### Post by Darkish Dave on 2010-02-21
How much free space do you have on "/"?

---

### Post by DeanZF on 2010-02-21
I have no idea and am not sure how to check!

---

### Post by Darkish Dave on 2010-02-21
> **DeanZF said:**
> I have no idea and am not sure how to check!

Open up a Terminal and Use this command

```
df -h
```

Terminal can be found under Applications > Accessories.

You should get something like

```
Filesystem            Size  Used **Avail** Use% **Mounted on**
/dev/sdb1              37G   23G   **13G**  66% **/**
udev                  1.8G  344K  1.8G   1% /dev
none                  1.8G  804K  1.8G   1% /dev/shm
none                  1.8G  300K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw
/dev/sda3             137G   48G   89G  36% /media/sda3

```

I highlighted what you should be looking for.

---

### Post by DeanZF on 2010-02-21
response was:

2.3G  2.2G   68M  97% /

---

### Post by DeanZF on 2010-02-21
to df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   62M  98% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  104K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  164K  1.8G   1% /dev
tmpfs                 1.8G   92K  1.8G   1% /dev/shm
lrm                   1.8G  2.4M  1.8G   1% /lib/modules/2.6.28-11-generic/volatile

---

### Post by DeanZF on 2010-02-21
[FONT=Courier New]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   62M  98% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  104K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  164K  1.8G   1% /dev
tmpfs                 1.8G   92K  1.8G   1% /dev/shm
lrm                   1.8G  2.4M  1.8G   1% /lib/modules/2.6.28-11-generic/volatile
[/FONT]

---

### Post by Darkish Dave on 2010-02-21
> **DeanZF said:**
> [FONT=Courier New]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   **62M  98% /**
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  104K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  164K  1.8G   1% /dev
tmpfs                 1.8G   92K  1.8G   1% /dev/shm
lrm                   1.8G  2.4M  1.8G   1% /lib/modules/2.6.28-11-generic/volatile
[/FONT]

There is your problem.

You only have 62MB of hard drive space available. 

Your running Ubuntu on a small partition.

Ubuntu requires at least 4GB of Hard Drive space. Your running Ubuntu of a 2.3GB hard drive.

---

### Post by DeanZF on 2010-02-21
How do I expand the partition? The drive is not small. I've forgotten, but I want to say 250 gigs? I can't remember enough about Ubuntu to get the real number.

Yes, 250 gig hard drive confirmed.

---

### Post by DeanZF on 2010-02-21
Have done more research here and found info about resizing partitions with GParted. Tried to download that and I don't have enough room to save it!

what next can I re-designate a bigger place for the download? If so, how?

---

### Post by 3rdalbum on 2010-02-21
Gparted can only sometimes allow you to resize the partition - it depends on whether it's inside an "Extended" partition container or not. In any case it can't touch a partition that's currently in use - just like how your mechanic doesn't work on your brakes while driving the car down the road.

From the Ubuntu CD (the live environment), you can attempt to use Gparted to resize the Ubuntu partition. Gparted comes on the live CD. If you can't resize it, then use Gparted to get rid of the Ubuntu partition, and then downsize the Windows partition. Finally, install Ubuntu into the resulting free space.

9.04's installer will happily default to creating a partition that's only barely big enough for Ubuntu, unless you use the resizing handle on the partitioning screen. This problem was fixed in 9.l0, because inexperienced users weren't noticing the resizing handle, especially on very large disks. Maybe try 9.10 anyway.

---

### Post by DeanZF on 2010-02-21
I'm getting increasingly frustrated. I can't download anything with my current setup as Jaunty installed itself on a very undersized partition. I am a total Ubuntu neophyte and do not know enough of the Ubuntu-ese vocabulary.

Points:

[LIST=1]
[*]I know I'm so very sorry that I screwed up an Ubuntu machine that was working fairly well to try to get where I really do need to be, but that's another post.
[*]I know I need to make a larger "/" partition.
[*]I know that I don't HAVE a Windows partition (yet), only, ONLY Ubuntu on this machine.
[*]I know I can't update ANYTHING because the "/" partition is so puny.
[*]I know that I can't find any info on how to actually USE GPartEd. Topics on this forum say use it, but I can't find instructions on HOW to use it.
[*]I know that I downloaded the .ico file from the SourceForge site with the implication that it was a CD ready file. NOT!
[*]I know that the CD with the .ico file will NOT boot itself.
[*]I do NOT know what size the "/" partition should be if I can ever get it to work. PLEASE give some real guidance to that. I have a 250 gig hard drive, so I have room, but need some real numbers for the various partitions that Ubuntu needs.
[/LIST]
Everyone whines about how crappy MS products are and how shoddy the instruction set is for their products. I'm finding that stuff under this OS is not even that good. VERY frustrating. Most of it presumes some level of experience or expertise. For those of us coming from the other side, we need to have things spelled out so we can learn the process and vocabulary.

I cannot IM right now because I can't update Pidgin so it will work. My only resources are those who can carry on a conversation with me here or by email. I need someone to hold my techno-Ubuntu-feeb hand through this process, please. Darkish Dave started the process, but went away mid-stream. I did not even get a chance to thank him for the help that he DID provide, so THANKS, DARKISH DAVE.

---

### Post by adam814 on 2010-02-21
Like 3rdalbum says you can resize your partition from the LiveCD environment.  GParted is available in the LiveCD so you won't have to worry about downloading it.

---

### Post by DeanZF on 2010-02-21
Sorry. I don't understand the term "Live CD environment". Maybe I'm thick, or maybe it's a common term within this Ubuntu community that I've wandered into, but I really just don't understand what that means.

I have the install CD for Ubuntu 9.04. Do I/Can I boot from THAT CD in order to fix my mess? What is the "Live CD environment" and how do I get there??

And while whining, once I achieve "Live CD environment", how do I "run" GPartEd?

Thanks for translating for this Ubuntu-feeb.

---

### Post by nishant.singh28 on 2010-02-21
> **DeanZF said:**
> Sorry. I don't understand the term "Live CD environment". Maybe I'm thick, or maybe it's a common term within this Ubuntu community that I've wandered into, but I really just don't understand what that means.

I have the install CD for Ubuntu 9.04. Do I/Can I boot from THAT CD in order to fix my mess? What is the "Live CD environment" and how do I get there??

And while whining, once I achieve "Live CD environment", how do I "run" GPartEd?

Thanks for translating for this Ubuntu-feeb.
Okay sir!!! Step by step.

Method 1
Boot with the Ubuntu CD you have. That is the Live CD. 
Select "Try Ubuntu *blah blah blah*" .
Voila! You have the Live CD environment :popcorn:
Go to System>Administration>Gparted(Ithink that's the name. If not, you'll find something that mentions partition under Administration)
Select /dev/sda
Proceed with resize.

Method 2
Boot with live cd
Select install
Proceed with options.
Where you have the option for disk usage, select "Specify Partitions Manually"
Select the partition you want to install Ubuntu on and click change button.
Select Format option, specify size and select format(ext 3 for 9.04)
Select its mount point as "/".
If you don't have enough space to your liking, select the disk you want to shrink, click change and set new size.
Once done with this, proceed with install.


I sympathise with you as I had the same problem 6 months back. Haven't looked back since.:D

---

### Post by jenaniston on 2010-02-21
> **DeanZF said:**
> [FONT=Courier New]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   62M  98% /

[/FONT]

So a 2.3GB extended partition (sda5) is what you really wanted to install to ?

run sfdisk -l and let's all see what is on the rest of the disk 
(this command just lists partitions, then exits)

---

### Post by DeanZF on 2010-02-21
sfdisk -l (small L) gave me absolutely no results, just another blinking cursor, exactly like the one where I typed sfdisk -l.

does this need something more to indicate what I want it to be looking at?

:(

---

### Post by DeanZF on 2010-02-21
Also, thanks to [nishant.singh28]("http://ubuntuforums.org/member.php?u=869456"), I was at least able to understand Live CD and could boot from there and play a little in the GPartEd, but still to no avail since no one provided what sorts of target numbers I should be looking for.

I have a Linux pro coming over in a few minutes to see if he can help me unscramble this mess. Sigh. Glad for someone at church who gets this stuff and who actually gets paid to do it. Sigh again.

---

### Post by brusegadi on 2010-02-21
My suspicion is that when you re-installed the system you did not use all the available space...instead, you may have used the free space.  Since you just installed it, I would re-do it but make sure you use the entire drive.  B

---

### Post by jenaniston on 2010-02-21
> **Darkish Dave said:**
> Open up a Terminal and Use this command

```
df -h
```Terminal can be found under Applications > Accessories.

You should get something like

```
Filesystem            Size  Used **Avail** Use% **Mounted on**
/dev/sdb1              37G   23G   **13G**  66% **/**
udev                  1.8G  344K  1.8G   1% /dev
none                  1.8G  804K  1.8G   1% /dev/shm
none                  1.8G  300K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw
/dev/sda3             137G   48G   89G  36% /media/sda3

```I highlighted what you should be looking for.

Sorry if I wasn't explicit enough . . . just like as before
Open up a Terminal and Use this command

```
sfdisk -l
```i.e. run the sfdisk -l (small letter L) in the same terminal like you ran the df -h command before.

We'd want to see what the other partitons . . . besides the sda5 - that are there on the disk  . . .
and that is one of several possible ways  - 
 sfdisk is safe since it will always exit if you include that small letter L

If you need help to get to a text mode or terminal, let the people here know -
but no, you shouldn't be at the flashing cursor.

---

### Post by gadolinio on 2010-02-21
When you open gparted, you see a window with a bar representing your hard drive. When you resize/delete/create partitions (you'll see every option/tool there, just use it and you'll see that it's not hard to use), give for example 9 GiB for the linux swap "type" of partition (that means: create a partitions of 9 GiB, and "linux swap" as filesystem), and the rest for ubuntu (leave no partition there, so that the freee space is called "unassigned" or stg like that). If you don't have important files in there, you have nothing to lose. Just do it :P  After you've done you resizing/creation of partitions, click "apply" to tell the program to actually do those things on the disk.

---

### Post by northrup on 2010-02-21
Target numbers as in sizes?  Or partitions?

Ultimately, you want the swap partition (it'll be labelled "swap") maybe 1GB or so, and the Ubuntu partition (it'll be formatted as ext3 or ext4) to consume the rest of the disk (unless you plan on dual-booting, which, in that case, you should leave half of your hard drive space unallocated).

Basically, if it's ext3 or ext4 (I don't know which one 9.04 uses), expand it.  Anything else, shrink.  It doesn't sound like you have any other partitions in the way.

Hope this helps.  Even Ubuntu, which is supposedly the easiest Linux distribution to use for beginners, is difficult to transition to at first.  Just keep at it, and you'll get the hang of it eventually.  I remember how frustrating it was at first for me :D

---

### Post by DeanZF on 2010-02-21
Thanks to all who tried, even late in the game.

My buddy from church came over and walked me through the removal of flawed partitions and the reinstall of 9.04 to a properly sized partition.

Now in process of getting things reset and working again.

Hopefully I'll come to a place where I can give back.

---

