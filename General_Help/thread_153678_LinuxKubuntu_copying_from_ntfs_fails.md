---
title: "Linux/Kubuntu copying from ntfs fails"
date: 2006-04-01
forum: General Help
---

### Post by duffydack on 2006-04-01
I`m gettin "protocol died" error message when tryin to copy all my Mp3`s on my ntfs external hd.......to my reiser on the same external....

its makin me shutdown by switchin off...  it wont shutdown/reboot.. just takes me to a console login,  (no a shutdown -F wont work either) it wont unmount the external partition its copyin to, nor will it delete the files/folders after even a reboot
i have to format the partition just to erase the files/folders its put there already.

really quite annoying...

---

### Post by duffydack on 2006-04-01
Just tested with a cdrom, and its the same... WTF?? cant copy a lot of files/folders from anywhere?
Im gunna have to ditch this and go back to windows if i cant resolve this.

---

### Post by duffydack on 2006-04-03
Ok seems it was because i made some folders on the partition and chown`d them to myuser:users ,   dont know why this would make it fail copying files/folders to it, but its fine after i chown`d the mount point to myuser:users ... odd

btw, for example i mount my cdrom (auto owned by myuser:myuser) and i copy files from it and they owner stays the same,, i want the files to take on the owner on the partition im copyin to.....  what do i need to set
thanks

---

