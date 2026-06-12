---
title: "How long does it take to zero out a hard drive?"
date: 2009-07-08
forum: General Help
---

### Post by blueshiftoverwatch on 2009-07-08
I have a 250gb hard drive that I'm trying to zero out using the shred command from the Xubuntu 9.04 live cd before reinstalling the operating system. The exact command I used after going into superuser mode was:
```
shred -vfz -n 100 /dev/hda
```

It said that it was doing passes over the hard drive but the process was done in about 20 or so minutes. I have no idea how long it would take to write over a 250gb hard drive one time with all zeroes, let alone 100 times. But it seems like it would take a lot longer than a half hour.

I went into file designated "hda" (which supposedly represents the entire hard drive) under the live CD in the /dev folder, right clicked and went to "properties", and under file size it said it was only 485.7mb big.

If /dev/hda represents the entire hard drive wouldn't it register as whatever size the hard drive is instead of only 485.7mb?

So how long should it take to zero out a 250gb hard drive in with one pass? Did I actually zero out the entire hard drive with the command I entered in above?

---

### Post by Slim Odds on 2009-07-08
What does the progress indicator tell you?

You should be able to estimate the time based on that.

---

### Post by rbc on 2009-07-08
I use this to zero out a drive, instead of shred:
sudo dd if=/dev/zero of=/dev/sd*x*, and it usually takes 1 1/2-2 minutes per GB

---

### Post by blueshiftoverwatch on 2009-07-08
> **Slim Odds said:**
> What does the progress indicator tell you?

You should be able to estimate the time based on that.
I can't post the command line readout because on the live cd Firefox crashes within a minute or so of opening it. Which isn't long enough to write a post. Also my flash drive doesn't show up when I insert it so I can't copy it a text file on that and open it up on the other computer I'm on now.

But I can tell you from memory that when it writes over the information I'll say that it's say "23MiB/486MiB" written. Meaning that it's only zeroing out 486mb of space, not 250gb.
> **rbc said:**
> I use this to zero out a drive, instead of shred:
sudo dd if=/dev/zero of=/dev/sd*x*, and it usually takes 1 1/2-2 minutes per GB
I tried that and it said that the entire operation was completed and that the device was filled within less than a second of entering the command. Which obviously can't be right.

---

### Post by Slim Odds on 2009-07-08
What does the following command show?
```
sudo fdisk -l
```

---

### Post by synapsys on 2009-07-08
I use darik's boot and nuke for all my disk wipes.... works great.
Just make sure you point it to the correct disk ;)

[http://www.dban.org/](http://www.dban.org/)

That being said.... isn't this overkill for a simple re-install?

---

### Post by k956411 on 2009-07-08
the speed completely depends on what speed size and connection your hard drive is.
Sata is quicker than IDE
Smaller is obviously quicker.
access time makes a difference too of course but yours is definately not working correctly.

as suggested check what is displayed using "sudo fdisk -l" to make sure the drive is recognised correclty and i assume you are using sudo?

finally, anything more than a single overwrite is a complete waste of time. 1 is enough to ensure nothing is recoverable.
yes i know they say it can be recovered with electron microscopes and whatnot but it can't.

and not to put you down in anyway, even if it was you would have to have some spectacular stuff on there for someone to take the time and money to do so.

---

### Post by Wim Sturkenboom on 2009-07-09
If you want to reinstall, zeroing the disk is a total waste of time. Shredding the disk sounds like more wasting of time. Only motivation for zeroing can be if you run into serious trouble with the HD. And only motivation for shredding is when you want to get rid of the disk and want to make sure that there's nothing leftover on it.

During all installs that I have done, I've simply removed the existing partitions and after that repartitioned the disk to my needs.

---

### Post by blueshiftoverwatch on 2009-07-09
> **Slim Odds said:**
> What does the following command show?
```
sudo fdisk -l
```
That worked at showing the designation of where the hard drive was. All I had to do with change "hda" to "sda" in the command and now it's zeroing out the drive. Although not 100 times, once should be sufficient.
> **synapsys said:**
> I use darik's boot and nuke for all my disk wipes.... works great.
Just make sure you point it to the correct disk ;)
DBAN was the first thing that I tried. But apparently it has major problems with computers that are running on Intel Core Duo processors. Because it worked great when I recommended it to a guy to use on his older PC. But horrible when I tried to run it on my iMac. As soon as I started started the zero out operation the  countdown to completion clock would go from around 2 and a half hours to over 700 hours within 10 minutes of leaving it run. I tried both the 1.0.7 and beta-2007042900 versions and neither worked well.
> **k956411 said:**
> finally, anything more than a single overwrite is a complete waste of time. 1 is enough to ensure nothing is recoverable.
yes i know they say it can be recovered with electron microscopes and whatnot but it can't.
In this instance I'm not concerned with making the previous contents of the HD unrecoverable, just zeroing it out. It seems there are two schools of thought as far as hard drive recoverability. The first is that hard drives need to be written over dozens of times (see: Peter Guttman) with psudo-random data and the second that one pass is sufficient. I don't know which is true. But if I were to give an old computer away to charity I'd err on the side of caution and go over it a dozen or so times with psudo-random data just to be sure.
> **Wim Sturkenboom said:**
> If you want to reinstall, zeroing the disk is a total waste of time. Shredding the disk sounds like more wasting of time. Only motivation for zeroing can be if you run into serious trouble with the HD. And only motivation for shredding is when you want to get rid of the disk and want to make sure that there's nothing leftover on it.

During all installs that I have done, I've simply removed the existing partitions and after that repartitioned the disk to my needs.
I agree that it's probably a waste of time. But the computer was getting very slow and even after I re-formatted the hard drive and re-installed OSX it was still just as slow as it was before. So I figured that zeroing out the hard drive couldn't hurt.

---

### Post by michy99 on 2009-07-09
Shred is for writing over a file, It does not write over the free space on the disk.

---

### Post by blueshiftoverwatch on 2009-07-09
> **michy99 said:**
> Shred is for writing over a file, It does not write over the free space on the disk.
On Unix-like systems everything is a file, which includes hardware devices such as the hard drive. Also, both System Rescue CD and the "fdisk -l" commands said that my hard drive has about 233gb of unallocated space. When I entered in the shred command the command line readout that periodically updates as it gets further towards completion says that it's successfully zeroing out X amount of space out of the 233gb of space total.

---

