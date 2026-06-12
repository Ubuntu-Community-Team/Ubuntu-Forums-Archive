---
title: "delete ubuntu without traces"
date: 2010-11-22
forum: General Help
---

### Post by evaristegalois on 2010-11-22
Assume I have a computer on which I want to use ubuntu for a while (single boot). Assume also that in about six months I want to give this computer to Mr. X, but I do not want Mr. X to know that I have been using ubuntu. I don't want to install anything over top of ubuntu, I just want the computer to be completely (or as nearly completely as possible) blank so that Mr. X cannot infer what I've been doing on it. The trick here is that I can't use operating system x_{1} to delete operating system x_{0}. I don't want Mr. X to know anything about which OS I have been using. Mr. X, by the way, is a sophisticated computer user but not particularly interested in tracking me down. Once he sees that the computer is blank Mr. X will just install his own operating system and everybody will be happy.

---

### Post by ahayzen on 2010-11-22
Hi

You could either:

Use a live CD/Memory Stick to boot and run Ubuntu (very slow)
Or
Replace the HDD before giving to Mr X
Or
'Shred'/wipe the HDD with multiple passes before giving to Mr X

Also you could also try to wipe the RAM as well to leave no trace.

Hope that helps

Andy

Or have i not understood your post.

When you say ' I don't want to install anything over top of ubuntu, I just want the computer to be completely (or as nearly completely as possible) blank so that Mr. X cannot infer what I've been doing on it' does that mean that you want Ubuntu to remain on your PC when you give it to Mr X or does it mean that you want it removed?

---

### Post by Mark Phelps on 2010-11-22
Computers aren't "blank" -- but hard drives can be "blank".

If what you're asking is to blank the drive completely when you're done with it, look into using "dd".

See the link below:

[http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux]("http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux")

---

### Post by evaristegalois on 2010-11-22
I basically want ubuntu to destroy itself. Erasing a hard drive is not what I want. I want to erase the operating system. All of this is single boot. If Windows is the operating system and I install ubuntu, then Windows is gone. I want ubuntu to be gone, without a replacement. The next person who uses the computer will need an installation CD to install whatever OS they want on it. It's OK if all data are deleted but that's not the point.

---

### Post by oldsoundguy on 2010-11-22
format the drive to NTFS using a Linux CD with G-Parted or the Linux Disk Utility and then run the free downloaded program of KillDisk off of a boot CD.
Drive will have nothing showing to the average user.  (someone with TRUE quality forensics software MAY be able to find something .. but doubtful.)

That will erase everything .. know that is not what you want, but just deleting Ubuntu or Linux will not leave traces as you  will then have to TRY and remove the partitions.

Once a single OS is removed, it will not boot from the hard drive anyway, so a total wipe is best if the new owner is to start clean.

---

### Post by The Cog on 2010-11-22
As the howto link suggests, dd will do it. This command will overwrite the hard disk with random data. You need to do it from a live CD because it's unlikely to finish if you do it from the ubuntu on the hard disk - it will probably crash partway through and leave some un-overwritten data at the end.
> sudo dd if=/dev/random of=/dev/sda bs=1M

---

### Post by evaristegalois on 2010-11-22
Thanks. That sounds great. Just what I needed.

---

### Post by Andrew.Z on 2010-11-27
> **ahayzen said:**
> 'Shred'/wipe the HDD with multiple passes before giving to Mr X

[Multiple passes are not better than a single pass](http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk)

> **The Cog said:**
> As the howto link suggests, dd will do it. This command will overwrite the hard disk with random data.

Random data is not better than zeros, and zeros make the drive blank (as if it were never used) rather than implying you are trying to hide something (as if by encrypting it or by overwriting it with random data to hide something). Also zeros are faster than random data (which will probably be bottlenecked at the CPU). I use this command

dd if=/dev/zero of=/dev/sda

Or use DBAN with the option to overwrite remapped sectors.

---

### Post by evaristegalois on 2012-01-04
So, now that I actually need to do this it doesn't work. 

If I use the command

```
dd if=/dev/zero of=/dev/sda
```

then it says "permission denied" (not surprising!)

If I use sudo (from a live CD), nothing happens; I am not even asked for a password -- I guess using sudo doesn't make much sense from a live CD.

How do I get around this?

---

### Post by evaristegalois on 2012-01-04
Ah, sorry, "nothing happens" just means it's quietly working on it.

All's well.

---

