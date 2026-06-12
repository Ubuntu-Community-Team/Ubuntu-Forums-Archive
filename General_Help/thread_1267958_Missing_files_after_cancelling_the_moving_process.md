---
title: "Missing files after cancelling the moving process"
date: 2009-09-16
forum: General Help
---

### Post by MCOSWEL on 2009-09-16
i move my files on a folder from ntf partition to another folder (documents) on ubuntu. when the moving is in progress, i cancel it because i move the wrong files. i want to move the rest of the files in documents folder back to ntfs partition (it's original location). To my surprise, there are missing files. I look at the folder in my ntfs partition, 5 files were move but when I look at the documents folder in ubuntu, there are only 3 files. Where's the two?? Where did ubuntu put the files before it move it from ntfs to linux partition. Plzzz help me.

---

### Post by danwood76 on 2009-09-16
Ubuntu didnt put them anywhere.
Its one of the problems with the NTFS filesystem drivers, normally you wouldn't cancel a move and would copy instead between NTFS and anything else as NTFS doesnt behave correctly under linux.

You might be able to recover the files with partman (I think thats the right app) and do a scan on the partition and find the deleted files.

---

### Post by MCOSWEL on 2009-09-16
woahh. thnx for the fast reply. ok, i'll try your method and see if i can recover the files. Thank you.

---

### Post by MCOSWEL on 2009-09-16
still doesn't work.. any other method??

---

