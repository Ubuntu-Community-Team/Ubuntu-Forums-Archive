---
title: "&quot;No space left on HD&quot; errors despite 2.2G free space?"
date: 2010-07-02
forum: General Help
---

### Post by cAlpha on 2010-07-02
I just tried to download a torrent and got an error message indicating there was no space left in the download location I'd specified.  

This happened earlier when *df -h* showed ~900M of free space.  Just now, I'm showing ~2.2G of free space.  Anyone have ideas what could be causing this?

---

### Post by Chame_Wizard on 2010-07-02
```
sudo fdisk -l 
```
What does it say?

---

### Post by cAlpha on 2010-07-02
The partition causing the problems is /dev/sda3

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315        8039    54012900    7  HPFS/NTFS
/dev/sda4            8040        9729    13574925    5  Extended
/dev/sda5            8040        8816     6234528+   7  HPFS/NTFS
/dev/sda6            8817        9684     6972178+  83  Linux
/dev/sda7            9685        9729      361431   82  Linux swap / Solaris

```

---

### Post by cAlpha on 2010-07-03
Any thoughts on this?  Please and thanks!

---

### Post by synapsys on 2010-07-03
How big is the torrent you are trying to download? Most of the ones I download are larger than 2Gb.

Also, where are you pointing the download? To your home directory?

---

### Post by cAlpha on 2010-07-03
It's small, <100M.  It's not specific to torrents either--I had difficulty downloading content off a website earlier.

I've had success downloading to folders on my Ubuntu partition (sda6 above), but had difficulty dling to folders housed on my Vista partition (sda3 above).

---

### Post by synapsys on 2010-07-03
So if you're having problems downloading to the vista partition only, you might be having permission problems, not space problems. How do you mount the vista partition?

Open the vista partition via the "places" menu, right click in an empty space and hit "create folder" If it allows you to create a folder then you have write permissions, if you are not allowed to create a folder here, then you need to mount it in a different way that allows you access to the partition.

---

### Post by cAlpha on 2010-07-03
I mount automatically at startup having modified fstab; and had no problems creating the folder, so it's not a permissions thing. 

One other thing I just noticed is some funkiness with Firefox:  when I reboot or close and then reopen Firefox during the last several days, it restores tabs that were present from a number of days ago, not those from when I most recently closed it.  Could glitchiness in Firefox be causing this?  I'm on FF version 3.5.9, FWIW.

---

### Post by stderr on 2010-07-03
It's probably the space reserved for root - usually 5% of the drive is reserved on Linux systems (well, Ubuntu anyway, not certain about all other distros).

You can check how much is reserved for a partition with tune2fs (needs to be run with sudo, but the partition doesn't need to be unmounted or anything). Try this - I write the long list of output to a file in your home directory, and then do a few calculations to display the final value in MB. To figure out if the value you get represents about 5% of the partition, elementary - (100*VALUE_RETURNED)/PARTITION_SIZE_IN_MB

Change /dev/sda3 in the first command if you want to have a look at other partitions too.

```
sudo tune2fs -l /dev/sda3 > ~/hddinfo
echo "$(expr $(cat ~/hddinfo | grep "Block size" | awk '{ print $3 }') \* $(cat ~/hddinfo | grep "Reserved block count" | awk '{ print $4 }') \/ 1024 \/ 1024) MB reserved for root"
```

You can change the amount reserved with tune2fs too, but if the value returned represented ~ 5%, then probably best to work on the assumption that the partition is full and you need to clear some space. Root _does_ need to have (well, _should_ have) some space reserved...

edit: Having said this, I can't replicate such behaviour (all my drives appear to have 5% reserved, but df reporting is accurate - I can go down to zero MB free), and I don't see why your sda3 would be affected rather than sda6...

Could you post the output of:

```
sudo tune2fs -l /dev/sda3 | grep Reserved
```

---

### Post by cAlpha on 2010-07-03
Thanks for your reply.

I don't think I follow how this could be related to space reserved for root though:  
(1)  the issues are cropping up on my mounted Vista NTFS partition, so it shouldn't have anything to do with root or my Ubuntu partition in general--it looks like tune2fs only works on ext2/3/4 partitions. 
(2)  this has only recently become a problem--last week, and at various points in the past, the *df* seemed generally accurate, only yesterday and obviously today did I notice the inconsistency.  

Furthermore, earlier in the day, as I alluded to, df -h showed ~900M of free space, so I deleted files to mollify the 'No space left' error messages, only to have that extra space mysteriously gobbled up.  

Are there any kinds of files or processes that df -h doesn't include/report?  I still don't even fully grasp how this could be happening.

---

### Post by stderr on 2010-07-03
Indeed you're quite correct about tune2fs, & you wouldn't get blocks reserved on an NTFS partition. D'oh!

Couple more crazy ideas :) Have you emptied your Deleted Items? and secondly, could you post the output of

```
df -i
```

Could possibly be you've too many files on your Vista partition & have exhausted the inode pool... I mean, obviously NTFS doesn't use inodes but df -i still shows IFree/IUsed for NTFS partitions, & you'd natually assume there's a limit that you could exhaust in the ntfs-3g implementation, but pretty unlikely that you'd do so...

---

### Post by cAlpha on 2010-07-03
By all means, it seems like we've exhausted all the sane ideas... :)

Here's output from *df -i*:
```
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda6             436320  143983  292337   33% /
udev                  215181     915  214266    1% /dev
none                  215181       6  215175    1% /dev/shm
none                  215181      56  215125    1% /var/run
none                  215181       1  215180    1% /var/lock
none                  215181       1  215180    1% /lib/init/rw
/dev/sda3            2554592  152161 2402431    6% /media/OS
/dev/sda5            1183680   46505 1137175    4% /media/File Share
```

---

### Post by stderr on 2010-07-03
Crumbs, there isn't much else to check! Perhaps some of the files you deleted still have open file descriptors, in which case the space won't actually have been freed (so couldn't be written to), but df might well assume it has been freed. 

Could you post the output of (sanitise if necessary ;)):

```
lsof | grep '/media/OS'
```

---

### Post by cAlpha on 2010-07-03
Output of lsof:

```
rhythmbox  2163         26r      REG        8,3    9747294     141498 /media/OS/Music/Z Torrents/Random Album Title V0/02 Complications.mp3
transmiss  2280         39r      REG        8,3    5087289     151299 /media/OS/Music/Z Torrents/Gorillaz-On_Melancholy_Hill_(Remixes)-(Promo_CDM)-2010-SiRE/04-gorillaz-on_melancholy_hill_(she_is_danger_remix).mp3
transmiss  2280         43r      REG        8,3    8396712     151297 /media/OS/Music/Z Torrents/Gorillaz-On_Melancholy_Hill_(Remixes)-(Promo_CDM)-2010-SiRE/05-gorillaz-on_melancholy_hill_(we_have_band_remix).mp3
transmiss  2280         47r      REG        8,3   11306686     150258 /media/OS/Music/Z Torrents/Wolf Parade - Expo 86/03 - What Did My Lover Say (It Always Had to Go This Way).mp3
transmiss  2280         48r      REG        8,3   11293448     150261 /media/OS/Music/Z Torrents/Wolf Parade - Expo 86/09 - Oh You, Old Thing.mp3
transmiss  2280         67r      REG        8,3   11148059     151840 /media/OS/Music/Z Torrents/Ceo-White_Magic-WEB-2010-PWT/04-ceo-white_magic.mp3
```

*sigh*

---

### Post by stderr on 2010-07-03
Nothing there either.

You could try unmounting and re-mounting the NTFS partition.

A reboot might help, and failing that I'd recommend booting to Windows and running a filesystem check on the NTFS partition with chkdsk/scandisk/whatever it's called.

---

### Post by cAlpha on 2010-07-03
So frustrating...and to make matters worse, I've been having issues booting into my Vista partition of late as well (namely, rather than booting into Vista, it simply restarts and I'm sent back to the GRUB screen).  *shakes head*  

Thanks for your help/attempts all the same.  :)

---

### Post by stderr on 2010-07-03
No worries, problems only become properly interesting when the first few attempts fail ;) 

In that case, it looks like it could well be filesystem corruption with the Vista partition. To my knowledge, there's no *nix-based chkdsk utility for the NTFS filesystem, so you would have to use Winblows to repair any problems. Perhaps boot from a Windoze CD and try to chkdsk from the 'Administrative console', or whatever M$ calls that nigh-on-useless CLI.

NB: Please excuse my inline Microsoft-bashing, a considerable amount of alcohol brings out the Free Software Foundation ideals in me!

---

