---
title: "Formatting and permissions of an external HDD"
date: 2009-07-18
forum: General Help
---

### Post by crownedzero on 2009-07-18
I picked up a external drive today to back up my movies/music/pics etc. I've more or less got the formatting done, but may have done it wrong. If I try to copy files from my old windows partition to the new ext4 I get permissions issue. i.e "The folder cannot be copied because you do not have permissions to create it in the destination." Any thoughts?

---

### Post by jms1989 on 2009-07-18
try running "sudo chmod 777 /media/ext_hdd/" to give everyone permission to read/write to it. After running the cammand refresh or reload your natilus window so it can see the change.

replace ext_hdd with the actual drive name.

---

### Post by Sidewinder1 on 2009-07-18
Or:
```
sudo chown -R your_username:your_username disk or filename
```
usually it's media/disk
enter your password; that should do it.

HTH,
Side

---

### Post by crownedzero on 2009-07-18
K, I'll give that a shot. Did a little bit of reading and found the chown; I'm assuming chown gives ownership whereas chmod just grants access to all users?

---

### Post by Sidewinder1 on 2009-07-18
I believe that is correct.
The exact command that I used is:
```
 sudo chown -R crownedzero:crownedzero /media/disk
```
if crownedzero is your username you should be able to copy and paste the command in terminal, enter your password when prompted and you should be "good to go".
Side

---

