---
title: "&quot;Unable to read NTFS $Bitmap: Input/output error&quot;"
date: 2012-06-18
forum: General Help
---

### Post by Jeremab on 2012-06-18
Hi all,
When I restarted my laptop today I was faced with the following error message:
an error occurred while mounting /media/docs
press s to skip  mounting or M for manual recovery

Then, when I try to open the 'docs' partition:
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda3 on /media/docs

And when I try
```
sudo mount /dev/sda3 /media/docs
```this is the message I get:
```

ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```I used to have a Windows partition, but I have deleted it some time ago.

-How can I access my documents on 'docs'?
-How could I make /media/docs mount automatically on startup ?

As I'm a beginner I'd be grateful if you could detail your answer. Thank you very much.

---

### Post by adroitster on 2012-06-18
I would recommend that you boot from a windows DVD first and somehow run chkdsk on that partition. 

After that in your 'fstab' file remove any line which has 'sda3' in it and then save it. Then install "NTFS configuration tool" from the software center and configure your partition. This will set up your system to mount it automatically on each reboot.

If you can mount it successfully then I would strongly recommend that you first copy all your data from that partition and convert that partition to a format which Linux handles better for eg. ext3 or reiserfs.

If you cannot perform the chkdsk part from Windows repair mode then I would suggest that you connect it as an external hard disk to a system running windows and then copy all your data and then convert it to a linux partition.

---

### Post by jim_24601 on 2012-06-18
It sounds to me as if your disc is dying. Go to Disk Utility, select the disc (which is probably your main hard drive) and go to SMART data. You are primarily interested in the "Current Pending Sector Count". If this isn't zero, you have a problem. (Well, you have a problem anyway, but you know what I mean.)

Am I correct in assuming that you blew away your Windows system partition but left the data drive as it was? And that it auto-mounted successfully up to now?

---

### Post by Jeremab on 2012-06-18
Thank you adroister and jim_24601.

I've had  a look at live CDs and DVDs but it looks like most of the Windows ones are meant to be run from an existing Windows session, and that's complicated for me.

"Current Pending Sector Count" shows indeed a warning (19 sectors need to be remapped apparently). Should I buy a new hard drive?

And yes, I used to have a dual boot, I deleted the Windows partition, extended the former common partition and left the format unchanged. Also, it automounted correctly before.

Is there another solution than to use the hard drive as an external hard drive to access the documents ?

By the way I didn't do anything special to the system (not even an update) the last time it worked correctly.

---

