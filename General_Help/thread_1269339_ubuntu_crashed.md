---
title: "ubuntu crashed"
date: 2009-09-18
forum: General Help
---

### Post by akrovatis on 2009-09-18
hello. i am a newbie. and i don't know very good english. i have attached 2 photos in order to see what happened unexpectantly when i opened my pc after i have connected a hd. after that i have the hd disconected bud the same message is there. what is the problem?

---

### Post by mungwana on 2009-09-18
No master in the art myself but from the error message I would say there is something wrong with the fie system (The instruction on your harddrive which is used to well.. handle files). Have you tried the harddrive in a differant machine and was it working fine?

Make sure and check that the new drive is set to slave. 

Also what happens when you run fsck and it instructs you?

---

### Post by akrovatis on 2009-09-18
the hd may have a problem but in the same system i have windows that it works normal with the hd connected. can i save my ubuntu or i have to reinstal? what can i do for the file system?

---

### Post by akrovatis on 2009-09-18
the hd that i'am talking about is a media hd it doesn't have any os on it.

"Also what happens when you run fsck and it instructs you?" 
what's that?

---

### Post by jimmyhacker on 2009-09-18
type fsck or fsck.ext3 and restart computer after system checking.i saw that im the only master speaking here.i think other advanced users dont give a damn for newbies.

---

### Post by akrovatis on 2009-09-18
> **jimmyhacker said:**
> type fsck or fsck.ext3 and restart computer after system checking.i saw that im the only master speaking here.i think other advanced users dont give a damn for newbies.

i have a job right now so i am going to do this after a while. thank you master. i hope that other masters will come

---

### Post by 3rdalbum on 2009-09-18
```
fsck /dev/sda6
```

This runs the filesystem check manually, as requested, and limits the checking to the disk in question (which is identified in the screenshot as being /dev/sda6).

---

### Post by akrovatis on 2009-09-18
i run fsck /dev/sda6 there were some problems that ubuntu fixed after asking. now it's all ok. i hope i don't ave any problems with my files. thank you very much guys.

---

