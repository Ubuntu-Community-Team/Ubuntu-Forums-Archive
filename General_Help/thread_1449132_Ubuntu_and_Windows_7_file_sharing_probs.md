---
title: "Ubuntu and Windows 7 file sharing probs"
date: 2010-04-07
forum: General Help
---

### Post by the lemming on 2010-04-07
A while back I had problems sharing files between Windows 7 and Ubuntu but somehow I solved the problem.  I did nothing different apart from re-install Ubuntu onto the laptop.  At the time I was able to share filed from Windows 7 to Ubuntu but not the other way round but I could live with this.

last week I had a spring clean of my computers by re-installing Windows7 on one computer and re-installing Vista and Ubuntu onto the laptop.

Now that I have done this I DO NOT have the ability to share files.  Every time I try to access the desktop from the Network I keep getting asked for a password.

Anybody know what I need to do to share files as my little brain hurts?

---

### Post by the lemming on 2010-04-10
Bump

---

### Post by oldfred on 2010-04-10
the best way is to permanently mount it with whatever permissions you want.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

After you understand some of the settings:
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)

This is my entry where I created shared a mount point in my home as that was where I wanted to see it.
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0

---

### Post by the lemming on 2010-04-11
> **oldfred said:**
> the best way is to permanently mount it with whatever permissions you want.





Sorry my mistake as I have not described myself accurately.  

I am trying to share files over a home network of two computers.

---

### Post by oldfred on 2010-04-11
I have some links but frankly I gave up. I have a portable that was windows and a desktop Ubuntu. Just about every fix from windows and every 6 month update to Ubuntu did something to my sharing. I just went back and installed Karmic to my portable and use NFS to share.

I believe there are two ways and you do not want to mix them as that causes confusion.

Howto: Fix Windows share browsing issues 
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
Sharing issues
[http://ubuntuforums.org/showthread.php?t=1374369](http://ubuntuforums.org/showthread.php?t=1374369)

 HOWTO: Setup Samba peer-to-peer with Windows 
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
For definitive explanation of SMB (CIFS) and how it works, see here .
[http://ubiqx.org/cifs/SMB.html](http://ubiqx.org/cifs/SMB.html)


[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

