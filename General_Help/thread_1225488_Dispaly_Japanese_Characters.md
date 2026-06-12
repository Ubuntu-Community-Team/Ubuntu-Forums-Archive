---
title: "Dispaly Japanese Characters"
date: 2009-07-28
forum: General Help
---

### Post by dwanders on 2009-07-28
Using 
Ubuntu 9.04
rsync version 3.0.5-1ubuntu2
samba-common 2:3.3.2-1ubuntu3
nfs-common 1:1.1.4-1ubuntu1
backuppc 3.1.0-4ubuntu1

I am experimenting with BackUpPC and I was hoping some one could shed some light on an issue I have been experiencing for many years. As the title states, it has to do with Japanese Characters begin displayed correctly - and I know this is a very complicated issue, but nevertheless, I hope some one may have an answer:

how is it, that when I browse to a network share (Windows) from Ubuntu using places everything displays fine (based on the Location: smb://windowsserver ... I cleverly deduce it is using Samba or a samba client of some kind. 

And when I try to use nfs to mount the same folder, I get nothing but ???'s and garbage for the character display. I have tried changing the encoding on the NFS servers (W2003) share from ANSI to EUC-JP or Shift-JIS and still get garbage characters on the Linux side. 

Is it possible to get both these technologies (SMB and NFS) to display the same character set correctly each time? I have Read on the BackUpPC web site that using rsync is a better methodology than SMB and would like to use it if possible - but this character issue kinda puts a kibosh on the works. 

Thanks,

---

### Post by dwanders on 2009-07-29
Nobody? Huh - I found the System > Administration > Language Support and installed the support for Japanese - I even set my logon to use Japanese rather than English and the results was the same, if I mount a file system with nfs - the encoding becomes ?????? rather than Japanese as it should be. 

I even tried mounting with cifs instead of nfs e.g.:

```
/sbin/mount.cifs //WindowsServerc/CORP /mnt/corp -o username=username,password=password,uid=username,gid=username,file_mode=0640,dir_mode=0750,isocharset=utf8 2>&1
```

After looking at that mount command I have been using, would changing the isocharset to something else make a difference? if so what could I change it to? 

But even after mounting a cifs - I got the ????? I am guessing that when I use Nautilus to browse the file systems on the network - it is using smbclient or something else to display things correctly either that or the gvfs or something is able to handle things better - it is very confusing and frustrating that I cannot get the characters to display correctly so I can back the data up. 

Any assistance with this matter is greatly appreciated.   

Thanks in advance.

---

