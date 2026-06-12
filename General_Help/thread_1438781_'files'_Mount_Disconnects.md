---
title: "'files' Mount Disconnects"
date: 2010-03-25
forum: General Help
---

### Post by johnathanamber on 2010-03-25
Hello everyone,

I've posted about this previously, but I am unable to find that post...

I have a separate partition: 'files'.

This has the mount point of: '/files'.

My /home/johnathan folder is a symbolic link to:
/files/installed/backup/johnathan

So when this particular mount point '/files' is not available I get errors stating ICEAuthority and that /Desktop and /.nautilus can not be created.

If I  log in as root, I can not mount the drive using System > Administration > Disk Utility

I get the error that '/files' can not be mounted because it is un use.

Sometimes, if I wait a while while logged in a root it will 'magically' mount and work again... then I can login as my profile.

I love Ubuntu that it keeps all of your settings and program settings within the profile. So, if I have to reformat or reinstall Ubuntu I simply recreate the symbolic link to /files/installed/backup/johnathan and all of my settings are back. All that is left is to reinstall my apps and I am back to where I was before reinstalling.

So, how can I correct this? I do have two other partitions that have mount points, but they do NOT do this like '/files' does.

I've even replaced the UUID in '/etc/fstab' with the path tot he partition: '/dev/sda2'. This also didn't work.

Any suggestions?

Thank you and God bless,
Johnathan

---

### Post by zvacet on 2010-03-25
From synaptic install **pysdm** and try to correct mount of that partition.You will find pysdm under system>admin>storage device manager.

---

### Post by johnathanamber on 2010-03-31
@zvacet,

Thank you for the reply.

I have installed pysdm. It does see the drive.

What do you suggest I do with this to resolve the issue?

Are there some options tat should be checked?

I see that it is already set to mount at boot-time.

Thank you and God bless,
Johnathan

BTW, I was thinking of putting in a bug report since this has happened several times with no fix AND it happens even with reinstalling Ubuntu Karmic. I do not know if this happens with other versions since karmic is the only one I have used with this setup.

---

### Post by gmargo on 2010-03-31
What is the content of your /etc/fstab?

---

### Post by johnathanamber on 2010-03-31
@gmargo,

Here is the contents of 'fstab'. It was generated when I reinstalled karmic.:
> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc         defaults                            0  0  
# / was on /dev/sda1 during installation
UUID=3a19d055-cee1-40ba-a4fc-d5d97713fa5f  /                 ext4         errors=remount-ro                   0  1  
# /files was on /dev/sda2 during installation
UUID=68782b08-5132-4b6b-a897-15fb8adfbe82  /files            ext3         errors=remount-ro,users             0  2  
# /media/FILES was on /dev/sda5 during installation
UUID=868C13BE8C13A7A7                      /media/FILES      ntfs         defaults,nls=utf8,umask=007,gid=46  0  0  
# /media/WindowsXP was on /dev/sda3 during installation
UUID=D4746D42746D2886                      /media/WindowsXP  ntfs         defaults,nls=utf8,umask=007,gid=46  0  0  
# swap was on /dev/sda6 during installation
UUID=61b51a77-9735-420b-80ac-03b127799784  none              swap         sw                                  0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8               0  0  


---

### Post by gmargo on 2010-03-31
I'm confused as to what problem you are actually having.  I don't see anything in the fstab except for the 'users' flag on the /files partition (users should not be able to unmount the /home partition.)  Are you unmounting/mounting this partition?  I would think you'd want to keep it mounted.

---

### Post by johnathanamber on 2010-03-31
@gmargo,

Yes I want to keep it mounted. I thought it might help after adding pysdm that zvacet suggested. I guess I'll remove that option.

Basically I have my ~ folder running of of the '/files' mount. So if it disconnects I get errors noted in the original post. Which makes since seems how it can't connect to the mount to read/write the files.

When this happens I login as root and either, wait a couple of minutes for it to mount OR I have to remove the /files folder and recreate it and reboot.

This mount should never disconnect, however it does a couple of times a week.

To do what I am doing... I logged in a root.
Moved the username folder from /home to another location... in this case: /files/installed/backup.

Then I created a symbolic link from /files/installed/backup/johnathan to /home/johnathan

Therefore my entire home folder is running off another partition. So when I need to reinstall or upgrade or whatever, I don't have to worry about my data. I simply recreate the symbolic link and viola! EVERYTHING is back to where I left it. Minus the apps I've installed of course. But ALL of their settings remain since they are all in my home folder.

Does that make sense?

Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2010-06-08
Issue has not come back up since upgrading to Lucid Lynx. BTW, I did do a minimalist install... that might have helped.

---

