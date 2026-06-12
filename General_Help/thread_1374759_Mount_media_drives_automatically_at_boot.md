---
title: "Mount /media drives automatically at boot"
date: 2010-01-07
forum: General Help
---

### Post by kabeza on 2010-01-07
Everytime I start Ubuntu, I have to go to Places, Home, then to browse the other drives so the system asks for the root password, and then mounts these partitions.

I need to mount the 2 partitions located in /media automatically
I've done some research, installed this package **pysdm**, run as sudo, but doesn't list the /media **(windows) partitions**

---

### Post by sarin_cv on 2010-01-07
u can edit /etc/fstab file and add the devices to be mounted at startup there....

for details, check this link 

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

or 

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by kabeza on 2010-01-07
thanks sarin_cv

While checking your links, I've downloaded a tool called MountManager which helped me to do this in a GUI window. I know it would be better to edit manually the /etc/fstab etc. but I don't want to spoil things now

---

### Post by Leppie on 2010-01-07
you can use the ntfs-config application to mount ntfs partitions automatically:
```
sudo apt-get install ntfs-config
```

add yourself to the FUSE group:
```
sudo adduser <username> fuse
```

this should mount the ntfs partitions at boot without prompting you for a password.

---

### Post by Morbius1 on 2010-01-07
You don't need pysdm or any other utility. This is an example of my process:

* Step 1: List the partitions on your system:*

Open **Terminal**
Type **sudo blkid -c /dev/null**

You'll get an output that looks like this ( partial ):
> [COLOR=Blue]/dev/sda1[/COLOR]: UUID="DA9056C19056A3B3" LABEL="WinXP" TYPE="ntfs" 
/dev/sda2: UUID="DA9056C19056A3B3" LABEL="WinXP2" TYPE="ntfs" *Step 2: Create Mount Points for your partitions to live in:*

Open **Terminal**
Type **sudo mkdir [COLOR=DarkGreen]/media/WinC[/COLOR]**

* Step 3: Add a line to /etc/fstab to mount the partition to that mount point on boot.*

[COLOR=Blue]/dev/sda1[/COLOR] [COLOR=DarkGreen]/media/WinC [/COLOR]     ntfs    defaults,nls=utf8,uid=1000,umask=007,gid=46    0    0
[B]
umask=007[/B] will give read / write access to owner and group and not others
**gid=46** will be the group referenced in the umask statement above. All local users on your system are member of group=46 (plugdev)
**uid=1000** will make you the owner. This really isn't necessary for you to have access, but if you ever want to share any folders on this partition across your home network , it will come in handy.

You should confirm that the uid=1000 number is correct by openning a terminal and typing: **id**

When you're all done, open a Terminal and type: [B]sudo mount -a

[/B]*Note: This is for NTFS partitions only. Linux filesystems ( ext3...) are handled differently and the options in my fstab don't apply and won't work. But the process is the same.*

---

### Post by Mareike on 2010-01-07
k

---

### Post by Mareike on 2010-01-07
Hi There,

I have the Problem that my Computer (Thinkpad X41) can not mount 2,5 external Hard Drives. I tried "removing it safely from Windows", I tried MountManager and I tried the "Force Mount". All Things which Ive found in Forums. Nothing worked. I formatted the External on Windows and Ubuntu. Still, nothings changed.

I will show here the error Response, maybe someone can help, I would appreciate it very much! Thanks a lot in Advance!!

"mount: only "root" can mount /dev/sdb1 to /media/disk-1"

and:

"DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Note: I even tried the "root mount ..." and "sudo mount ...". Still, no mounting.

---

### Post by Mareike on 2010-01-07
Uh, and it is formatted to FAT32, it was also on NTFS, but that as well did not work. Ive changed it to FAT32, then it worked for a while.

---

### Post by Mareike on 2010-01-07
Direction /media/disk-1 exists, i can not create that.

---

