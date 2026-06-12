---
title: "files vanished, determine how or by whom"
date: 2010-01-22
forum: General Help
---

### Post by pbrille on 2010-01-22
Files on my ubuntu fileserver vanished.
How did that happen or by whom?
I supsect unauthorized access but I can't except a mulfunction since this NFS and SMB server acts for several PCs but only me and 1 other person are authorized. There are also some additional services running like avahi or daapd.

Please help me find out when the last accesses to a specific folder happened and by whom. Or is there a "better" method for me to find facts. Maybe files have been moved accidentally...
How do I find out?

---

### Post by c0mput3r_n3rD on 2010-01-22
> **pbrille said:**
> Files on my ubuntu fileserver vanished.
How did that happen or by whom?
I supsect unauthorized access but I can't except a mulfunction since this NFS and SMB server acts for several PCs but only me and 1 other person are authorized. There are also some additional services running like avahi or daapd.

Please help me find out when the last accesses to a specific folder happened and by whom. Or is there a "better" method for me to find facts. Maybe files have been moved accidentally...
How do I find out?


I'm not to do what you're asking, but I think you need to check your file permissions, because unless some body hacked into your computer, or your password is weak and some body was able to guess it, then the permissions of your files were not appropriate.  Are you familiar with the chmod and chown commands?

---

### Post by pbrille on 2010-01-23
> **c0mput3r_n3rD said:**
> I'm not to do what you're asking, but I think you need to check your file permissions, because unless some body hacked into your computer, or your password is weak and some body was able to guess it, then the permissions of your files were not appropriate.  Are you familiar with the chmod and chown commands?

I totally Am and my computer does not have a public reachable IP-address though the host can be reached on specific ports by doing DNAT i.e. Apache, openssh, vsftpd (80,22,21).
I closed them now, for security. Maybe my wireless network has been cracked. But If so, my fileshare password must have been hacked, too. Both passwords differ. Oh no, I also use NFS which allows write access when the host has a local address. Will close that now, too and change WPA2 key.
But honestly, how can I figure out how that happened? Isn't there anny logging, like the journaling of the filesystem (ext3)???

Edit: My password security is like medium. Additionally I used chkrootkit and rkhunter but everything seems fine.
Some additional infos to my storing technique:
4 * 1 TB HDD as softare RAID 5 with lvm on top. The logical volumes are used within xen domUs.

---

### Post by pbrille on 2010-01-25
Update:
I checked the volume with fsck, no erros.
The lvm volume is around 1.7 TB of size. It's been nearly full, now I resized the volume and it's around 100 GB free space available. I don't know if that has something to do with it.
I doubt the files vanished by user interaction. I really suspect some kind of malfunction. I reviewed /etc/syslog but couldn't find anything helpful.

Isn't there any possibility for me how to figure out when exactly the files vanished and by which process or user?

---

