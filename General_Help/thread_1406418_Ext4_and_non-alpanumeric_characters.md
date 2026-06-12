---
title: "Ext4 and non-alpanumeric characters"
date: 2010-02-13
forum: General Help
---

### Post by AbdRahim on 2010-02-13
I have ~15000 music files to transfer to my new server, which is formatted in Ext4. It won't allow me to copy files with a colon in the file name. These files have been on ntfs drives and ext3 drives with no problem. Any ideas? It would take years to rename all of these files. I really don't want to take everything off of the server and re format it.

---

### Post by ColombianGold on 2010-06-22
Hi AbdRahim,

Im having the same issue, I think its a samba problem. Im still searching for a solution, were you able to solve it? Anybody have any ideas?
Thanks

---

### Post by lukeiamyourfather on 2010-06-22
If its a Samba thing try another way to copy the files like scp (ssh server needs to be on source end). Not sure if the colon is a valid character for filenames, I assume it is but I'm not in front of a Linux machine to check. Cheers!

---

