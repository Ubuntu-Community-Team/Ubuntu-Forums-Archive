---
title: "DMRaid - Why by default?"
date: 2010-01-17
forum: General Help
---

### Post by Roasted on 2010-01-17
Beginning with Karmic, I began to notice weird things in my partition editor when I would install it on my main rig. My system is as follows:

500gb - Vista/Kubuntu 9.10
500gb - Backup of Home Directory
250gb - Samba Network Drive
250gb - Samba Network Drive Backup

I DO NOT WANT RAID. If I wanted RAID, I would have gotten a board that supported it. When I ran into this, I thought it was just something stupid about Karmic. I tried Mandriva, openSUSE, etc... they all had it too - however openSUSE was so kind to offer an option to disable the DMRaid prior to installing - therefore allowing me to install the operating system without any BS.

So here I am... I put Karmic back in my computer, I install with the raid by default, then I have to go through the headache after to get the UUID of each drive, uninstall dmraid, add the UUID to /etc/fstab, and set it up that way.

Is there an option during the installer I missed to turn this off? Or is this the method of installing *buntu on computers with multiple hard drives that we just have to deal with?

---

### Post by jamesisin on 2010-01-17
Install the OS on one drive and ignore the other three until you log in at which point you can add those other three drives.  That's my usual method.

---

### Post by Roasted on 2010-01-17
> **jamesisin said:**
> Install the OS on one drive and ignore the other three until you log in at which point you can add those other three drives.  That's my usual method.

My usual method is letting all drives plugged in, sort through partitions manually, and blam - 6 steps taken down to 1.

---

### Post by jamesisin on 2010-01-17
I'm sorry, isn't your usual method failing you here?

---

### Post by Roasted on 2010-01-17
> **jamesisin said:**
> I'm sorry, isn't your usual method failing you here?

It doesn't matter what method I use. When I hook up the other drives, set up fstab, and reboot, it STILL comes up as raid.

So, no. My method is not working. And neither is yours. The only way around it was to boot up on 1 drive, uninstall dmraid, then go through the other steps.

So.. again... I ask... why is this installed by default, or at least why don't we have an option to shut it off prior to installing?

---

### Post by jamesisin on 2010-01-17
I have multiple drives in multiple machines and not a single RAID on any of them (except one I created manually).

---

### Post by Roasted on 2010-01-17
> **jamesisin said:**
> I have multiple drives in multiple machines and not a single RAID on any of them (except one I created manually).

I don't have RAID. In fact, the most common "con" of my motherboard when I bought it in the reviews I read was it did not have RAID. But I didn't want RAID, so it's all good.

Ubuntu 8.10 = fine.
Ubuntu 9.04 = fine.
Kubuntu 9.04 = fine.

The raid thing came on board with Ubuntu + Kubuntu 9.10.

I also tried GParted LiveCD, which saw the 2 drives as RAID. Mandriva Free 2010, Fedora 12, OpenSuSE 11.2, all saw the 2 drives as RAID.

Maybe something with a newer Linux kernel? I don't know what to blame.

Plus - if you fire up a LiveCD and go to synaptic or kpackagekit and search for "dmraid", it shows up as installed.

You probably never had a RAID problem because the drives weren't identical (taking a guess here). My two drives are identical and partitioned identically with the exact same size/type of partition on each (a single EXT4 partition spanning across the entire drive).

---

