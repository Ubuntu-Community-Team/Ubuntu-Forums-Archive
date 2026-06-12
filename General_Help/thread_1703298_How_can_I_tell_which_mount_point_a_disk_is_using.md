---
title: "How can I tell which mount point a disk is using ?"
date: 2011-03-09
forum: General Help
---

### Post by tg3793 on 2011-03-09
**How can I tell which mount point a disk is using ?** I'm getting a weird "Unable to mount SignatureMini" error and I narrowed it down to "SignatureMini" used to be sdb1 and now it is sdc. 

I would like to have the SignatureMini go back to being sdb1 mounted at /media/SignatureMini where it usd to be

But alternatively I suppose I would be ok with letting the SignatureMini stay at sdc where it is but to mount that at /media/SignatureMini.

I've never done this stuff before just making some educated guessing based on about five hours of reading through the forums and some fstab tutorials that I've been looking at. So any advice is appreciated :-)

---

### Post by tg3793 on 2011-03-09
And because I'm 90% sure someone is going to ask me what my fstab and fdisk -l looks like, here ya go :-)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    nodev,noexec,nosuid     0       0
#Entry for /dev/sda1 :
UUID=dd4aa20f-984c-4791-a709-97077ac2046e       /       ext4    errors=remount-ro       0       1
#Entry for /dev/sdb1 :
UUID=EAB0AEECB0AEBF07   /media/SignatureMini    ntfs-3g defaults,nosuid,nodev,locale=en_PH.UTF-8        0       0
#Entry for /dev/sda5 :
UUID=5befa7ad-aa00-49bf-bbca-7d851cf7a389       none    swap    sw      0       0

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004108d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60074   482542592   83  Linux
/dev/sda2           60075       60802     5841921    5  Extended
/dev/sda5           60075       60802     5841920   82  Linux swap / Solaris

Disk /dev/sdb: 137.4 GB, 137438952960 bytes
255 heads, 63 sectors/track, 16709 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x65787bf0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16709   134215011   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x802f9a8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

---

### Post by handy on 2011-03-09
Can you access the disk/partition or not?

---

### Post by tg3793 on 2011-03-09
Oh yes. Sorry for not including that. I just manually mounted the drive by creating a new mount point and then doing this "sudo mount /dev/sdc1 /media/SignatureNew".

However since I know that there is a LOT that I don't know, I want to avoid having my system in an abnormal state; that is any state that it was not in previously. I about 90% sure that I have other programs running on this system that reference my external hard drive as being at sdb1 like it was before and I can't think of any good reason why it should have changed.

Can you help me get it back to the way it was?

And one more point. All of these seemed to have happened yesterday after the update manager came up and I approved some things to update. And I honestly can't remember what they were right now (the things that updated). I simply recall them being pretty innocuous and typical to the things that I had approved before.

---

### Post by zenwalker on 2011-03-09
> UUID=EAB0AEECB0AEBF07 /media/SignatureMini ntfs-3g defaults,nosuid,nodev,locale=en_PH.UTF-8 0 0
Have you manually added this to fstab file? If so remove it. Automatically detected USB drives when plugged will be added to /etc/mtab file. If you add manually or some way to fstab, then always your usb drive will be mounted to that mount point.

---

### Post by tg3793 on 2011-03-09
Sorry for waiting so long before replying. Browser had a bad moment and I took for a walk while I wait for those thirty or forty windows to open :-)

In any case I did not manually add anything to my fstab file. I've ready too many bad stories about people editing it so I've been wary to do so ... I looked at it a bit a few months ago but I moved on to other things thinking that I would come back to it one day when needed.

Ok so this entry for my external 500 gig drive is not supposed to be permanently in there? Should I delete it? I do keep this drive attached to my computer at 364 days out of the year and I use it like a permanent file storage drive. Are there any advantages or disadvantages to having this "permanent" drive as a permanent entry in my fstab?

---

### Post by Grenage on 2011-03-09
> **tg3793 said:**
> Ok so this entry for my external 500 gig drive is not supposed to be permanently in there? Should I delete it? I do keep this drive attached to my computer at 364 days out of the year and I use it like a permanent file storage drive. Are there any advantages or disadvantages to having this "permanent" drive as a permanent entry in my fstab?

If you want a particular device to always use the same mount point, it's ideal (scripts, etc); if you don't really care, there are no benefits.

---

### Post by tg3793 on 2011-03-09
> **Grenage said:**
> If you want a particular device to always use the same mount point, it's ideal (scripts, etc); if you don't really care, there are no benefits.

Ok sounds like I want to err on the side of caution on this one and have that external drive permanently in the fstab. I'm working on a million things that the moment and can't think of a script that is referencing the external drive, but if there is one then taking it out will break something. But it sounds like there aren't any negatives in keeping a permanent fstab entry for my external drive.

