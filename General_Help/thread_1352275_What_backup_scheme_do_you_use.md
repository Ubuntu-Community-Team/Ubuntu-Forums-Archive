---
title: "What backup scheme do you use?"
date: 2009-12-11
forum: General Help
---

### Post by järven on 2009-12-11
Like the title says, what backup scheme do you use?
 
   I am asking since I don't do much backup myself, all I do is copy and paste my important files to an external hard drive. I want to do more but there are just so much information out there that it gets kind of hard to choose applications and ways to backup your data. So I hoped maybe those of you who have come up with a good scheme for backuping your data and system could share so I and others can be inspired   :). It would of course be positive for you too since you can get ideas from others and people can also make suggestions on how you could improve your backup scheme.
 
To precise my question a bit it would be good if you for example could answer this about your backup scheme:

Why you have chosen the way you do it and what computer situation you're in (do have one laptop or 5 desktops? for example), what applications you use and what features you take advantage of, how often you do your backups and if it's automated or not etc.


Please note that I am not asking you to make any howtos or anything, one can probably  find howtos to most applications through google and on their homepage, but of course you can link to to some if you want.

---

### Post by Woody70_06 on 2009-12-11
I back up my hme directory regularly, but other then that I don't image or clone..its not worth the time

I can reinstall Ubuntu, and be fully updated and configed in about 2 hours...so it seems to work out ok

---

### Post by raymondh on 2009-12-11
A good friend of mine (presence1960) introduced me to this 2-pronged approach..... and I have used it already to recover.

For normal back-ups, I use RSYNC in conjunction with the GUI, GRSYNC.  Both of which can be found in the repos.  I do a weekly back-up schedule unless required otherwise.

The other 'safety' net is I use is [PING]("http://ping.windowsdream.com/") to create image/s of my partitions and the whole HD. These images are saved in an external source ..... as well as in a specific HD (I have multi-HD set-up) just in case I lose the external.

Also, I have used aptonCD to save/restore/transfer my apps

Regards,

---

### Post by järven on 2009-12-13
> **raymondh said:**
> A good friend of mine (presence1960) introduced me to this 2-pronged approach..... and I have used it already to recover.

For normal back-ups, I use RSYNC in conjunction with the GUI, GRSYNC.  Both of which can be found in the repos.  I do a weekly back-up schedule unless required otherwise.

The other 'safety' net is I use is [PING]("http://ping.windowsdream.com/") to create image/s of my partitions and the whole HD. These images are saved in an external source ..... as well as in a specific HD (I have multi-HD set-up) just in case I lose the external.

Also, I have used aptonCD to save/restore/transfer my apps 

I was thinking about doing kind of the same thing, backup most of my files weekly and cloning my partitions monthly (well I guess cloning would depend on if I have done many changes to the system). I haven't heard of aptonCD but from reading some on their sourceforge page I suppose you use it to backup your applications, as a complement to RSYNC since that only backup files(?). That seems like a good idea, which I might add to my original backup plan.

---

### Post by järven on 2009-12-18
I thought people would be a little more interested in this topic, oh well.

---

### Post by Mighty_Joe on 2009-12-18
> **järven said:**
> I thought people would be a little more interested in this topic, oh well.

Read the numerous topics of people wailing and crying because their system is borked and they can't get to the precious files which they have not backed up and you won't be surprised that few people have backups.  
My scheme is simple: keep a copy my files on a 1TB external drive. Most of my data is media (movies, music) that doesn't change so versioning is not a problem. The *really *valuable files (baby pictures of my boys, for instance) get backed up to DVD and stored offsite.  
As Woody70_06 said, I can get a new machine up and running in no time, so it's not worth the time or trouble to image the OS or applications.

---

### Post by lisati on 2009-12-18
My usual method is to manually copy files I wish to back up either directly to an external HDD or via another machine, occasionally taking the time to review what I have on my external HDDs and deleting stuff I'm unlikely to need again.

---

