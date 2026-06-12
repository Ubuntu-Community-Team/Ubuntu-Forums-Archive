---
title: "Strange data corruption problem"
date: 2011-09-22
forum: General Help
---

### Post by joealanbrooks on 2011-09-22
Hi all,  ):P

I'm not sure whether to attribute this problem to Ubuntu or something else, so sorry if this is the wrong place for this.

I've been running Ubuntu with ntfs-3g.  I have a large ntfs drive I use to store media.  One day I opened an .mp3 file, and VLC instead played a bunch of snippets of other files on the drive (including video) spliced together. :shock: Weird.

All the other songs I tried behaved like that, but all the videos--which were in a separate folder--I tried played fine.  Thinking some part of my disk must be failing, I ran a S.M.A.R.T. self-test, but it came back clean.  Then I ran chkdsk, it returned and fixed some errors, but I read the log and nothing seemed relevant to this particular problem.  Tried playing some songs and they were the same.  Then I defragged the whole volume and tried playing songs again.  Now, instead of playing, say, 10 seconds of video, 5 seconds of the middle of a random song, etc., VLC would play a continuous song, but it was still totally random, began in the middle, and didn't correspond at all to the filename. :confused: It's like the hard drive is just putting the needle down in the middle of the record and playing whatever's there.

I haven't done any major operations to half of my drive since the last time I successfully played a song.  And my drive doesn't seem to be failing.  So something must have silently corrupted the filesystem?  The data seems to all be there even though it's attached to the wrong file... :-k Any idea how I recover it?

---

### Post by ajgreeny on 2011-09-22
Are you opening the mp3 files etc etc by double clicking on them, (or perhaps right clicking and choosing "Open with.."), or are you opening VLC and using the "Media ->Open file" dialog?

I must admit it seems a very strange thing to happen, and I am rather grabbing at straws looking for any information.

---

### Post by joealanbrooks on 2011-09-22
Thanks for the reply. :D It happens no matter how I open the file or what program I use.  Even the nautilus hover-over mp3 preview plays a random song.

It's not specific to music, though; a certain large chunk of my files (including all my images and some of my documents) are made up of data from other files, while another chunk of my files (mostly videos in their own folder) are fine.

I'm thinking because the dividing line between good files and bad files seems to be which folder they're in, it must be a filesystem problem rather than a disk problem.  Perhaps there's a way to re-align the file system to the data on the disk?

---

