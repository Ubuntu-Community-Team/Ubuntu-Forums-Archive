---
title: "Samba Shares Not Writable | Side issue about Mounting"
date: 2012-06-18
forum: General Help
---

### Post by howett on 2012-06-18
I've been messing with this issue(s) for days (searching too), but have not figured out a solution. I just recently installed 12.04 (64bit) (no upgrade), and was previously using 10.10 for a long while. I had everything setup exactly how I needed it on 10.10, but the "this version is no longer supported message" prompted me to finally upgrade.

Now in 12.04, I cannot get the samba shares to allow write access from other machines in the local network. My 10.10 smb.conf file was extremely stripped down to the bare essentials: 1 path to /media, no printers, no comments. I used that as a basis for the new smb.conf. I gained access to the server immediately and could read and execute everything. I could not write though. After searching I read several posts saying there was changes to the smb.conf after ubuntu 10.x (I didn't see anything really), so I went back to the master file and added my changes there without stripping down the file. Again, I can connect just fine and access all the files, but I cannot create new files or alter existing ones.

The drives I am accessing in the media folder are ntfs. I have manually added them to the fstab file and they mount at boot just fine. While on the ubuntu machine I have no problems accessing and altering any file (or creating new). They are currently owned by root:root, so I wasn't sure if that was the samba issue. I have since changed one of the drives to be primaryuser:sambagroup (not real names), but I still cannot write to the drive from samba.

So, I am at a total standstill right now. I've never had a problem connecting, or writing in the past, but after the upgrade to 12.04 no matter what configuration I do... nothing.

Some Configuration Information (using/ed):
read only = no
writeable = yes (doesn't show up in testparm)
create mask = 0775
directory mask = 0775
valid users = primarysambauser

---

Side Issue:

Along with manually adding the mounted drives in fstab, 12.04 doesn't always unmount them correctly on halt or reboot. This sometimes causes the shutdown screen to hang. If I manually unmount every drive before shutdown/reboot, it works every time. I've tried every fix under the sun to get this working correctly, but still nothing as well. Any help with this issue would be helpful, but the samba write issue is my main concern.

---

### Post by Morbius1 on 2012-06-18
The only way out of this is to ask for everything related to the issue(s). So please post the output of the following commands:
```
testparm -s
``````
cat /etc/fstab
``````
sudo blkid -c /dev/null
```

---

### Post by howett on 2012-06-18
testparm -s does nothing. testparm prints out:
```
[global]
	workgroup = My Workgroup
	server string = %h server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[media]
	comment = Media
	path = /media
	valid users = username
	read only = No
	create mask = 0775
	directory mask = 0775
```

manually added fstab portion (removed uuids):
```
UUID=thekey	/media/sdc1	ntfs-3g defaults,nls=utf8,uid=1000,gid=124,umask=022	0	0
UUID=thekey	/media/sdb1	ntfs-3g	defaults,nls=utf8,umask=022	0	0
UUID=thekey	/media/sdd1	ntfs-3g	defaults,nls=utf8,umask=022	0	0
UUID=thekey	/media/sda4	ntfs-3g	defaults,nls=utf8,umask=022	0	0

```

blkid prints (unneeded portions removed):
```
/dev/sda4: UUID="thekey" TYPE="ntfs"  
/dev/sdb1: LABEL="sdb1" UUID="thekey" TYPE="ntfs" 
/dev/sdc1: LABEL="sdc1" UUID="thekey" TYPE="ntfs" 
/dev/sdd1: LABEL="sdd1" UUID="thekey" TYPE="ntfs" 

```

I've removed the uuid's above, but they're all matching.

---

### Post by Morbius1 on 2012-06-18
> testparm -s does nothingDon't know how that could be so I'll ignore it.
> [media]
    comment = Media
    path = /media
    valid users = username
    read only = No
    create mask = 0775
    directory mask = 0775The only way "username" will gain anything other than read access to anything in that share is if you either set /media to 777 which I do not recommend or maybe change groups, change permissions to 775, and make sure "username" is a member of that group. I don't recommend that either. Share the individual mount points within /media instead.
> I've removed the uuid's above, but they're all matching.     That cannot be either unless you cloned the partition. The whole idea of a UUID is that they are unique.
> UUID=thekey    /media/sdb1    ntfs-3g    defaults,nls=utf8,umask=022    0    0You are mounting the ntfs partition with write disabled to everyone other than root. Change "umask=022" to "umask=000".

---

### Post by howett on 2012-06-18
By "matching" i mean they are the correct uuids. They are all unique. Changing umask to 000. Testing.

---

### Post by howett on 2012-06-18
I changed the umask from 022 to 000. Still no write access and everything inside of /media is still owned by root:root. Even with the mask of 0777 in the samba share, I cannot write.

I downloaded the gnome user and group manager to see what the user looked like (easily). I altered the samba users' group to the same as it's name, root, primaryuser; still nothing.

When I manually share these mounted drives through the sharing options of ubuntu, that share is removed every time I reboot the computer. Are you recommending a separate samba share for each drive I've added to fstab?

---

### Post by Morbius1 on 2012-06-18
In reverse order:
> Are you recommending a separate samba share for each drive I've added to fstab?     Yes. You don't want to be sharing a system directory the way your are doing. Create a separate share for /media/sdb1, etc.. instead.
> When I manually share these mounted drives through the sharing options  of ubuntu, that share is removed every time I reboot the computer.It never occurred to me that you were using nautilus-share. Please post the output of the following command. You might be sharing things twice:
```
net usershare info --long
```> I downloaded the gnome user and group manager to see what the user  looked like (easily). I altered the samba users' group to the same as  it's name, root, primaryuser; still nothing.You are dealing with an ntfs partition. You cannot change the ownership or permissions of an ntfs partition outside of fstab. 
> Even with the mask of 0777 in the samba share, I cannot write.Create mask, directory mask, and any other kind of mask in the samba share will have no affect because this is an ntfs partition - see above.
> I changed the umask from 022 to 000. Still no write access and everything inside of /media is still owned by root:root.umask controls permissions not ownership. With a umask of 000 you have a partition that is read / write to everyone. Your problem with write access is somewhere else if you changed the fstab entry after unmounting the partition and either rebooted or issued a :
```
sudo mount -a
```

---

### Post by howett on 2012-06-21
Delayed by life. Back to fixing this issue.

net usershare info --long:
```

info_fn: file /var/lib/samba/usershares/{each drive/folder} is not a well formed usershare file.
info_fn: Error was Path not allowed.

```

I get 4 of those errors showing when running that command, with the "{each drive/folder}" I added representing each of the drives plus the media folder.

---

### Post by howett on 2012-06-21
Do you recommend any GUI for managing samba shares? I've done it manually, using Gadmin, and I'm trying recently Samba Server Config tool.

---

### Post by howett on 2012-06-21
So after removing the original share and sharing each drive individually, I have write access. So, it was something to do with that /media folder.

---

### Post by howett on 2012-06-21
[deleted]

---

