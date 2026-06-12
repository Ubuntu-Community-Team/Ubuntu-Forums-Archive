---
title: "Samba share lockup"
date: 2006-03-05
forum: General Help
---

### Post by tmkly3 on 2006-03-05
I am successfully able to mount a network directory on ubuntu breezy, however the terminal locks whenever I do anything but cd or ls.

I mount with: ```
sudo smbmount //rosetta.ics.purdue.edu/user /mnt/mentor -o username=user,password=pass,fmask=755,dmask=755,rw
```

This successfully mounts the drive and I can ls it's contents in /mnt/mentor, however if I attempt to do say cat /mnt/mentor/example the terminal freezes.

/etc/mtab contains:
```
//rosetta.ics.purdue.edu/user /mnt/mentor smbfs rw 0 0
```

If I open a new terminal and attempt to unmount it returns: ```
 /mnt/mentor: device is busy
```

Does anyone have any suggestions as to the nature of the problem? I've tried mounting via /etc/fstab and the same problem occures. Thanks.

---

