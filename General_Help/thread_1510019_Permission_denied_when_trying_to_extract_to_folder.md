---
title: "Permission denied when trying to extract to folder"
date: 2010-06-15
forum: General Help
---

### Post by lanceman63 on 2010-06-15
I have been trying to download some brushes for GIMP and when I try to extract to the brushes folder in : Filesystem > USR > Share > GIMP > 2.0 > Brushes I get a dialogue box that says "Permission denied. You do not have permission to copy files to this folder" or something to that effect. I am the administrator on this system and the only user. Why can't I copy to the folder? How can I fix this?

Thanks,

lanceman

---

### Post by owain123 on 2010-06-15
In terminal type:
sudo chmod 755 /usr/share/gimp/2.0/brushes

(not sure if my path is 100% correct with letter caseing as i don't have it installed)

What the 'chmod 755' command does is give you admin rights to that folder or file that you state after it, alternatively you can use the 'chmod 777' command if that doesn't work.

If the command works without throwing any errors at you, then go ahead and try copy/move the file into that folder.

Hope this helps

---

### Post by zvacet on 2010-06-15
```
sudo cp package_name /usr/share/gimp/2.0/brushes
```

---

### Post by maedox on 2010-06-15
Do *not* just randomly change permissions on system folders. You will be in a heap of trouble if you mess up.

Do the copying with sudo or open a file browser as root with this command
```
gksudo nautilus
```
And be careful. ;)

---

