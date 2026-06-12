---
title: "Can mdadm damage a hard drive?"
date: 2012-01-01
forum: General Help
---

### Post by Headcase_Fargone on 2012-01-01
Hello all,

Last night I shoved four brand new 3TB HDs into an array.  I only mention that they were 3TB drives because that seems to cause some problems in Linux in my experience.

These drives were working fine by themselves.  They were detected, volumes were created using PARTED, etc.  SMART diagnostics showed healthy on all disks just last night.

Two of these disks have been in use for about a month now, and two are straight out of the package.

This morning I woke up expecting to find the array finished building but instead I now have SMART errors on one of the drives that was healthy just last night.  I'm not sure which drive it is yet but it struck me as odd.

Is it possible for software to cause damage to a hard drive or is this just really bad luck?

---

### Post by 2F4U on 2012-01-01
What errors do you get? In my experience, software may cause certain kind of filesystem corruptions, but it is unlikely, that you get bad sectors from using any kind of software.

---

### Post by rsvancara on 2012-01-01
What are the make and model of the drives you are using?

--
[Know Your Linux?]("http://www.knowyourlinux.com/")

---

### Post by Headcase_Fargone on 2012-01-01
> **rsvancara said:**
> What are the make and model of the drives you are using?


Hitachi 3TB green drives.  Turns out the bad drive was one of the new, unopened ones that's never been used before.  They all showed healthy when using PARTED on them.  It wasn't until I tried to build the array that it started throwing SMART errors.

Even the BIOS was showing a SMART error afterwards.  I had to bypass the error just to be able to boot.  Disk Utility was saying to replace the drive immediately.

For the record, here are the commands I ran on each drive in PARTED:

parted /dev/sdb
mklabel gpt
unit TB
mkpart primary ext4 1 3.00TB
set 1 raid on

Then in mdadm:
mdadm --create /dev/md0 --level=5 --verbose --raid-devices=4 --spare-devices=0 /dev/sd{a,b,c,d}1

Does that all look correct?

---

### Post by Paqman on 2012-01-01
> **Headcase_Fargone said:**
> is this just really bad luck?

This. 

Actually a failure on a brand new drive isn't even particularly bad luck. There's a reason why they come with a warranty, failures in early service due to manufacturing defects are realtively common.

---

### Post by Headcase_Fargone on 2012-01-01
> **Paqman said:**
> This. 

Actually a failure on a brand new drive isn't even particularly bad luck. There's a reason why they come with a warranty, failures in early service due to manufacturing defects are realtively common.

Welp I went out and bought another one rather than wait on a two month RMA (what with the flooding).  I take it's normal for the array to show as DEGRADED in disk utility when you first hit create in mdadm?

It's been sitting on 0% for about 15 minutes now.  Getting kind of antsy after last time.

---

### Post by rsvancara on 2012-01-01
Drives are so expensive right now.  I am waiting until the price goes down...someday.

---

### Post by Headcase_Fargone on 2012-01-02
Welp, it worked with the new drive and all is right with the world.  8.4TB free. Formatted and mounted the volume and it shows up just fine under /media.

One issue though:

Edit: That was easily fixed with a Google search.  Thanks again guys!

---

### Post by audiomick on 2012-01-02
> **Headcase_Fargone said:**
> 
After rebooting the volume isn't mounted.  It shows up under "Computer" but not until I open it up from there does it show up under /media.

I dare say you need to add it to your fstab.

Here is some reading. I wont try and explain it, as I have not messed around with this myself at all.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

edit: oh, you beat me to it. :)

---