### Post by jamesisin on 2010-01-17
My 9.10 desktop has four identical drives in one SATA controller.  No RAID.  I had created two mirrors early on, but changed my mind and made four drives out of them.  (Regardless, until I created those RAID's they were separate.)

On my 8.10 system I don't show dmraid, but I suppose it's a useful package to have on a live CD.

---

### Post by Roasted on 2010-01-17
There seemed to be some confusion when Karmic came out, because a lot of reviews were saying that Karmic could not handle multiple hard drives and that they showed up weird in the partitioner. Only later did it surface that the drives were showing up as RAID, hence the weirdness people were seeing in the partitioner section of the installer or livecd.

But it still begs the obvious question. Why isn't there some sort of a toggle to turn this off? It's frustrating to have to jump through hoops because it was assumed raid is something I wanted.

---

### Post by jamesisin on 2010-01-17
If what you say is true, that Kubu is taking drives you've designated in fstab and making RAID's out of them, this is a very different (and more critical) issue than Kubu assuming that new, unallocated drives ought to be in a RAID.

---

### Post by Roasted on 2010-01-17
> **jamesisin said:**
> If what you say is true, that Kubu is taking drives you've designated in fstab and making RAID's out of them, this is a very different (and more critical) issue than Kubu assuming that new, unallocated drives ought to be in a RAID.

It was a fresh install. I hadn't configured fstab yet. By having the drives plugged in during the install, it does the fstab work for me.

But it's not exclusive to Kubuntu.

What about GParted LiveCD? It too saw my 2nd pair of drives as RAID. And Mandriva. And OpenSUSE. And Fedora. The only thing was, OpenSUSE (and I believe Mandriva) gave me the option to turn that off during the installer.

---

### Post by jamesisin on 2010-01-17
When I built my 9.10 desktop there was only the OS drive installed.  But I added all four drives on the SATA controller afterwards and didn't have any trouble with the new disc utility as far as RAID confusion was concerned.

---

### Post by Roasted on 2010-01-18
So tonight I decided to redo my desktop, so I did the following:

Removed 3 spare drives.
Booted up to LiveCD Ubuntu 9.10 64 bit with only the OS drive in.
Installed Ubuntu 9.10 64 bit.
Booted up. 
Got all updates/latest kernel/nvidia drivers.
Rebooted.
Set up twinview with my dual monitors.
Powered down.
Installed 3 backup drives.
Powered up.
Oh look, RAID is there.
Uninstalled dmraid via synaptic.
Tweaked /etc/fstab accordingly to boot drives via UUID.
Rebooted.
When booted, ran sudo blkid.
Oh look, BOTH backup drives have the same UUID. Thank you, DMRaid.
Formatted 2nd backup drive.
Ran sudo blkid. 2nd backup drive has new UUID.
Added that UUID to /etc/fstab.
Rebooted.
Now things are PERFECT. Just the way I want them.
Running rsync script to pull data from primary backup to secondary backup.

So, I have to ask yet again, what is the point of dmraid? It'd be nice to have a toggle option for it instead of having to go through these headaches.

---

### Post by jamesisin on 2010-01-18
I built two machines here with 9.10 and neither has dmraid installed (nor presumably ever did).  Nor does my 8.10 machine.  We must be doing something different during the build process if you are seeing dmraid installed.

(These machines are all 32 bit but I don't imagine that's the issue.)

---

### Post by Roasted on 2010-01-18
> **jamesisin said:**
> I built two machines here with 9.10 and neither has dmraid installed (nor presumably ever did).  Nor does my 8.10 machine.  We must be doing something different during the build process if you are seeing dmraid installed.

(These machines are all 32 bit but I don't imagine that's the issue.)

All of mine are 64 bit...

I never had the issue in 8.10. Only with 9.10, Mandriva 2010, and openSUSE 11.2, and the newest LiveCD edition of GParted - which is why I assumed it may be a kernel thing??

---

### Post by jamesisin on 2010-01-19
Well maybe someone who uses the 64 bit version will drop by and tell us if it's a standard part of that installation, but short of that I'm inclined to think it's the result of some choice-branch in the install process where you go left and I go right.

Can I assume you manually set up your partitions?

---

### Post by Roasted on 2010-01-19
> **jamesisin said:**
> Well maybe someone who uses the 64 bit version will drop by and tell us if it's a standard part of that installation, but short of that I'm inclined to think it's the result of some choice-branch in the install process where you go left and I go right.

Can I assume you manually set up your partitions?

Always. I don't think I've ever set up Ubuntu with the partitioning wizard options or whatever they are.

I always have additional drives in my PC that I want to handle different tasks, as a result I want them mounting to different locations, which is why I always used the manual method.

I really don't think there's anything in the installer to screw up. I mean think about it. Language, Time Zone, English keyboard, Partitioner. Where could we have gone separate ways? The partitioner (without touching anything at all besides hitting next step to open the partitioner menu) brings up the drives like that.

Just to reiterate - Mandriva and openSUSE both come through with the option to turn this off. Believe me - I've looked for it in Ubuntu. It's not there. :(

---

### Post by jamesisin on 2010-01-19
I don't know the answer but looking at the facts there must be one.  On all the installations I have done this application is not even installed let alone seeing any RAID's created without my direct intervention.

What is it that Holmes says?  "Eliminate the impossible and whatever you are left with, however unlikely, is the answer."

---

### Post by Roasted on 2010-01-21
Ahh, yes. I love it.

Booted up my system today - hard drive failure. My primary drive with my OS's was failing with bad sectors. So I pulled a spare 500gb drive from my shelf, dumped my OS's back on and was good to go. Went to set up fstab for the pair of 250gb drives I have running as backups. Oh, right. DMRaid. Again. Each of them have the same UUID, which I use to mount them with via fstab.

Fortunately I found a command (tune2fs or something) that can change the UUID. Prior to this I would just format it (since it was a backup of a backup) and just re-rsync the data over. tune2fs = quick fix! Anyway, so I set up fstab and everything is good... I check synaptic for dmraid - not installed. I reboot, and blam... dmraid is installed.

ATTENTION LUCID DEVELOPERS.

DO NOT HAVE DMRAID INSTALL BY DEFAULT.

Thanks.

edit - cancel that. It's giving me a ton of errors when I try to mount it. Formatting it. Again. And pulling the data back over. Again.

My gosh I cannot express how frustrating something like DMRaid is. PLEASE DISABLE IT.

---

