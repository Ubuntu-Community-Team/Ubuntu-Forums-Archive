---
title: "Samba Problems (9.10 Karmic)"
date: 2009-11-21
forum: General Help
---

### Post by Jayy on 2009-11-21
Hello,
I'm trying to share files from my Ubuntu computer with other computers on my network. When I do it off the Live CD it works great. But when I try to do it on a real install, with the exact same settings as the Live CD, it doesn't work. When I try to access the Ubuntu computer over my network from one of my other computers it gives me the following error:

[B]"\\Ubuntu\documents is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The network path was not found."[/B]


Thanks,
Jay

---

### Post by Jayy on 2009-11-21
Bump.

---

### Post by Goggeli on 2009-11-21
Hello!

What kind of OS are you running on the other machines in your network? As you might know, Ubuntu 9.10 is running the ext4 file-system. I might be wrong but I do think that systems that are running ext3 or earlier file-systems are not compatible with ext4.

---

### Post by Jayy on 2009-11-21
xp pro 32bit, xp pro 64bit, and mac os 10.5. I actually am using ext3, not ext4, but I've tried both. The interesting thing is that it works on the live cd and live usb...

---

### Post by Iowan on 2009-11-21
Samba *should* make the underlying file system transparent. *Might* be a permissions thing.  Is security set for user or share?

---

### Post by Jayy on 2009-11-26
I'm not sure...

---

### Post by Charlietje on 2009-11-26
Please post your smb.conf file

and how you are trying to connect to your ubuntu system. (map network or directly)

Can you ping your ubuntu server?

---