### Post by amsterdamharu on 2009-12-18
Use dsl on a usb to back up mbr and partition tables of the partitions with dd (back up on the usb). You can then write that back on your hd when it becomes unbootable and you haven't changed the partition layout: BE CAREFULL WITH DD COMMAND, IT CAN DESTROY YOUR HARDDISK.
backup
dd if=/dev/sda of=sda.bin bs=512 count=1
dd if=/dev/sda1 of=sda1.bin bs=512 count=1
...
restore
dd if=sda.bin of=/dev/sda bs=512 count=1
dd if=sda1.bin of=/dev/sda1 bs=512 count=1

Use ghost to make a copy of my windows partition because that one breaks down quite often. Ghost is on a dos image file on the usb that syslinux and memdisk will start.

Use tar to make a backup of my linux system (started from the usb):
tar -cvpzf /sda5/backup/backup.tar.gz -&#8211;exclude=/sda5/backup --exclude=/sda5/lost+found --exclude=/sda5/sys --exclude=/sda5/mnt --exclude=/sda5/media --exclude=/sda5/home /sda5/
You can see from the above that I don't use seporate /boot and /home partitions

All these backups go to a hidden partition for windows and root only for Ubuntu:
in the /etc/fstab
/dev/sda2    /media/backup    vfat    nouser,noauto,noexec,rw    0    0

Some documents and photos go in there as well and then for some just to be extra safe go on my other computer's harddisk. I have to change the fstab line first to be able to mount it:
/dev/sda2    /media/backup    vfat    user,noauto,noexec,ro    0    0

But I would not be surprised that I will sometimes still loose that document or pictuere after I screwed up and deleted some stuff I shouldn't have.

I am not keen on re-installing and re-configuring everything again so the 2gb of the system backup is worth it (windows doesn't have a lot of big programs installed and I guess Ubuntu hasn't either). So that's why and (see above) how I back it up.

Mighty_Joe has a good point of storing the really important stuff off site and preferable multiple locations. Many of my photos are at my mums and my brothers home.

---

### Post by KeLa on 2009-12-18
Earlier system i used tar to make backups to external disk but now i have one server with raid on it where i rsync all changes periodically and also one disk network box for extra copy of extra important data.
I think that server's raid is safe enough in most cases because it has hot swap disks and if one disk fails and i can change it to new before next fails all data is safe.

---

### Post by andrewbrown22 on 2009-12-18
I use a combination of rsync & cron as well as simple copy and paste. 
I have a desktop and a server that I use to keep copies of my files on. I've recently upgraded them both to gigabit ethernet and it makes my backing up much quicker.
I setup cron and rsync to copy the "Documents" folder on my server (which is kept up to date from my laptop with copy and paste) to my Desktop's "Documents" folder every morning at 4am.
Every Monday at 4:30am I've set up my crontab to sync my ~70GB of Music from my server to my desktop. 
I find this to work very well, runs in the background and I have nothing to worry about. 

I also (about monthly) will plug in an eSATA drive (1TB) and exactly mirror the contents of the 1TB drive in my server with all my extra data. 

This way I've got at least 3 local copies on my network as well as an external copy in case it hits the fan as they say.

---

### Post by raymondh on 2009-12-18
and as mighty_joe hinted .... those really "precious" files are copied to DVD's.

---

### Post by stinkeye on 2009-12-18
I use luckybackup to backup my home directory once a week and also create a local repository on a usb stick from
/var/cache/apt/archives so I don't have to re-download if I have to do
a clean install.

---