### Post by joealanbrooks on 2011-09-22
I should add that this was an ntfs disk used as my Ubuntu home folder (which I've heard can cause some problems), and that the disk is a WD20EARS if it matters.

---

### Post by patryk77 on 2011-09-22
Can you access that drive from a Windows PC? I know it's not a nice solution, but you should try and run Windows chkdsk.

There might be tools to fix an NTFS partition under Ubuntu, but I never used any.

---

### Post by ajgreeny on 2011-09-22
> **joealanbrooks said:**
> I should add that this was an ntfs disk used as my Ubuntu home folder (which I've heard can cause some problems), and that the disk is a WD20EARS if it matters.
Do you mean you have /home an an ntfs formatted drive, or have you now reformatted the drive to a linux file-system?

---

### Post by joealanbrooks on 2011-09-22
When I ran chkdsk, it did find and correct some errors, but I went through the log and all the corrections seemed to be about invalid characters in filenames. (Ubuntu seems to accept accented characters and some symbols in filenames that Windows sees as errors.)  Afterwards, my problem was still the same.

ajgreeny: I haven't reformatted it.  I don't want to lose this data!  What I meant was that up until this problem, the disk had been set to auto-mount on boot as /home/joe.  Now all I've done is remove it from my fstab.

---

### Post by ajgreeny on 2011-09-22
I am slightly lost.

Is this /home/joe your real home folder with all your hidden configuration folders and files as well as the data folders with all your music and videos etc etc.  If it is, I am surprised that you can even manage to boot the system, as many files needed to open your /home will not have the correct permissions;  /home/username** can not **be on an ntfs partition for this reason.You have also removed it from fstab so it does not mount at boot, therefore it simply can not be your /home, hence my lost situation.

Please can we see the output of ```
cat /etc/fstab
``` and ```
sudo fdisk -l
``` to allow us to see a bit more of your setup arrangements.

---

### Post by joealanbrooks on 2011-09-22
Appreciate your help aj :) I can post the fdisk after I reassemble my computer back to the way it was... Right now I'm transferring the good data to a new hard drive.

Sorry if that was confusing.  Yes, the ntfs drive was my real home folder, and it had everything in it a regular home folder does, plus all my media.  I believe this is a pretty common setup for people dual-booting Windows and Linux.  I've used it on various computers for at least a year without issue (I mean, not including this one).  I've only read an ambiguous forum post or two saying it's maybe an unwise or unstable thing to do, even though it works fine, so that's why I brought it up.  It'd be helpful if someone could explain what risk a setup like this poses to someone's data, if any.

What I meant was that I removed the drive from fstab only when I realized there was a problem, and then I stopped using that user.  Since that time, I've made some hard drive purchases, moved things around, and re-installed both Windows and Ubuntu, so the fstab I removed it from no longer exists anyway.  

I don't think that's important though.  The problem remains that this drive is not producing the right data.

---

### Post by joealanbrooks on 2011-09-22
It looks like the split was not as clean as I first thought... most of the folders contain both good files and bad files.  This is a sad day. :cry:

---

### Post by ajgreeny on 2011-09-23
> **joealanbrooks said:**
>  Yes, the ntfs drive was my real home folder, and it had everything in it a regular home folder does, plus all my media.  I believe this is a pretty common setup for people dual-booting Windows and Linux.  I've used it on various computers for at least a year without issue (I mean, not including this one).  I've only read an ambiguous forum post or two saying it's maybe an unwise or unstable thing to do, even though it works fine, so that's why I brought it up.  It'd be helpful if someone could explain what risk a setup like this poses to someone's data, if any.

What I meant was that I removed the drive from fstab only when I realized there was a problem, and then I stopped using that user.  Since that time, I've made some hard drive purchases, moved things around, and re-installed both Windows and Ubuntu, so the fstab I removed it from no longer exists anyway.  

I don't think that's important though.  The problem remains that this drive is not producing the right data.
I still believe that your problem is related to having your /home folder or partition on an ntfs format, and as I have already said, I did not even think it was possible, and would result in boot errors galore.

It is now obviously too late to see the output of the command from your old setup, but it would be useful to see the output from your new installation of those command I mentioned, and now ```
mount
``` as well, as this may sort out the truth of having your /home on an ntfs partition.

Can you point me to a reference regarding using ntfs as your /home please.  I think you may be getting muddled up with having a data partition on ntfs, which as you rightly say is not a problem and often used by dual booters.   I repeat, having /home on ntfs is impossible, so can you clarify this a bit more.

---

### Post by joealanbrooks on 2011-09-23
You're right, it doesn't seem to be as common as I thought it was.  I think you're right about the cause too.  To clarify, what I basically had was an empty /home/[user] folder on my Ubuntu partition, and then my ntfs disk would auto-mount at /home/[user] at each boot and fill the empty folder with data.  If you were to look at the ntfs disk, you'd see a long list of folders usually found in a home folder like "Music" and ".ssh" at the root of the file-system.

---

### Post by joealanbrooks on 2011-09-24
fdisk for the drive in question:
```
Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003f7a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2               1      243202  1953513472    7  HPFS/NTFS

```

Running:
```
sudo mount /dev/sdc2 /mnt -t ntfs
```
returns no errors... Is that what you meant by "mount"?

I don't have my old /etc/fstab file, but the line for this partition probably looked something like this:

```
Label=Joe
/home/joe
ntfs-3g
auto,uid=1000,gid=100
0  
0
```

---

### Post by joealanbrooks on 2011-09-26
Randomly occurring problems like this that no one can explain really make me regret switching to Ubuntu :(

---

