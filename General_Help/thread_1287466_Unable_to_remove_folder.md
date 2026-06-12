---
title: "Unable to remove folder"
date: 2009-10-10
forum: General Help
---

### Post by olympic on 2009-10-10
Ran grsync today to backup my /home/ folder to a new USB HDD.  In error though I created my backup directory (UbuntuBU) in /media/ and not on the HDD.  I have since rectified that and completed the backup to the HDD, but for some reason am unable to remove the now empty unwanted folder in /media/.

The permissions for /media/UbuntuBU/ were originally root, but I have changed that to myself but still get a "permission denied" message if I try removing the directory ( using the cli and command <rmdir /UbuntuBU/>).
I have also tried <sudo rmdir /Ubuntu/> without success.

There are no "hidden" files in the directory - it is empty.

Any suggestions?

---

### Post by wojox on 2009-10-10
Just try:

```
sudo rm -rf UbuntuBU
```

---

### Post by olympic on 2009-10-10
Thank you.

That was about the only command I did not try.

The directory is gone.:P

---

