---
title: "drive imaging help"
date: 2012-04-20
forum: General Help
---

### Post by Doug11 on 2012-04-20
I am trying to make an exact image of a 2GB SD card. the card is partitioned with a FAT16 partition which contains a boot file, and there are two ext3 partitions, one contains a skinny linux system and the other has the program to run a game. I am using the method through the terminal with the "DD" command. Is there another method or program to do this with, because when I copy with this way, it does not work, something could be read protected?

---

### Post by cogier on 2012-04-21
I had a look for you and found a tool called "Gdiskdump" which you can download from here. 

[http://gtk-apps.org/content/show.php/Gdiskdump?content=142316]("http://gtk-apps.org/content/show.php/Gdiskdump?content=142316")

---

### Post by Mark Phelps on 2012-04-21
You could try using Clonezilla.  It has an option for imaging an entire "drive" -- which is essentially the same as your USB stick.

---

