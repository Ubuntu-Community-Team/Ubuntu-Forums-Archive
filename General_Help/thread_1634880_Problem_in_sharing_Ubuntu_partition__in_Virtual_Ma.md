---
title: "Problem in sharing Ubuntu partition  in Virtual Machine"
date: 2010-12-01
forum: General Help
---

### Post by drdigital on 2010-12-01
Hello every one,
I'm using Ubuntu 10.10 and I have a problem in sharing windows (NTFS) partitions to be shown in Virtual Machine (Virtual Box).

I can share folders in ubuntu system folders without problems but when I try to share folders inside NTFS partitions I cant.
at first: msg: cant execute child process testparam. I came across some posts and installed samba and now different error msg

samba's testparm returned error 1

Can any one help me on this ?
I'm not a professional user.

Thanks so much.

---

### Post by runeh76 on 2010-12-01
> **drdigital said:**
> Hello every one,
I'm using Ubuntu 10.10 and I have a problem in sharing windows (NTFS) partitions to be shown in Virtual Machine (Virtual Box).

I can share folders in ubuntu system folders without problems but when I try to share folders inside NTFS partitions I cant.
at first: msg: cant execute child process testparam. I came across some posts and installed samba and now different error msg

samba's testparm returned error 1

Can any one help me on this ?
I'm not a professional user.

Thanks so much.

Virtualbox make default 10gb partition to ur hd. U cant share there ur other hd contest becouse virtualbox doesnt see ur real win/linux files. U can drop files there with usb-stick.

---