### Post by scouser73 on 2009-12-18
I use [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html") and I just back up the **.googleearth .mozilla, .openoffice.org .purple** [Pidgin IM] **.songbird2** & **.thunderbird**.

Everything else is done as a fresh installation.

---

### Post by KeLa on 2009-12-18
Hope someday we have something like 2brightsparks syncback in Linux
[http://www.2brightsparks.com/syncback/syncback-hub.html](http://www.2brightsparks.com/syncback/syncback-hub.html)
Used it in windoze and it's wonderful software.
Beats all other backup softwares by 10 - 0 in my opinion.

---

### Post by KeLa on 2009-12-18
Hey, i just remembered what backup system Linus Torvalds used for backup when he started to development of the kernel, he just copied all files for one ftp server and after sort time you find them almost from all ftp servers in internet.

---

### Post by ushills on 2009-12-18
Personally I use jungledisk and Amazon S3 cloud.

You can't really rely on on-site backups and off-site with tapes or DVD's can become an admin nightmare.

Always test the reliability of restoring on a new machine, you will be suprised.  Also keep a copy of any backup software.

---

### Post by fcuk112 on 2009-12-18
dropbox all the way - i use it for backing up essential personal files, config and development files/scripts...  your files get automatically synched across all your machines on which you have dropbox installed so you can always work with them.  you get 2GB of free storage space, which can be expanded by introducing new people to dropbox or by purchasing it.

---

### Post by internalkernel on 2009-12-18
Simply... an rsync script. 

Tar ball /home, /etc, /usr/share/themes,icons,backgrounds,font

backup to external drive... I exclude the HUGE directories in my /home from the tar ball, so it only picks up configs. Rsync for music, videos, docs to a Backup drive. 

If you keep the name of the Backup drive consistent then you can create a UDEV script which will auto run the script everytime that drive is plugged in. 

oh and my personal favorite... 

```
dpkg --get-selections > installed_packages.txt
```

That way I don't have to worry about trying to remember all the little packages I've installed... Just dpkg --set-selections and install...

---

### Post by Ralph L on 2009-12-18
I am a fairly new Ubuntu user and like you I have backup questions.  

At this time I have partitioned my disk to include a Shared_Data partition and 5 operating system partitions.  One operating system is Windows and it is standalone.  It doesn't access the Shared_Data partitions.  All the other OS partitions have different versions of Ubuntu or Kubuntu on them and they all access the Shared_Data partition.  I just use either a simple drag&drop under Nautilus or a cp under Terminal to copy all my data on the Shared_Data partition to an external USB hard drive.  I have gone to the trouble of making sure that anything I want backed up is on the Shared_Data partition.  This includes all email, address books, group email lists, Firefox Bookmarks, and any files I create.

If I screw up an OS partition, which I have done, I just drop back to an older version of the OS and run using it.  That gets me going immediately.  When I get a chance I reformat and reload the OS that failed.  If I lose the Shared_Disk partition, which I have not had happen, I would reformat and reload that partition from the external USB disk.  If I mistakenly delete a file, I just go to the USB disk and copy it back.  I keep a rotation of 3 copies of my backup on the USB disk, so that if I would lose the latest one, I could at least get most of my files back from an earlier backup.  Of course if I have a total disk failure it would take me some time to reinstall the entire system and reload all my data from the USB drive.

I tried sbackup and strongly recommend against it.  In fact I recommend against any backup system that combines all the separate folder/files into a few very large files with a single directory.  sbackup does this and during my experimentation somehow the combined file directory got screwed up and I couldn't recover a single file.  I have had this happen on other backup systems over the years.  I want a system that is robust in the sense that if one file gets messed up I can still recover all the others.  So far the only way I have found to achieve this goal in Ubuntu is with a simple copy.

---

### Post by pricetech on 2009-12-18
Since I have to function in a winders world supporting a herd of winders boxen, I use SyncToy from MS.  (I know; boo, hiss, and all that)  So far it works just fine.  I sync to my thumbdrive at work, then again at home so my stuff is in two separate locations.

---

### Post by majoob on 2009-12-22
I've stared using rsync also to back up the entire /home directory and its four user folders to an external HD docking station with a 1TB SATA hard drive. The docking station supports both USB2 and eSATA but USB has been SLOW and I'm thinking of switching over to eSATA.

> **andrewbrown22 said:**
> 
I also (about monthly) will plug in an eSATA drive (1TB) and exactly mirror the contents of the 1TB drive in my server with all my extra data.


Andrew, did you have any problems with eSATA drivers / mounting your drive?

I'm doing a little research before purchasing a:
eSATA PCI card [http://www.newegg.com/Product/Product.aspx?Item=N82E16816132007](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132007)
and
eSATA cable [http://www.newegg.com/Product/Product.aspx?Item=N82E16812119250](http://www.newegg.com/Product/Product.aspx?Item=N82E16812119250)
for my
docking station [http://www.newegg.com/Product/Product.aspx?Item=N82E16817155014](http://www.newegg.com/Product/Product.aspx?Item=N82E16817155014)

I have Jaunty.

---

