---
title: "Burn a ISO image with a specific name"
date: 2012-05-16
forum: General Help
---

### Post by Telhma on 2012-05-16
Hello all, I wanna burn a CD, but the CD needs to get a name i want to give it. It's a ISO immage. I use furious ISO mount to burn my cd's but it does not allow me to make a cd title.

How can i fix this problem??

thanks in advance

xx

---

### Post by cmont899 on 2012-05-16
You need to open the iso, edit "/.disk/info" and then repack the ISO.

---

### Post by Cheesemill on 2012-05-16
I use [ISO Master]("apt://isomaster").

---

### Post by Telhma on 2012-05-16
> **cmont899 said:**
> You need to open the iso, edit "/.disk/info" and then repack the ISO.

How do i find those hidden files, and what program do you use to remake the ISO ?

---

### Post by Telhma on 2012-05-16
I created the a new ISO with
mkisofs -o /tmp/file.iso /tmp/filemap/

but then the lable became CDROM, and again not the lable i need to have :(

---

### Post by Mojosdad on 2012-05-17
Does the -V option of mkisofs allow you to specify the volume name of the created iso?

mkisofs -o /tmp/file.iso -V "MY_VOL_ID" /tmp/filemap

---

### Post by Mojosdad on 2012-05-23
Funnily enough I just created an iso image and forgot to put the correct image name in as per previous reply. I used hexedit to modify the 32 bytes ASCII strings starting at offsets 0x8028, 0x10019, 0x10875, 0x11855, 0x18019, 0x18875, 0x19855, 0x80871, 0x80931 to give the name I wanted.

---

### Post by tumutanzi.com on 2012-05-23
I always use the USB stick to make an OS and then install it on my  computers. It is really environment friendly.

---

