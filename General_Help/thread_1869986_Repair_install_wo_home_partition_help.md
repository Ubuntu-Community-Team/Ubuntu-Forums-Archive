---
title: "Repair install w/o home partition help"
date: 2011-10-26
forum: General Help
---

### Post by dez93_2000 on 2011-10-26
Hi all.
In lieu of a full solution to [this]("http://ubuntuforums.org/showthread.php?t=1865796") I'm trying to repair install 11.10. The 4th post of [this]("http://ubuntuforums.org/showthread.php?t=1435000") says 

"Boot the install CD and go through the install process as usual. Use the  SAME user name and when you get to the partitioner, check the box  marked "Manually select partitions" and click forward. You'll see your  old setup. UNCHECK all the 'format' boxes and mount the partitions in  the same place they are now. As long as no 'format' boxes are checked,  no data will be lost and system files will be overwritten with the  originals. You'll need to do security updates again."

However it's not clear how I do it & I  don't want to destroy everything. As per my reply to that post (on a solved thread), the liveCD installer doesn't display my existing ubuntu configuration with an option to overwrite install without suggesting a partitioning solution which sounds like it'll wipe everything.

My setup:

/sda
 /sda1 i have ubuntu

/sdb
/sdb1 i have my old xp install.

On the drop-down list for which partition to select, neither ubuntu or xp are clearly shown. What is does show is:

dev/mapper/jmicron_SiRAID
 dev/mapper/jmicron_SiRAID1 (type=ntfs)

In the drop-down selection below, for those entries it says
Linux device-mapper (mirror) for the first and
Microsoft Windows XP Professional for the second.

If I click to install on the linux one, it says "no root system is  defined. please select one from the partitioning table". If I click "new  partition table" on the top one it asks if I really want to format the  whole partition. Given that I want to install over the existing setup, I  assume I don't. In which case...um? DO I want to format the whole partition?

I have two identical drives on the RAID SATA ports, but not configured in a RAID array. They were a XP RAID before I got ubuntu originally, then i made SDA ubuntu & SDB win XP.

Any advice / thoughts / tips really really appreciated.

---

### Post by rowbird on 2011-10-26
You should make sure you have all your data backed up before you attempt to repair/reinstall. Back it up to an external drive first if you hav'nt already done so.
   If you can boot up your Ubuntu, you can use Grsync to back up to an external device, then delete your ubuntu partition and create a 10Gb root partition, and the remaining as a home partition using Gparted. This must be done with the disk unmounted as in using a live cd to do it. Then reinstall, and add your data back. I am not sure about your raid installations, although you might want to disconnect them to avoid any confusion while you reinstall.

---

### Post by oldfred on 2011-10-26
+1 on backups

It does not look like you have a separate partition for /home and that is the only way to reinstall without overwriting a /home that is just a folder in / (root).

If you had RAID and do not now have RAID run this to remove RAID meta data on drives.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by dez93_2000 on 2011-10-27
Thanks both. I can't get into ubuntu at all however i can access the files using something i found for windows caled "DiskInternals Linux Reader" which seems to work well and is free (me plugging it in case anyone else is in the same situation!).

Can you guys think of any particular places to back up?
Is it the case that I should back up the whole of \home\me\ ? It occurs to me that i'd be keeping loads of application files which would probably be just as well installed fresh.

Other than
.evolution for emails
.firefox for bookmarks (or rather .mozilla/firefox)
.dropbox for the settings
and all the non-dot folders,

is there anywhere else which is going to have personalised stuff, AFAYK? usr/share/? Nothing's jumping out at me from there.

####


Fred, re: the RAID advice: firstly - thanks. It does look like extant RAID config might be spoiling the broth here, but - unless you think this unwise - i'm feeling it'll be better to leave it until I backup, and overwrite install with a home partition, because I'm concerned that currently GRUB is working fine and I can get into XP which means I have a working computer, and if I follow any of the correct advice wrongly, or the wrong advice correctly, I could mess with GRUB and thus not access XP,  or worse, delete XP altogether. What thinks you on this one?

Cheers both.
dez

---

### Post by oldfred on 2011-10-27
I use rsync to copy to another drive that I have. I copy all of /home but have little or no data in my /home as I have that in other partitions. But I backup a list of installed applications, system configuration and /etc in case I have made some system wide settings changes. I normally do clean installs, but install to another 25GB / (root) partition so I can go back and get something I missed. My /home is only about 1GB with most of that .wine for Picasa. My / is about 6-7GB but sometimes something seems to get written into root so I like to have some extra space.

More detail on what I backup:
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by dez93_2000 on 2011-10-27
Fred, that's brilliant, thanks, i'll get cracking on this tonight.


.wine for Picasa meaning you use the windows Picasa in WINE rather than the [linux one]("http://picasa.google.com/linux/thanks-deb.html")? How come?

dez

---

### Post by oldfred on 2011-10-27
My wife wanted all the features of the Windows version as she started in XP with Windows. The Linux one is based on the older version and has not all the new features.

Google actually helped Wine improve their system to work with Picasa and the Linux version just installs its own wine system.

Had to make one setting to get the internal uploads to Kodak or other sites to work, and have to install a few other things in wine to make it work well.

---

### Post by dez93_2000 on 2011-11-04
So I unplugged my windows drive and went into the live cd and was given the option of doing an updaet (or upgrade, not sure) install from 11.10 to 11.10 which i did. Most of my stuff has been saved, which is great. Just need to copy across the evolution folders to home/me/.local/share/evolution/ and sort out something odd:
my drives now all have underscores after them eg
Samsung_
instead of
Samsung

so various links and shortcuts don't work. Not sure why - I think ubuntu thinks the no-underscore drives are still there so has renamed what it sees as new drives to avoid a naming conflict? Just a guess. Will have to sort this out as well as fix grub which doesn't recognise my wondows drive as bootable since i plugged it out & in.

Thanks for the tips guys - really helpful.

---

### Post by oldfred on 2011-11-04
If you have a partition fsab mounted in /media or /home, it may show it again with the underscore. But if you try to use the second one it will give an error that it is already mounted.

---

### Post by dez93_2000 on 2011-11-04
it's the underscore ones that work.

I'm going to try this:
[http://ubuntuforums.org/showpost.php?p=9203303&postcount=2](http://ubuntuforums.org/showpost.php?p=9203303&postcount=2)
(I did a bit of searching!)

Next step: grub (assuming the above works)!

---

