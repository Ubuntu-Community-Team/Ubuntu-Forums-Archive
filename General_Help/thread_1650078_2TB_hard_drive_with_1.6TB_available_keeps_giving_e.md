---
title: "2TB hard drive with 1.6TB available keeps giving error: &quot;No space left on device&quot;"
date: 2010-12-21
forum: General Help
---

### Post by purefusion on 2010-12-21
2TB hard drive with 1.6TB available keeps giving error: "No space left on device"

I'll try to be as detailed as possible, but I've been using the latest desktop livecd to copy some files from an old NTFS formatted internal 500GB hard drive to a new NTFS formatted 2TB external USB hard drive. Things seemed to be going well, up until a point where I started getting these errors stating "No space left on device". I get the same error whether I copy files or create a new directory via the Nautilus UI, or using mkdir, cp or rsync from the terminal.

I've never run into this before, and naturally it's something I'd least expected to run into with Ubuntu. I had the same issues on both 10.10 and an older 9.04 livecd I had laying around. This makes me suspect it might not actually be an Ubuntu issue, but I digress. Google wasn't much help in sorting out the issue (more on that later), and everyone in the  IRC support channel on freenode seemed to be baffled by this issue as well, so I wanted to bring it up here hoping that someone might shed some light on the cause and perhaps present a workable solution.

I started out running the 9.04 livecd, letting the drives mount wherever the system naturally decided to mount them. I opened each drive as a folder in the Nautilus UI and started copyiing some files over. After about 24GB was copied on the first set of files I was trying to copy over, I ran into the first "No space left on device" error. At this point, was still able to copy a few more files and folders, but there was a point where everything I tried to copy would copy over afterwards would no longer copy over.

Thinking it might have been an issue with Ubuntu 9.04, I grabbed the latest 10.10 release and ran that as a livecd, letting each drive mount wherever they naturally mount. After trying to create a new folder on the 2TB drive via Nautilus, and getting the same error, I tried the terminal. All relevant commands, including mkdir, cp and rsync all failed with the same error.

After Googling several variations of the error and relevant terms, the only suggestions I could find involved issues with inode limitations. However, I found that after running the following code, I got the following results which seemed to suggest that inodes are indeed not the issue. 

Here are the commands I tried, with the relevant results for each command shown below for both the 500GB (first) and the 2TB (second) drives:

```

df -i
 
Filesystem    Inodes        IUsed      IFree         IUse%    Mounted on
/dev/sdd1     176612292     2088978    174523314     2%       /media/Internal Backup
/dev/sdc1     1677282040    906416     1676375624    1%       /media/Seagate 2TB

```[COLOR=White].[/COLOR]

and

```

df -h

Filesystem   Size    Used    Avail    Use%    Mounted on
/dev/sdd1    466G    300G    167G     65%     /media/Internal Backup
/dev/sdc1    1.9T    265G    1.6T     15%     /media/Seagate 2TB

```[COLOR=White].[/COLOR]

Not sure what to try next, other than completely obliterating and reformatting the drive, then trying again, but I'd rather not do that. There's no saying that would even fix the issue anyway.

---

### Post by dcstar on 2010-12-21
> **purefusion said:**
> 2TB hard drive with 1.6TB available keeps giving error: "No space left on device"

I'll try to be as detailed as possible, but I've been using the latest desktop livecd to copy some files from an old NTFS formatted internal 500GB hard drive to a new NTFS formatted 2TB external USB hard drive. Things seemed to be going well, up until a point where I started getting these errors stating "No space left on device". I get the same error whether I copy files or create a new directory via the Nautilus UI, or using mkdir, cp or rsync from the terminal.
.........
Not sure what to try next, other than completely obliterating and reformatting the drive, then trying again, but I'd rather not do that. There's no saying that would even fix the issue anyway.

Unless you are **100% sure** that the new drive is formatted to standard NTFS (and that means not some weird non-standard block size formatting) then I would recommend reformatting it in Linux.

I do not trust drives pre-formatted for Windows systems with all sorts of Windows utilities usually on them.

---

### Post by purefusion on 2010-12-21
Yeah, you might be onto something. I don't think I ever did reformat it after I purchased the drive. Still quite curious what would be causing the issue though. Any way to check if that block size you mentioned might be non-standard is indeed not right? Also, what is the standard/ideal block size?

---

### Post by bryanl on 2010-12-21
When you set up a partition in Linux (ext2,3,or4), 5% is reserved for system use. That adds up to quite a bit on large partitions. 

If the partition does not need to worry about log files or system stuff and is used only for data storage, you can eliminate the reserve. 

tune2fs is the utility for this. See the man page. Try 

```
tune2fs -m 0 /dev/sd(whatever is appropriate)
```

the -l option will list the parameters that tune2fs. My root drive, for instance, lists "Block count: 4096000 | Reserved block count: 204800 | Free blocks: 1938521"

Not so sure what this does for NTFS drives. Also keep in mind that some confusion can exist in size reporting depending upon whether it is binary or decimal. That's the MiB vs MB thing.

---

### Post by psusi on 2010-12-21
> **bryanl said:**
> 
Not so sure what this does for NTFS drives. Also keep in mind that some confusion can exist in size reporting depending upon whether it is binary or decimal. That's the MiB vs MB thing.

It does nothing of course, since tune2fs is for tuning ext2 series filesystems.  It will not run on anything else.  And he isn't anywhere near 95% full.

What the OP needs to do is boot into windows and run a chkdsk on it.  Also check the output of dmesg for more detailed errors after this happens.

I have spoken to a few people recently with WD 'elements' external drives that they seem to be shipping with a broken NTFS format, maybe the same thing is going on with your drive.

---

### Post by ppv on 2010-12-21
Could you see if you have the same behavior in Windows incase you have access to a windows pc. 

If you would be using the external drive exclusively with Linux you may chose a linux filesystem which would be more compatible. If you are going to use it on both Windows and Linux system then you would want to use NTFS.

---

