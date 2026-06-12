---
title: "Network File Permissions"
date: 2009-11-10
forum: General Help
---

### Post by CrusaderAD on 2009-11-10
I'm having an issue with file permissions over the network. I'll map a drive using Nautilus' network feature and log into the drive using the correct user name and password. I can browse the files and open them just fine. If I change anything in the file and save it, the permissions get changed and I can't open it back up again. It says that it can't determine the the permissions. I know that the user I am logging in with has full permissions on these drives. Any ideas?

---

### Post by alphaniner on 2009-11-10
Try doing things 100% from the command line and see if you get the same results.

The easiest first step, I think, would be to log in to the share with smbclient and copy a file over.

```
smbclient \\\\<IP>\\<share> -U=<username>
```

Depending on how that goes, move on to mounting the share and editing a file with vi.

---

### Post by CrusaderAD on 2009-11-11
When logged into the samba drive, what commands can I use? Things like cp, copy, nano, vi do not work.

---

### Post by alphaniner on 2009-11-11
smbclient is limited, it works like an ftp client.  AFAIK you can't edit files, only transfer to/from the share.  Before connecting, change to a directory with some files you can transfer.  Then connect.  To copy files (from pwd) to the share, use **put *file***.  To copy files from the share, use **get *file***.  You can see all the commands by entering **help**, but there's no description.

---

### Post by CrusaderAD on 2009-11-12
When trying to "get" a file, I get this error in the command line:

```
NT_STATUS_ACCESS_DENIED opening remote file \folder\file.txt
```

When I mount the drive and open the file, I get a permissions error in gedit (in a red bar) or nothing at all in vi. I also get permission denied in nano.

---

### Post by lykwydchykyn on 2009-11-12
Since it sounds like the problem may be a configuration issue on the server, it might help to know some things about the server: 

 - What OS is it running?
 - What are the local file permissions/owner on the share?
 - If it's Linux, post the smb.conf file from the server.

---

### Post by CrusaderAD on 2009-11-13
It's a Windows 2003 Server and I have checked to make sure that the permissions are set on the share I am accessing with the user I'm connecting with. The weird thing is that I have several 9.04 Ubuntu systems connecting with the same credentials the same way and they do not have an issue.

---

### Post by CrusaderAD on 2009-11-15
Bump

---

### Post by mr clark25 on 2009-11-15
if you don't have any other people trying to access your files on your network, you might try checking the box "allow guest access" i was having issues to,(i don't use a server) and that fixed it.

---

### Post by CrusaderAD on 2009-11-17
Thanks for the replies. Can you guys take a look at the attached screen shot? This is what the folder's permissions are set to on the client machine. I did make sure I have open permissions on the host machine.

---

### Post by CrusaderAD on 2009-11-17
I'm not sure if it will stay working... but mounting the file shares through Place > Network seems to work. It's doesn't seem to reset the file permissions when I save, exit, and re-open the file. Must have been a bug they worked out. Mounting through Fstab still doesn't work.

---

