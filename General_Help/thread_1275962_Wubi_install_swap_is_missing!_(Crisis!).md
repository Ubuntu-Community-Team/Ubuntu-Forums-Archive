---
title: "Wubi install swap is missing! (Crisis!)"
date: 2009-09-26
forum: General Help
---

### Post by J V on 2009-09-26
After installing wubi, I came across a bug with flash player that created an amazing memory leak (1.5gigs in 20 seconds from a 30 meg file, wow!) that made me realise I needed a bigger swap...

I logged windows, deleted swap.disk, ran the following command, and rebooted.
```
fsutils file createnew C:\ubuntu\disks\swap.disk 5000000000
```

It worked, I have a 5 gig swap file in exactly the right place, with exactly the right name... But ubuntu doesn't recognize it.

What started as some crummy adobe programming has led to 0 swap file... I don't feel safe trying to run ubuntu without a swap so I'm back on windows typing this.

This is a crisis! It needs a fix asap!

---

### Post by bodhi.zazen on 2009-09-26
First, depending on how much RAM you have, you may not need swap at all.

Second, to fix your swap problem you will need to add an entry in /etc/fstab.

Boot to Ubuntu

List your partitions with :

```
sudo blkid
```That will give you the UUID of your swap partition.

Now, ```
gksu gedit /etc/fstab
```Find the old swap line and update it with the new UUID.

Then simply:

```
sudo swapon -a
```Last, sounds as if you have a buggy program or application. How do you know you have a memory leak ?

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Linux uses RAM very different then Windows.

Post the output of :

```
free -m
```I think you will need to identify and if possible fix your memory leak rather then simply make a larger swap partition.

---

### Post by J V on 2009-09-26
Thanks for the help, booting now...

And yes I need to do something about the leak, but its specific to a particular flash applet, so I will complain to them later...

Will post results later

---

### Post by J V on 2009-09-26
Ok, this is a wubi instalation so I think something went wrong here...

Looking at the results from blkid:
```
/dev/loop0: UUID="e54bafe2-43bb-411b-a671-b7fd60ad7585" TYPE="ext3" 
/dev/sda1: UUID="53D9793E3B36A9F7" TYPE="ntfs" 
/dev/sda2: UUID="4F348D1C1274F319" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="BCDCD2F7DCD2AAC2" LABEL="OS_TOOLS" TYPE="ntfs" 
```I know recoverey and os_tools are actual partitions, and I'm pretty sure the swap isn't sda1:ntfs...

In /etc/fstab I see this:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro,relatime 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
```swapon gives me:```
swapon: /host/ubuntu/disks/swap.disk: Invalid argument
```

---

### Post by bodhi.zazen on 2009-09-26
What you posted looks fine, but I am not sure why it is not working.

Hopefully somebody more familiar with wubi can answer.

Otherwise, see these sections (it appears you can add a disk from within wubi/ ubuntu using the dd command).

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20create%20a%20virtual%20disk%20in%20Ubuntu?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20create%20a%20virtual%20disk%20in%20Ubuntu?)

---

### Post by J V on 2009-09-26
Been over that page a million times... its the only documentation for wubi available...

I don't think it will work, but I'll try anyway

Edit: Nope, swap filesystem isn't an option for that...

Mabey something about the file being created in windows is causing it to open incorrectly?

Will try to null the contents... How do I do that without emptying the file? :/ (Theres gotta be something to zero the contents)

---

### Post by J V on 2009-09-26
Sad little bump, how do I fill a file with zeros? (I doubt it will work but mabey, meh...)

rm -z has a similar command, but I don't want to remove the file, just blank it and leave it the same size...

---

### Post by bodhi.zazen on 2009-09-26
Well, what you want to do is make a swap file, not fil it with zeros.

The problem as I see it, the "disk" is not recognized.

To be honest, IMO wubi is to "try" ubuntu. If you wish to stay with Ubuntu I would advise you remove wubi, partition your hard drive, and perform a standard installation.

If you wish to stay with wubi, try making a swap file :

[http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html)

---

### Post by J V on 2009-09-26
1. I don't have a choice, thanks to a very nasty little legal knot I can't partition this drive and effectivley remove windows, so wubi is my only option...
2. I already made the swap file, its just not reading it... so, if I run a "dd if=/dev/null" on it, perhaps that will clear up whatever problem is causing ubuntu to throw a fit whenever it tries to load it...

Edit: After blanketing the swap with 0's, I'm still getting an invalid argument, too tired to bother atm, will have a crack at it tomorrow...
Edit2: Had to run mkswap for the system to recognize it... well, it works :)

---