So, back to my original question. How can I tell which mount point a disk is using ? :-) ... I think that's what I need to know before I try to unmount the drive at the mount point that it's at, then attempt to remount it where it was before at media/SignatureMini and then add that back to the fstab file.

Oh but wait, I still have to figure out why the SignatureMini is at sdc now instead of where it was at sdb1 and to change it back to sdb1. Is that right?

---

### Post by vanadium on 2011-03-09
> Re: How can I tell which mount point a disk is using ?
To answer that question: 
```

mount

```
> If you want a particular device to always use the same mount point, it's ideal (scripts, etc); if you don't really care, there are no benefits.
A labeled partition will neatly be mounted on the same place, /media/<label> without any need to include it in /etc/fstab. In fact, there are no good reasons to put a removable drive into /etc/fstab.

---

### Post by Grenage on 2011-03-09
> **vanadium said:**
> In fact, there are no good reasons to put a removable drive into /etc/fstab.

I can think of a few, but they are unlikely situations; it's usually a bad idea to have anything other than a static drive in there.  Sometimes you just don't want a drive mounted in /media, or listed in Nautilus.  I have a selection of drives which are renamed and reformatted frequently, but these days I use udev rules.

---

### Post by Morbius1 on 2011-03-09
> A labeled partition will neatly be mounted on the same place, /media/<label> without any need to include it in /etc/fstab.And one way you can change the label is by using GParted.

What's curious about the original post:
> I'm getting a weird "Unable to mount SignatureMini" error and I narrowed  it down to "SignatureMini" used to be sdb1 and now it is sdc. But you aren't mounting it by legacy /dev/sdxy, you're mounting it by UUID in fstab:
>  UUID=EAB0AEECB0AEBF07   /media/SignatureMini    ntfs-3g defaults,nosuid,nodev,locale=en_PH.UTF-8        0       0Have you done reformat?
Run the following command to see what the UUID is at the moment. It will also tell you if you already have a label on that partition:
```
sudo blkid -c /dev/null
```Anyway, as vanadium already stated, the best approach is probably to remove any reference from fstab and just redo the label.

---

### Post by tg3793 on 2011-03-09
Thanks everyone, you are giving me some great information and it's really helping to connect the dots with all that I've been studying regarding fstab and mounting.

@vanadium ... "mount" is a beautifully simple command. I only knew how to use it to actually 'do' the mounting. I didn't know it could be used to get the status of all mounted devices ... thank you.

@Morbius1

> What's curious about the original post:
     Quote:
                                                 I'm getting a weird "Unable to mount SignatureMini" error and I  narrowed  it down to "SignatureMini" used to be sdb1 and now it is sdc.                                 
But you aren't mounting it by legacy /dev/sdxy, you're mounting it  by UUID in fstab:To expand on my original error message, every time I plug my external drive in, 'or' simply have it already plugged in during a reboot, I get the same error message:

[B][COLOR=Green]Unable to mount SignatureMini

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdc1 on /media/SignatureMini
[/COLOR][/B]
So that's what led me to believe the problem lay with the fact that SignatureMini changed from sdb to sdc1 for some reason; I still don't know why.

> Have you done reformat?Nope.

> Run the following command to see what the UUID is at the moment.

sudo blkid -c /dev/null
ok here is my output:

[B][COLOR=Green]/dev/sda1: UUID="dd4aa20f-984c-4791-a709-97077ac2046e" TYPE="ext4" 
/dev/sda5: UUID="5befa7ad-aa00-49bf-bbca-7d851cf7a389" TYPE="swap" 
/dev/sdb1: LABEL="Redo" UUID="efb6b8c2-0776-4afa-a624-3146778f7571" TYPE="ext4" 
/dev/sdc1: LABEL="SignatureMini" UUID="EAB0AEECB0AEBF07" TYPE="ntfs"[/COLOR][/B]

I'll try to take "Redo" and "SignatureMini" off in a few minutes and then just remount the SignatureMini on sdb1 if possible. I'll see if that fixes my problem.

---

### Post by tg3793 on 2011-03-09
Sorry got distracted by some more research that I was doing. I've already unmounted both of the externals and am trying to figure out how to remount the sdc as sdb1 like it used to me. 

In the process of researching that I [found this post]("http://crunchbanglinux.org/forums/topic/11144/solvedsometimes-my-drive-is-sdb-and-others-it-is-sdc/") that advised "When using multiple HDs configuring UUIDs is probably the best option."

So, I'm still going to go through with taking out the fstab entry. But I'm keeping this second set of advice "in my back pocket" to consider later :-)

---

### Post by vanadium on 2011-03-09
Make your life easy, and remove the entry of that external drive from /etc/fstab. Shut your computer down, unplug that drive, boot up again and (eventually) delete the folder SignatureMini in /Media. Then plug the drive back in. Problem will be solved.

