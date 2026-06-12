---
title: "Grub read satge 1.5 error"
date: 2011-04-29
forum: General Help
---

### Post by kannanee06 on 2011-04-29
I'm Running Ubuntu 10.04, Debian(Lenny) and Windows on sda, often i get a Grub error displaying "Grub read Stage Error 1.5" . I'm Not Getting this all the time, but very often when i boot my PC. Pleases someone give me a Solution to overcome this, and i'll be grateful for the same.

---

### Post by sikander3786 on 2011-04-29
Welcome to the forums :-)

We need to see the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Run the script and copy all text from the generated Results.txt and paste in your post. While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

It would let us see your boot setup and might reveal any related problems.

---

### Post by sisayie on 2011-04-29
Boot from liveCD 
Start terminal 
run **sudo fdisk -lu** to see the partition of the disk then run fsck on the bootable partition of your disk (most probably **fsck /dev/sda1**)

I hope it helps

---

