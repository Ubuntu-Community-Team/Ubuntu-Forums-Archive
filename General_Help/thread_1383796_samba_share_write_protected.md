---
title: "samba share write protected"
date: 2010-01-17
forum: General Help
---

### Post by titanicmusic14 on 2010-01-17
Remove the write protection or use another disk. I have changed the samba share as much as possible. What should I do in the ubuntu file system to fix this error. this is an xp generated error.

---

### Post by Morbius1 on 2010-01-17
Not a whole lot to go on there. What method of sharing are you using?
What are you sharing? An internal directory or an external usb device?

Let's start with th basics:

Please post the output of the commands from the Terminal:

[B]net usershare info
testparm -s[/B]

---

### Post by titanicmusic14 on 2010-01-17
> **Morbius1 said:**
> Not a whole lot to go on there. What method of sharing are you using?
What are you sharing? An internal directory or an external usb device?

Let's start with th basics:

Please post the output of the commands from the Terminal:

[B]net usershare info
[/B]


[upload]
path=/home/FTP-shared/upload
comment=
usershare_acl=Everyone:R,
guest_ok=y


[B]testparm -s

oad smb config files from /etc/samba/smb.conf
Processing section "[print$]"
WARNING: No path in service print$ - making it unavailable!
NOTE: Service print$ is flagged unavailable.
Processing section "[printers]"
WARNING: [printers] service MUST be printable!
WARNING: No path in service printers - making it unavailable!
NOTE: Service printers is flagged unavailable.
Processing section "[upload]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    netbios name = PENILE
    server string = %h Ubuntu
    interfaces = lo, eth0
    bind interfaces only = Yes
    passdb backend = tdbsam
    username map = /etc/samba/smbusers
    syslog only = Yes
    announce version = 5.0
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS
    wins support = Yes
    invalid users = root

[print$]
    available = No

[printers]
    printable = Yes
    browseable = No
    available = No

[upload]
    comment = Unique's Buntu
    path = /home/FTP-shared/upload
    valid users = @sambashare
    read list = @sambashare
    write list = negrobuntu
    read only = No

THANKS!!!

[/B]

---

### Post by Morbius1 on 2010-01-17
Let's start with the most obvious problem:

Nautilus-share says this:
> [upload]
path=/home/FTP-shared/upload
comment=
usershare_acl=Everyone:R,
guest_ok=yClassic Samba says this:
> [upload]
    comment = Unique's Buntu
    path = /home/FTP-shared/upload
    valid users = @sambashare
    read list = @sambashare
    write list = negrobuntu
    read only = NoYou have a very complicated smb.conf so I would suggest getting rid of the nautilus-share share:

Open **Terminal**
Type **net usershare delete upload**
Type[B] sudo service samba restart

[/B][COLOR=Blue]This will remove the nautils-share share not the smb.conf share.

[COLOR=Black]It's probably too much to hope that this will fix everthing so I need to see what the permissions are on [/COLOR][/COLOR]/home/FTP-shared/upload[COLOR=Blue]:

**[COLOR=Black]ls -dl[/COLOR] **[/COLOR]**/home/FTP-shared/upload**
[COLOR=Blue]

[/COLOR]

---

### Post by blueridgedog on 2010-01-17
What are the permissions of /home/FTP-shared/upload?

Can you post the output of:

```
cd /home/FTP-shared/
ls -al

```

I suspect you need to make /home/FTP-shared/upload world writable with:
```

sudo chmod 777 /home/FTP-shared/upload
```

---

### Post by titanicmusic14 on 2010-01-17
> **Morbius1 said:**
> Let's start with the most obvious problem:

Nautilus-share says this:
Classic Samba says this:
You have a very complicated smb.conf so I would suggest getting rid of the nautilus-share share:

Open **Terminal**
Type **net usershare delete upload**
Type[B] sudo service samba restart

[/B][COLOR=Blue]This will remove the nautils-share share not the smb.conf share.

[COLOR=Black]It's probably too much to hope that this will fix everthing so I need to see what the permissions are on [/COLOR][/COLOR]/home/FTP-shared/upload[COLOR=Blue]:

**[COLOR=Black]ls -dl[/COLOR] **[/COLOR]**/home/FTP-shared/upload**
[COLOR=Blue]


[/COLOR]

[COLOR=Blue]**[COLOR=Black]ls -dl[/COLOR] **[/COLOR]**/home/FTP-shared/upload**
[COLOR=Blue]
[/COLOR]
[COLOR=Blue]drwxrwxr-- 9 negrobuntu negrobuntu 12288 2010-01-16 23:37 /home/FTP-shared/upload[/COLOR]

---

### Post by titanicmusic14 on 2010-01-17
> **blueridgedog said:**
> What are the permissions of /home/FTP-shared/upload?

Can you post the output of:

```
cd /home/FTP-shared/
ls -al

```I suspect you need to make /home/FTP-shared/upload world writable with:
```

sudo chmod 777 /home/FTP-shared/upload
```

root@negrobuntu-desktop:/home/FTP-shared#** ls -al**
total 24
drwxrwxrwx  3 negrobuntu sambashare  4096 2010-01-17 17:08 .
drwxr-xr-x 10 root       root        4096 2010-01-14 20:59 ..
drwxrwxr--  9 negrobuntu negrobuntu 12288 2010-01-16 23:37 upload
-rw-r--r--  1 negrobuntu negrobuntu   502 2009-12-18 01:16 vlc_vod_config~

---

### Post by titanicmusic14 on 2010-01-17
I also typed in this:  no change ... Cannot .... The disk is write-protected. Remove the write-protection or use another disk
sudo chmod 777 /home/FTP-shared/upload[/CODE][/QUOTE]

---

### Post by Morbius1 on 2010-01-17
Did you get rid of the nautilus share because it's set to read only:

> Open **Terminal**
Type **net usershare delete upload**
Type** sudo service samba restart**

---

### Post by titanicmusic14 on 2010-01-17
> **Morbius1 said:**
> Did you get rid of the nautilus share because it's set to read only:

Yes typed it in .. is there a way to double check?

---

### Post by Morbius1 on 2010-01-17
Just issue this command again:

**net usershare info**

It should be empty.

---

### Post by titanicmusic14 on 2010-01-17
I'm just gonna download swat . The gui for samba. Its useless getting help for samba on here.

---

### Post by titanicmusic14 on 2010-01-17
> **titanicmusic14 said:**
> I'm just gonna download swat . The gui for samba. Its useless getting help for samba on here.
I take that back ... Swat is just as useless. ..

---

### Post by blueridgedog on 2010-01-18
> **titanicmusic14 said:**
> root@negrobuntu-desktop:/home/FTP-shared#** ls -al**
total 24
drwxrwxr--  9 negrobuntu negrobuntu 12288 2010-01-16 23:37 upload


Your upload directory lacks write permissions for "other".  Currently it is RWXRWXR--.

```
sudo chmod 777 /home/FTP-shared/upload -R
```

---

### Post by Morbius1 on 2010-01-18
How are you accessing the Linux share from Windows?

And is this the error you're receiving in windows ( see attachment ). The reason I mention this is that I have never seen that error before when using samba. If it were a linux permissions error you'd think that windows would say something like "access denied" or "you do not have permissions" or something like that. 

It really looks to me as a local windows client issue not a samba server issue.

Also, you've been asked to do a chmod several times now. If the permissions haven't changed to 777 is 
/home/FTP-shared/upload a mount point for a FAT32 or NTFS partition.

---

