---
title: "Encrypted Retrieval"
date: 2009-11-15
forum: General Help
---

### Post by dhblausey on 2009-11-15
The other day I was trying to upgrade from 9.04 to 9.10 via the update manager, but midway it came up with some errors, restarted, and corrupted my OS. 

I have no idea how to fix this, but I was planning on just downloading the 9.10 .ISO then starting fresh, but I would like to retrieve some files from my Home directory first. I've tried using a 9.04 live boot disc to get in then coping the files to an external Hard Drive, but every time I try I'm told I'm not the owner of the files and thus can't copy them. I've even tried using the terminal, using:

sudo cp 

but then it says excluding files and lists all of them.

Any help would be great!

Thanks

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
Are the files encrypted or just belong to a certain user? You can change the permissions if the latter with chmod. If the former then you should still have permissions on the encrypted archive and chmod would be the solution still. Otherwise you could decrypt the files with the password you set to encrypt them and move them.

---

