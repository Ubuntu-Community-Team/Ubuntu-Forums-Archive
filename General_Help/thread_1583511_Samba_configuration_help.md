---
title: "Samba configuration help"
date: 2010-09-27
forum: General Help
---

### Post by hirapanna on 2010-09-27
I have ubuntu server 10.4 installed on an Intel SS4200-E, which I have configured without any RAID. This machine acts as a media server to another PC. The other PC runs Windows 7 Ultimate. I have 3 1TB hard disks connected to it, and the file system on all the 3 are NTFS. I have mounted the hard disks as ntfs. I have made the folders on all the 3 hard disks shareable. I have configured Samba to make the folders on the hard disks "visible".

The ubuntu machine is in a headless configuration (it doesn't have any VGA card where can connect a monitor). I can configured SSH on it, so I can use putty from the Windows machine to logon to the ubuntu machine, but it is text based only.

I am able to see all the 3 disks from the Windows machine. I am able to read/write into 2 of the disks. I am able to read, copy and delete from the 3rd disk, **but not write new content to it**.

Following is the snippet from /etc/fstab:

```
/dev/sda3 /media/Media1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sdb1 /media/Media2 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sdc1 /media/Media3 ntfs-3g defaults,locale=en_US.utf8 0 0

```

Following are the lines which I have added to the end of /etc/samba/smb.conf:

```
[Media1]
   path = /media/Media1
   writable = yes
   guest ok = yes


[Media2]
   path = /media/Media2
   writable = yes
   guest ok = yes


[Media3]
   path = /media/Media3
   writable = yes
   guest ok = yes
```

Any help in resolving this issue would be greatly appreciated.

---

### Post by robsoles on 2010-09-28
Welcome to UF.

It is odd that you can delete from the third drive but cannot write a file to it, normally deletion rights indicates write rights and it takes a proper 'users and permissions' file-system to set up what is happening for you.

Would you please copy and paste back the output from
```
ls /media -al
```

---

### Post by hirapanna on 2010-09-28
Following is the output:


> /media:
total 80
drwxr-xr-x  5 root root 4096 2010-08-28 15:40 .
drwxr-xr-x 22 root root 4096 2010-08-08 02:01 ..
drwxrwxrwx  1 root root 4096 2010-09-28 07:04 Media1
drwxrwxrwx  1 root root 4096 2010-09-25 17:09 Media2
drwxrwxrwx  1 root root 4096 2010-09-27 07:12 Media3


---

### Post by robsoles on 2010-09-28
Please show me error message or other output of following command
```
ls >> /media/Media3/testperms.txt
```

---

### Post by hirapanna on 2010-09-28
Am at work at the moment, would post the output once I reach home in the afternoon.

---

### Post by hirapanna on 2010-09-28
Following are the contents of testperms.txt file:

```
Desktop
Documents
Downloads
examples.desktop
Music
Pictures
Public
Templates
Videos

```

Once I login into the ubuntu box from Windows using putty, I don't have any problem in read/write/delete any file. Problems are from the windows box using windows My Computer (after mapping a drive to the respective folder)

---

### Post by robsoles on 2010-09-28
On windows PC click 'start' and enter 'cmd' into search/run box, press [Enter] if a DOS terminal opens then proceed otherwise complain back to me.

You need to replace where I use 'server' below to use the 'friendly' name of the Samba Server
```
net use k: \\server\media3
```
(may ask for 'admin' password for Windows 7 here, may not - am not that familiar with Windows 7)
```
echo testing raw perms >> k:\test2.txt
```
The specific way it reports 'permission denied' may hold a clue for us, at least that is what I am trying now.

---

### Post by hirapanna on 2010-09-28
Surprising results here (results are after invoking the command prompt, without Admin rights):


```
New connections will be remembered.


Status       Local     Remote                    Network

-------------------------------------------------------------------------------
OK           P:        \\Server_Name\Media1   Microsoft Windows Network
OK           Q:        \\Server_Name\Media2   Microsoft Windows Network
OK           R:        \\Server_Name\Media3   Microsoft Windows Network
The command completed successfully.

```
As mentioned before, I have mapped the 3 hard disks to windows. R: is the problematic drive.

Surprisingly, I don't see any error while creating the test2.txt file. When I open the folder using My Computer, I see the file test2.txt created, and the contents are there.

So the question becomes, why is My Computer behaving differently?

---

### Post by robsoles on 2010-09-28
Difficult to fathom but if you like you could 'follow' the /var/log/samba/smbd.log file while you try different operations on each of the mapped drives and it may provide clues (in terminal on server PC)
```
tail -f /var/log/samba/smbd.log
```

Other logs in the /var/log/samba folder may hold clues to this as may /var/log/messages and even a couple of other logs in the /var/log folder.

Personally I'd blame Windows 7 because umpteen instances of samba doing anything from simple file share through to full-on domain controller just hasn't given me that sort of result without a clear permissions issue I had to fix.

---

### Post by hirapanna on 2010-09-28
One of the logs in /var/log/samba has:

```
  desktop-pc (::ffff:192.168.1.6) connect to service Media1 initially as user nobody (uid=65534, gid=65534) (pid 1893)
[2010/09/28 15:42:18,  1] smbd/service.c:1063(make_connection_snum)
  desktop-pc (::ffff:192.168.1.6) connect to service Media2 initially as user nobody (uid=65534, gid=65534) (pid 1893)
[2010/09/28 15:42:18,  1] smbd/service.c:1063(make_connection_snum)
  desktop-pc (::ffff:192.168.1.6) connect to service Media3 initially as user nobody (uid=65534, gid=65534) (pid 1893)
[2010/09/28 15:57:17,  0] smbd/nttrans.c:2119(call_nt_transact_ioctl)
  call_nt_transact_ioctl(0x900eb): Currently not implemented.

```

This suggests that Windows is logging into the ubuntu machine as a guest. Is there a way to verify the username used by windows while connecting to the ubuntu server?

Also found something interesting while trying out the copy from My Computer - when I try copying the file which I just created (using the console via putty), I am able to do so. Am not able to copy files which were already on the hard disk before.

Created a folder from the console, and tried copying a few files to it using My Computer - no luck. As expected, am able to copy files to it from the console.

---

