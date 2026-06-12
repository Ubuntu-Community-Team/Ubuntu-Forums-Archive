---
title: "Need help with fstab entry for Dlink DNS-323 NAS device"
date: 2009-11-18
forum: General Help
---

### Post by tele_mark on 2009-11-18
I tried to post this in [this thread]("http://ubuntuforums.org/showthread.php?t=532996"), but the system isn't letting me, so I have to start one here. 

Like the OP of that thread, I'm trying to make an fstab entry for my Dlink dns-323 NAS box,so I can access it easily from applications that don't know about .gvfs . Unfortunately, I'm not having good luck like he did. 

This is the entry I made in fstab:

```
//DLINK-09AFB0/Volume_1     /mnt/dlinkNAS    smbfs    user,rw,sync,noauto,exec,uid=mark  0    0
```

And this is the error I'm seeing when I try to mount the share:

> mark@Dell1501:/etc$ mount /mnt/dlinkNAS
mount: wrong fs type, bad option, bad superblock on //DLINK-09AFB0/Volume_1,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so                    I've tried it with the ip address of the device instead of the name, and get the same result.
Can anyone steer me in the right direction?

---

### Post by sisco311 on 2009-11-18
smbfs is now depreciated for cifs: [http://linux-cifs.samba.org/]("http://linux-cifs.samba.org/") ( [thread=283131]How to fstab[/thread] )

this should help: [thread=288534]Mount samba shares with utf8 encoding using cifs[/thread]

---

### Post by kellemes on 2009-11-18
This is on e of my fstab-lines for connecting to a Synology ds207+
```
//IP_TO_NAS/shared_folder /mnt/dir cifs user,uid=1000,rw,suid,credentials=/etc/credentials 0 0
```

Where /etc/credentials is a file holding login-data for the NAS...
```
username=john
password=mypassword
```

You need to have "smbfs" installed.

---

### Post by tele_mark on 2009-11-18
> **sisco311 said:**
> smbfs is now depreciated for cifs: [http://linux-cifs.samba.org/](http://linux-cifs.samba.org/) ( [thread=283131]How to fstab[/thread] )

this should help: [thread=288534]Mount samba shares with utf8 encoding using cifs[/thread]

> **kellemes said:**
> This is on e of my fstab-lines for connecting to a Synology ds207+
```
//IP_TO_NAS/shared_folder /mnt/dir cifs user,uid=1000,rw,suid,credentials=/etc/credentials 0 0
```Where /etc/credentials is a file holding login-data for the NAS...
```
username=john
password=mypassword
```You need to have "smbfs" installed.


Thanks for the help! So, the smbfs option in fstab will no longer work in 9.10, and you should be using cifs?? I'm a new user -- I had 9.04 as a first install for a few days before 9.10 came out. Is smbfs installed by default, or do I have to  so on my system? I'm at work right now, so no access to my laptop. Is cifs something I have to install as well or is it installed when you install smbfs?

---

### Post by kellemes on 2009-11-18
> **tele_mark said:**
> (..) Is cifs something I have to install as well or is it installed when you install smbfs?

smbfs will provide this..
As far as I know it is not installed by default, so you have to..
```
sudo apt-get install smbfs
```

---

### Post by tele_mark on 2009-11-18
Thank you!! I'll report my results tonight.

Oh -- the NAS is open to all users on the network -- so do I leave the credentials file blank when I create it?

---

### Post by tele_mark on 2009-11-18
Ok, thanks again -- everything worked fine and I now have my DNS-323 auto mounted on my Dell 1501. I installed smbfs, modified nsswitch.conf, installed winbind, and modified the entry in fstab to  cifs as fstype. Quite a little education!

---

### Post by sisco311 on 2009-11-18
> **tele_mark said:**
> Ok, thanks again -- everything worked fine and I now have my DNS-323 auto mounted on my Dell 1501. I installed smbfs, modified nsswitch.conf, installed winbind, and modified the entry in fstab to  cifs as fstype. Quite a little education!

Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

EDIT: thanks!

---

### Post by LamaZ on 2009-12-02
For the record.  I was unable to mount this device until I modified the /etc/samba/smb.conf file on the Ubuntu machine.

things started to work when I added the following line in the [global] section:
```
client lanman auth = yes
```

[Here is the source of my reasoning.]("http://wiki.linuxmce.org/index.php/D-Link_DNS-323_How_To_Install_On_LMCE-810")

Symptoms were as follows, I could mount from Ubuntu to my vista share, but I could not mount from my Ubuntu machine to the DNS-323.  Also, to verify I could mount from the Vista machine to the DNS-323.  Ubuntu kept asking me for the password, over and over again.

I felt that I had to leave this posted somewhere for posterity.

Cheers,

LamaZ

---

