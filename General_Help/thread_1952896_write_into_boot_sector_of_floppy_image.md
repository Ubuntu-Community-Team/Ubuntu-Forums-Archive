---
title: "write into boot sector of floppy image"
date: 2012-04-05
forum: General Help
---

### Post by psudheera on 2012-04-05
hi friends,

I'm doing a project of my os class. came across with a difficulty when overwriting the boot sector of a floppy image. I've created and formatted a floppy image using dd and mkdosfs. Now I want to copy a boot.bin file in to this .img files boot sector. How can I do it?  In the case of actual floppy disk the disk would show in the /dev folder. But in this case it is not. Please can anybody help me? thank you in advance

---

### Post by psudheera on 2012-04-05
never mind I found it.!!

First I connect the image with a loop device using losetup /dev/loop0 image_file.img
Then use dd ,  sudo dd if=./boot.bin of=/dev/loop0

---

### Post by dcstar on 2012-04-05
> **psudheera said:**
> never mind I found it.!!



Then **mark** the thread.

---

### Post by lisati on 2012-04-06
@psudheera: Please use the default font for your posts, and don't forget to mark the thread "solved" using the "thread tools" menu near the top of the page.

---

