---
title: "Windows 7 &amp; Samba Help Please?!?"
date: 2011-11-30
forum: General Help
---

### Post by Mr. Cookie on 2011-11-30
Having issues getting Samba to work with Windows 7.

I am using XBMC live which has no window manager installed. All instructions must be terminal based please.

My setup:
XBMCLive (minimal ubuntu 10.04) installed on an 8GB USB stick
2TB internal SATA disk to store media on.
I have the 2TB disk mounted on /share
fstab entry:```
 /dev/sdc1 /share ntfs-3g defaults 0 0
``` 

smb.conf:
```
[share]
path = /share
guest ok =yes
read only = no
```

Now my win7 box can see the share and access files on it. However when I try to push any kind of file to it windows reports that there is not enough free space. df reports 1.2TB free space. 

After a bit of googling I found an issue where someone said that they fixed the issue by commenting out a line in the global section of smb.conf that read: ```
min receivefile size=128k
```

I figured I would take the entire posted smb.conf and edit the share to reflect my own needs. Again I got the same issue of not enough free space. I decided to try and uncomment that line and finally, I could transfer files. After trying to play the movie failed, I ran an md5sum and got different results on the win7 and XBMC box. The file was corrupted during transfer. 

I tried with a Ubuntu virtual machine and an android smartphone with no issues. The files transferred and MD5's matched. I tried a win7 virtual machine and got the same errors.

As a point of interest, I can see the shares from win7 I can even create folders and text documents in them. I just cant push files!?!?

**tl;dr** samba is either reporting a full disk or corrupting the transfers from Windows 7. Win7 can create folders and documents in the share without issue. Ubuntu/Android can push files correctly. My Configs are above.

Any ideas?

---

