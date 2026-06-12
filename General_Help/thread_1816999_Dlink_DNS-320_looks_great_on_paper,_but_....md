---
title: "Dlink DNS-320 looks great on paper, but ..."
date: 2011-08-02
forum: General Help
---

### Post by Losergamer04 on 2011-08-02
I'm running into an issue and I was hoping someone else on this forum could point out what I'm missing.

I purchased a Dlink DNS-320 NAS box for my Boxee Box and Ubuntu file sharing/backups.  I've been using cifs to communicate with it but I tire of this slow connection.  I've read NFS is much faster but I have yet to get it working.  

```
sudo mount -t cifs 192.168.0.100:/Volume_1 /mnt
```The above command works. I had installed the smbfs (or something like that) package to get it to work.  But, when I sub nfs for cifs I get :
```
mount: wrong fs type, bad option, bad superblock on 192.168.0.100:/Volume_1,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```What (simple?) thing am I missing to get this to work?

---

### Post by dcstar on 2011-08-03
> **Losergamer04 said:**
> I'm running into an issue and I was hoping someone else on this forum could point out what I'm missing.

I purchased a Dlink DNS-320 NAS box for my Boxee Box and Ubuntu file sharing/backups.  I've been using cifs to communicate with it but I tire of this slow connection.  I've read NFS is much faster but I have yet to get it working.  
.........

NFS **only** works on NFS file servers, Samba based NAS devices are **not** NFS devices.

---

### Post by Losergamer04 on 2011-08-03
The product claims NFS support but I wouldn't be surprised if that was a  lie.  It does have a setting to turn NFS and the Apple equivalent on,  which I have done.

Long story short, if the CIFS mount worked, and NFS was supported, I  should be able to mount it using NFS, correct?  It seems as though my  issue lies with the manufacture.

I tend to look in the mirror before I point the finger.  Thanks for the help.

---

### Post by nipennem on 2011-08-03
> **Losergamer04 said:**
> The product claims NFS support but I wouldn't be surprised if that was a  lie.  It does have a setting to turn NFS and the Apple equivalent on,  which I have done.

Long story short, if the CIFS mount worked, and NFS was supported, I  should be able to mount it using NFS, correct?  It seems as though my  issue lies with the manufacture.

I tend to look in the mirror before I point the finger.  Thanks for the help.

I think you need to configure NFS and Samba/CIFS separately in the NAS. I own a DNS-323 and my Samba users do not necessarily have FTP access, Samba has shares, in FTP you set root folders for users, etc. NFS setup will be different again. Did you already configure anything else beyond just enabling NFS or are there no such options?

Edit: Googled the DNS-320 manual and there is a per-user setting to enable NFS access. No comments on how to connect / how to set it up though. Surely you have a problem with the manufacturer, and more specifically with their worthless documentation.

---

### Post by jby601 on 2013-01-22
This link may help:
<http://www.jwandrews.co.uk/2011/11/166/>

---

