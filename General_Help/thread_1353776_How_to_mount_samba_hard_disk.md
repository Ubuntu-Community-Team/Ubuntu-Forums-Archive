---
title: "How to mount samba hard disk?"
date: 2009-12-13
forum: General Help
---

### Post by miros84 on 2009-12-13
Hello.
I have a network samba hard disk. I can access it by typing 
smb://mirosred1 in my browser.
But what I want to do is, mount it in the /mnf folder.
SO, I type 
```
mount -t vfat smb://mirosred1/ /mnt/mirosred1

```
but I get this errror. The samba dispositive doesnot exist.
And I know that it exists, because I can enter in.
Ane help to ca mount it?

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by tele_mark on 2009-12-13
The short of it -- try changing vfat to cifs. I had the same problem with my Dlink NAS until I did that.

---

### Post by miros84 on 2009-12-13
Hi

I tried this
//servername/sharename  /media/mountname  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

but it doesnot work for me.
FOr me, the only way to access the network samba HDD is to type that:
smb://mirosred1

Other solutions?

---

### Post by miros84 on 2009-12-13
> **tele_mark said:**
> The short of it -- try changing vfat to cifs. I had the same problem with my Dlink NAS until I did that.

Hi

It tells me that it doesnot find the host and the Ip adress.

But I do can access my HDD by typing smb://mirosred1

I didnot understund where is the problem.

---

### Post by miros84 on 2009-12-13
If i try that:

```
//192.168.0.200  /mnt/mirosred1  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

I get this error when I try to mount:

```
Miros-main:/home/miros# mount -a
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
Mounting the DFS root for a particular server not implemented yet
No ip address specified and host
```

Wait for your help.

---

### Post by tele_mark on 2009-12-13
> **miros84 said:**
> Hi

It tells me that it doesnot find the host and the Ip adress.

But I do can access my HDD by typing smb://mirosred1

I didnot understund where is the problem.

That's over my head bud, I've been using Ububtu for two months. Hopefully someone will be along soon with skills and a solution. I do remember that in addition to the above, I had to do something to enable netbios resolving, maybe [this]("http://ubuntuforums.org/showthread.php?t=88206")?

Seems strange you're able to use the share name with the smb command though.

---