### Post by jim_24601 on 2012-06-18
I think you should buy a new hard disc. 19 is not a good number of pending sectors to have. (0 is a good number of pending sectors to have. Anything else is a sign of an ailing disc. I'm not an expert, but 19 looks pretty bad to me.)

[ Info: A modern hard drive will reserve an area of disc to use as spare space in case of bad sectors in the main area. However, if it's to move a bad sector into the reserved area it has to know about it. If the first sign of anything wrong is a sector it can't read, it has a problem. It can't just switch to the reserved area because there might be important data there that would be lost. So instead it marks the bad sector as "pending" in the hope that either it's a temporary glitch and it will eventually be able to recover the data, or that you'll overwrite it with known data that it can move. ]

Again, I'm no expert, but a pending count of 19 suggests to me that a big chunk of disc has gone down at once, or that it's been collecting bad sectors for a while and this is the first one that's hit a critical area of the disc, or that it's run out of spare space. All of these things are bad.

I reckon the disc is a write-off. The data may be salvageable, depending on the actual state of the disc, how important it is and how up to date your backups are. Is this a laptop or a desktop?

edit: Sorry, laptop, you said. That makes things trickier. It might still be manageable, though.

---

### Post by jmore9 on 2012-06-18
I would do this first , as has has been sugested just boot into yoour winows cd use the repair option and run chkdsk and then defrag from command line.

If you can move the data to another hard drive and boot into the manufacturs setup disk and reformat the drive.   You could also try before that to just unmount then re mount the drive.   

I would do this first , as has has been sugested just boot into yoour winows cd use the repair option and run chkdsk and then defrag from command line.

I now run only one of my 4 drives with NTFS just so my windows machine can talk to the linux one.  I also use the same drive alot in ubuntu.  Every now and then i boot into my winxp disk run chkdsk and after that i defrag it.

Hope this helps a little.

---

### Post by oklokl on 2012-06-18
The method I use


```
sudo umount -l /dev/sda3
```ex>```
mkdir ~/test
sudo ntfs-3g /dev/sdXy ~/test
``````
sudo ntfs-3g /dev/sda3 /media/docs
```# Incorrect execution... error.. ntfs
# mount /dev/sdXy ~/test



If you experience a bug in auto-mount use.
[http://askubuntu.com/questions/89244/how-to-disable-automount-in-nautiluss-preferences](http://askubuntu.com/questions/89244/how-to-disable-automount-in-nautiluss-preferences)
# automount fail
```
sudo apt-get install dconf-tools
```org> gnome >desktop >media-handling/automount
[ATTACH]219882[/ATTACH]




[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)
# ntfs automount 
# sudo apt-get install pysdm


but..

Linux does not like ntfs.
 Frequent crashes.




 windows booting -> Please fix the system files in Windows.

Is not recommended.
 This is how the emergency response.

```
#sudo apt-get install ntfsprogs #Does not require installation
sudo umount -l /dev/sda3   # Please.. umount
sudo ntfsfix /dev/sda3 

```If the file backup.
 ntfs partition and use the new format.

badblocks test..
man badblocks
[http://manpages.ubuntu.com/manpages/intrepid/man8/badblocks.8.html](http://manpages.ubuntu.com/manpages/intrepid/man8/badblocks.8.html)
[http://askubuntu.com/questions/59064/how-to-run-a-checkdisk](http://askubuntu.com/questions/59064/how-to-run-a-checkdisk)

---

### Post by Mark Phelps on 2012-06-18
> **Jeremab said:**
> I've had  a look at live CDs and DVDs but it looks like most of the Windows ones are meant to be run from an existing Windows session, and that's complicated for me.
LiveCDs are Linux disks, not Windows.  You can boot from them and use them to copy the files off the Windows filesystem partition to something else.

> "Current Pending Sector Count" shows indeed a warning (19 sectors need to be remapped apparently). Should I buy a new hard drive?
One report of bad sections does not mean your drive is failing.  Repeated reports, do.  Buying is new drive is your choice.

> And yes, I used to have a dual boot, I deleted the Windows partition, extended the former common partition and left the format unchanged. Also, it automounted correctly before.
So I take it, you can not boot into Windows to run chkdsk on the partition, right?  That's a problem because you're going to need to do that to repair the filesystem on that partition.

> By the way I didn't do anything special to the system (not even an update) the last time it worked correctly.
All you have to do to have this happen is shut down a PC with the windows filesystem partition still in use.  That would flag it as "dirty" and prevent Linux from mounting it again.

---

### Post by jim_24601 on 2012-06-18
> **Mark Phelps said:**
> One report of bad sections does not mean your drive is failing.  Repeated reports, do.  Buying is new drive is your choice.

A few bad sectors that the drive can remap, perhaps. We are dealing with a pending sector count in the double figures and a filesystem that won't mount. It is with difficulty that I restrain myself from quoting the dead parrot sketch.

I've seen a Windows disc with 4 pending sectors that Windows' recovery mode wouldn't touch. Linux gave the exact same error; I ended up blowing away the offending sectors with dd. The drive remapped them and I could recover the data. On that occasion I recommended that the guy not buy a new HD once I got Windows to boot and chkdsk'd it, however: 1) he was a student and couldn't really afford it, 2) it was only a few sectors, 3) he wasn't doing anything critical that he couldn't use a USB stick for, and 4) the laptop was going to be replaced in a couple of months anyway. And he bought the new HD anyway.

> So I take it, you can not boot into Windows to run chkdsk on the partition, right?  That's a problem because you're going to need to do that to repair the filesystem on that partition.

All you have to do to have this happen is shut down a PC with the windows filesystem partition still in use.  That would flag it as "dirty" and prevent Linux from mounting it again.

It's the bad sectors that are preventing the partition from mounting. There may be filesystem corruption as well, which would indeed need Windows to repair, if Windows' repair tools would work on the disc. Of course, it is the OP's choice how to proceed. Using a non-native filesystem type on a Linux system hasn't made things any easier, but I don't think it's the main problem here.

If it were my computer, I'd write off the disc, and do my best to retrieve the data. I shouldn't bother about Windows restore tools until I had a file system that was 1) physically readable and 2) corrupt enough that Linux couldn't get the important files off it. But as you say, it is the OP's choice. It might be possible to restore it to some semblance of life and keep the data without replacing the disc. If we're prepared to nuke everything and reformat, it gets a lot easier. Still, 19 pending sectors sounds like a pretty sick drive to me.

---

### Post by Jeremab on 2012-06-18
Thank you very much for your help, your patience and your clarifications.

I've used a Windows disc to use chkdsk (there was no defrag command though). After that I could access my files, so I backed up as advised. I've reinstalled Ubuntu completely and formated the partitions in ext4.

For information the number of bad sector decreased from 19 to 7  after the chkdsk command (or I think that was the reason) and then down to 1 after re-installation of Ubuntu.

---

### Post by jim_24601 on 2012-06-19
My apologies to Mark Phelps and Jeremab. It seems there was a bug in my mental model of how Windows chkdsk interacts with pending sectors. I think I prefer bugs in the software I write to ones in my own mental software. Unless they're really egregious, they don't cause me to make a fool of myself in public quite so much.

I'd expect a repair/reformat to get rid of most of your pending sectors, since when you write new data to them the drive can remap them, provided it's got enough spare sectors left.

I would still advise you to keep your backups current and plan to have replace the hard disc (or the computer) eventually. Of course, this is good advice in general, but it's even more important once you've started to get bad sectors.

---

### Post by Magnetixx on 2012-11-28
Hi

I had a similar issue and the easiest solution was ntfsfix.

In this case the hardware was known to be good. The error occured when the harddrive was unplugged without a proper shutdown.

```
sudo ntfsfix /dev/sdXX
```

sdXX will be something like sda1 for the first primary partition on SATA disc 1.

To find yours, just do 

```
ls - la /dev/
```

---

