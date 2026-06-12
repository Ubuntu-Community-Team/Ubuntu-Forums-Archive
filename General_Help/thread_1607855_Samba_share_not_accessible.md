---
title: "Samba share not accessible"
date: 2010-10-28
forum: General Help
---

### Post by New00Folder on 2010-10-28
I'm running Ubuntu 10.04 and Samba 4. The folder I've shared is on NTFS partition and though is visible from other Windows 7 system on LAN, it can't be browsed. Even from my own computer if go to network places the folder is there but when I double click on it I get

Unable to mount location
Failed to mount windows share

---

### Post by luvshines on 2010-10-28
Howdy, Delhite !! Cheers :)

I would recommend to downgrade to Samba 3.

Also, from terminal try this(to get some better error logs):
```
smbclient //<server-ip>/<shared-path> -U<username>%<passwd>
```

Also, make sure that the shared directory and all the directories starting from / upto this shared one have read permissions for the user who is trying to access the shares

---

### Post by New00Folder on 2010-10-29
I put IP of gateway (192.168.15.1) instead of <server-ip> and path of the folder instead of <shared-path>.
```
smbclient //192.168.15.1/media/d/Cartoons -U<username>%<passwd>
```Output:
Connection to 192.168.15.1 failed (Error NT_STATUS_HOST_UNREACHABLE)

I even tried my IP on LAN.
```
smbclient //192.168.15.111/media/d/Cartoons -U<username>%<passwd>
```Output:
session setup failed: NT_STATUS_LOGON_FAILURE

There's a strange thing about the shared folder. It's on a NTFS partition which is auto-mounted at start-up on /media/d and it's owner is root. It's permissions are drwxrwx---. Though I can change owner of /media using "sudo chown" to <username>, the same command can't change the owner of /media/d and for that matter any other file or folder inside it. Similar thing happens when I try "sudo chmod a=x" for the folders. No error message whatsoever. And all the while I can still access a system (not all) on LAN and copy shared files from it.

I'm clueless.

---

### Post by luvshines on 2010-10-29
> **New00Folder said:**
> 
I even tried my IP on LAN.
```
smbclient //192.168.15.111/media/d/Cartoons -U<username>%<passwd>
```Output:
session setup failed: NT_STATUS_LOGON_FAILURE

There's a strange thing about the shared folder. It's on a NTFS partition which is auto-mounted at start-up on /media/d and it's owner is root. It's permissions are drwxrwx---. Though I can change owner of /media using "sudo chown" to <username>, the same command can't change the owner of /media/d and for that matter any other file or folder inside it. Similar thing happens when I try "sudo chmod a=x" for the folders. No error message whatsoever. And all the while I can still access a system (not all) on LAN and copy shared files from it.

I'm clueless.

Did you provide a valid username and passwd with -U option ?
Can you provide output for```
testparm -sp
```

---

### Post by New00Folder on 2010-10-30
Yes, I did enter username with -U and leaving a space after U.
Output of testparm -sp
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section &quot;[printers]&quot;
Processing section &quot;[print$]&quot;
Processing section &quot;[Cartoons]&quot;
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
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

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    valid users = nobody, voldemort

[Cartoons]
    path = /media/d/Cartoons
    guest ok = Yes

```

---

### Post by Morbius1 on 2010-10-30
Your share looks like this and allows guest access:
> [Cartoons]
    path = /media/d/Cartoons
    guest ok = YesHowever:
> It's on a NTFS partition which is auto-mounted at start-up on /media/d and it's owner is root. It's permissions are drwxrwx---.Those last 3 "---" are the permissions for "other" and a "guest" is a "other".

Since it's automounted you will have to modify the line in fstab that automounts it to allow "others" to gain access.

Post your fstab so we can see how it's set up:
> cat /etc/fstab

Note: chown and chmod are for linux filesystems not windows filesystems which is why your use of them had no affect.

---

### Post by New00Folder on 2010-10-30
I kind of see the light now. I changed the *umask* for the mounting folder to 005 (r-x for others, right?) from 007 in the *fstab* file. Or should I just remove the *umask* part so that instead of entire drive having read permission for others I would be be able to set read permissions only for folders I want to be shared perhaps after start-up. But *chmod* wouldn't work. I'll try and see how things work out. Here's the (uncorrected) line in fstab.
```
/dev/sda5    /media/d    ntfs    defaults,umask=007,gid=46,noatime
```[B]

And thanks a lot for your time!![/B]

---

### Post by luvshines on 2010-10-31
> **New00Folder said:**
> I kind of see the light now. I changed the *umask* for the mounting folder to 005 (r-x for others, right?) from 007 in the *fstab* file. Or should I just remove the *umask* part so that instead of entire drive having read permission for others I would be be able to set read permissions only for folders I want to be shared perhaps after start-up. But *chmod* wouldn't work. I'll try and see how things work out. Here's the (uncorrected) line in fstab.
```
/dev/sda5    /media/d    ntfs    defaults,umask=007,gid=46,noatime
```[B]

And thanks a lot for your time!![/B]

If you use umask of 005, won't you get permissions of 777-005=772, ie, only writeable drwxrwx-w- for others ?
The default system 022 umask should be good, drwxr-xr-x permissions. But I think you have put gid=46 and w for that, maybe as per your requirement
Try using 002 too :)

---

### Post by New00Folder on 2010-10-31
You're right. Permissions for folders are inverted. Things have worked out fine.

Thanks a lot again.

---

### Post by luvshines on 2010-10-31
> **New00Folder said:**
> You're right. Permissions for folders are inverted. Things have worked out fine.

Thanks a lot again.

Fundoo!! Nice to know that it worked

Don't forget to mark this thread **SOLVED** :)

And Happy Diwali :D

---

### Post by Morbius1 on 2010-10-31
luvshines, I've been meaning to ask you about the "p" parameter in testparm. What does it do? I can't find it in man testparm and when I run it with ( testparm -sp ) and without "p" ( testparm -s ) it seems to make no difference.

---

### Post by New00Folder on 2010-10-31
And a very happy diwali to you too.

---