---

### Post by Hakunka-Matata on 2011-03-09
> **tg3793 said:**
> Oh yes. Sorry for not including that. I just manually mounted the drive by creating a new mount point and then doing this "sudo mount /dev/sdc1 /media/SignatureNew".

However since I know that there is a LOT that I don't know, I want to avoid having my system in an abnormal state; that is any state that it was not in previously. I about 90% sure that I have other programs running on this system that reference my external hard drive as being at sdb1 like it was before and I can't think of any good reason why it should have changed.

Can you help me get it back to the way it was?

And one more point. All of these seemed to have happened yesterday after the update manager came up and I approved some things to update. [COLOR="Red"]And I honestly can't remember what they were right now (the things that updated).[/COLOR] I simply recall them being pretty innocuous and typical to the things that I had approved before.

[COLOR="Red"]Open Synaptic Package Manager > File > history[/COLOR]

---

### Post by Morbius1 on 2011-03-09
> **vanadium said:**
> Make your life easy, and remove the entry of that external drive from /etc/fstab. Shut your computer down, unplug that drive, boot up again and (eventually) delete the folder SignatureMini in /Media. Then plug the drive back in. Problem will be solved.
Please oh please follow this sage advice ;)

---

### Post by tg3793 on 2011-03-10
I've had to be away from the computer all day and just 'finally' getting back to it. Ok so first the Synaptic History from Tuesday and Wednesday:

**Upgraded the following packages**:
inkscape (0.48.0-1~getdeb1) to 0.48.1-1~getdeb1
xulrunner-1.9.2 (1.9.2.14+build3+nobinonly-0ubuntu0.10.04.1) to 1.9.2.15+build1+nobinonly-0ubuntu0.10.04.1
gdm (2.30.2.is.2.30.0-0ubuntu5) to 2.30.2.is.2.30.0-0ubuntu5+langfixes~lucid1
language-selector (0.5.8) to 0.5.8+langfixes~lucid1
language-selector-common (0.5.8) to 0.5.8+langfixes~lucid1
avahi-autoipd (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
avahi-daemon (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
avahi-utils (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libavahi-client3 (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libavahi-common-data (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libavahi-common3 (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libavahi-compat-libdnssd1 (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libavahi-core6 (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libavahi-glib1 (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libavahi-gobject0 (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libavahi-ui0 (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libmetacity-private0 (1:2.30.1-0ubuntu1) to 1:2.30.1-0ubuntu1.1
libtiff4 (3.9.2-2ubuntu0.3) to 3.9.2-2ubuntu0.4
metacity (1:2.30.1-0ubuntu1) to 1:2.30.1-0ubuntu1.1
metacity-common (1:2.30.1-0ubuntu1) to 1:2.30.1-0ubuntu1.1
python-avahi (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2


* and I've already removed the entry of that external drive from /etc/fstab. Just haven't rebooted yet. It's always hard for me to stop what I'm doing in all of the desktops that I'm doing stuff on and convince myself to reboot 
... I figure I'll have to reboot eventually  ... But for now I've manually mounted the drive and am able to do stuff. Again, when I have to reboot, probably in the next couple of days, I'll have the nails in the coffin for this issue :-)

---

### Post by Morbius1 on 2011-03-10
> * and I've already removed the entry of that external drive from  /etc/fstab. Just haven't rebooted yet. It's always hard for me to stop  what I'm doing in all of the desktops that I'm doing stuff on and  convince myself to reboot 
... I figure I'll have to reboot eventually  ... But for now I've  manually mounted the drive and am able to do stuff. Again, when I have  to reboot, probably in the next couple of days, I'll have the nails in  the coffin for this issue :-)There is no need to reboot:
Step 1: If you have the external drive mounted - unmount it.

Step 2: Disconnect the exteranl drive from the machine.

Step 3: Make sure your fstab entry for the external drive has been removed.

Step 4: Run the following command:
```
sudo mount -a
```Step 5: Connect the external drive to the machine

Based on all the information you have posted the following things will happen:

- The external drive will automatically mount to /media/[COLOR=Black]SignatureMini
- A mount icon will appear on your desktop
- Nautilus will open up to that location
[/COLOR]

---

### Post by tg3793 on 2011-03-12
Morbius ... As the biggest commenter on this thread I have to naturally give you the most appreciation. But thanks to handy , zenwalker , Grenage, vanadium (in order of appearance) and all of you that helped me out. As it stands I did have to reboot because of an intermittent problem that I'm having when I'm doing some heavy multi-tasking with other users logged into their Gui. I'll work on that another day but in the meantime my external drive is back at work. Thanks to all.

---

### Post by Morbius1 on 2011-03-12
The person who had the insight was vanadium. All I did was say the same thing using way more words. :wink:

---

