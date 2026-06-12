---
title: "changed partition label, now can't log in"
date: 2010-04-10
forum: General Help
---

### Post by carltoews on 2010-04-10
I may have sabotaged my installation beyond repair, but I am nourishing a cautious optimism, as justified below, and would warmly welcome any ideas.  Here's the scoop:

The harddrive on my Dell Latitude is divided into a number of partitions; I used to run a Windows-Linux dual boot, so I had some EXT3, some NTFS, and some FAT32 partitions, but a few months ago decided to eliminate the windows, and thus converted the ntfs partition into a linux partition.  I've been using this newly converted partition for temporary backups; it held no important data.  This, at least, was my supposition:   yesterday, I decided to change the label on this partition (cosmetic motives), and after cavalierly making the change with GPARTED, I now can't log in.  

A few clues about what could be going on:

1.  The system boots up fine; when I get to the login screen, however, and enter my name and password, I get the following error message: "GDM could not write to your authorization file.  This could mean that you are out of disk space or that your home directory could not be opened for writing.  in any case, it is not possible to log in.  Please contact your system administrator."  

2.  All my files are intact (following some advice I saw posted on the forums, I hit cnt + alt + F1 and was able to log in) and as far as I can tell, I am not out of disk space.  This gives me hope that maybe I can restore the system without totally reinstalling Ubuntu.

That is about all I know.  If anyone has any thoughts as to what might be going on, I would be very happy to hear them.

Thanks in advance!

-Carl

---

### Post by blueridgedog on 2010-04-10
When booted and logged in via the ctrl+alt+f1 method, what is the output of the command:

```
df
```

?

---

### Post by me13221 on 2010-04-10
The first thing I would do is boot with a live CD and inspect the partition.  If you can mount it from a live CD then it should be possible to mount it from the proper install; otherwise, you can maybe troubleshoot.  At minimum, you can mount the root partition and edit /etc/fstab to avoid the problematic partition.

---

### Post by Skidbladnir on 2010-04-10
Most likely an ICE (I can't remember the full name, it's a hidden file, however) file got chowned by a sudo program.  Always use gksudo when launching graphical apps.  Anyhoo, ```

sudo chown -r yourusername:yourusername /home/yourhomedirectory

```
Will probably fix it.  I think.  I'm tired, so... just try it.

---

### Post by carltoews on 2010-04-11
I think you're probably on the right track:  the problem feels like it has to do with permissions.  I tried following your suggestion, and though it didn't fix the problem, it did change the error message.  (For the record, I had to issue the command in cnt+alt+F1 mode, since I can't log in, and I replaced the 'r' option with an 'R', since the lowercase variant doesn't seem to be valid.)  After getting back to the login screen via alt+f7, I tried logging in, and got this error message:

"your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try loggin in with one of the failsafe sessions to see if you can fix this problem"

The "view details" button produced this information:

"/etc/gdm/Xsession:  Beginning session setup...Setting IM through im-switch for locale-en_uS.  Start IMthrough /etc/x11/xinit/xinput.d/all_All linked to /mkdtemp:  private socket dir:  permission denied."

That last bit hints strongly that you're right about the permissions business, but I suspect I need to change the permissions elsewhere.  It's not clear (to me) from the error message what might need changing, however.

Thanks again, I really appreciate your help.

Regards,

Carl

---

### Post by carltoews on 2010-04-11
In response to the other suggestions:

To blueridgedog:  df yield a fairly long listing showing all my partitions, % used, etc.  As far as I can tell, every partition mounted fine (including the one whose label I changed.)  None of the partitions is full.  To me13221:  I ran gparted live, and all the partitions seem fine, an assesssment supported by the results of the df command.  So I don't think the issue is a bad partition, though that would have been a reasonable guess.

Thanks to both of you for your thoughts!

Best,

Carl

---

### Post by carltoews on 2010-04-11
Quick follow up:  in investigating the source of the error messages, I observe that I do not have the folder /etc/x11, which is odd in light of the message.  Should this folder exist?

---

### Post by blueridgedog on 2010-04-11
it is /etc/X11...note capitalization.  

Can you post the df output?

---

### Post by carltoews on 2010-04-11
Thanks, I hadn't noticed the capital (not surprisingly, the directory is indeed present.) 

Here's the df output:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             15236756   5285580   9183272  37% /
varrun                  517624       112    517512   1% /var/run
varlock                 517624         0    517624   0% /var/lock
udev                    517624        76    517548   1% /dev
devshm                  517624         0    517624   0% /dev/shm
lrm                     517624     39760    477864   8% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1             15116836    168724  14180208   2% /media/Hinterland
/dev/sda6             31873392  27094624   4778768  86% /media/Music
/dev/sda7              7286328   4006304   3280024  55% /media/Photos
/dev/sda8              7222136   6030312   1191824  84% /media/Documents

---

### Post by carltoews on 2010-04-11
Thanks to Google, I've solved the problem:  apparently, the issue was with the permissions on the /tmp file.  Here is a link to a relevant discussion in Ubuntu forums:

[http://ubuntuforums.org/showthread.php?t=288053](http://ubuntuforums.org/showthread.php?t=288053)

Many thanks to everyone who shared their thoughts!

Cheers,

Carl

---

