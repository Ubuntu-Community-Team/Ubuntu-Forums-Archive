---
title: "create tar archive"
date: 2011-10-23
forum: General Help
---

### Post by spiky001 on 2011-10-23
I would like some help with tar, !st I have a .img of a partition (16gigs)which I used dd to create. I would like to compress the file but cant seem to get it right. ```
tar cvzf file.img
``` Or dose that just create an empty archive and I should add the .img to that?
   Also the .img only has about 200 mb of data at the moment so the rest is empty I was reading somewhere yesterday about filling the empty space with Zero's???
  
    1 more Q can I pipe dd through gzip to achieve same end result.
```
dd if=/dev/sdc1 | gzip of=/home/user/file.img
```will the above command produce file.img.gz
 This was from memory of a website I cant find today

---

### Post by dino99 on 2011-10-23
maybe this can help:

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

---

### Post by Dave_L on 2011-10-23
Either of these will produce the compressed file /home/user/file.img.gz:

```
dd if=/dev/sdc1 | gzip > /home/user/file.img.gz
```

or

```
dd if=/dev/sdc1 of=/home/user/file.img
gzip /home/user/file.img
```

I don't know whether piping (|) a large output file, as in the first case, uses an excessive amount of RAM.

---

### Post by spiky001 on 2011-10-23
Looks like thats what I wanted thks Dave, The best way to restore uzip then dd back? or is there another

---

### Post by Dave_L on 2011-10-23
I think that's the only way of restoring it.

```
gzip -d /home/user/file.img.gz
dd if=/home/user/file.img of=/dev/sdc1
```

(For other readers of this post who are unfamiliar with the "dd" command, I'll note that it's a very powerful and dangerous command; use it only if you know exactly what you're doing.)

---

### Post by WasMeHere on 2011-10-23
I often use ```
dd if=/dev/sdc1 bs=4096 | gzip > /home/user/file.img.gz
``` (bs=4096 makes it faster)

---

### Post by spiky001 on 2011-10-23
Thks olle I will give that 1 a try as well,
 And I am learning as well dave just have to stay away from main drive then lol

---

