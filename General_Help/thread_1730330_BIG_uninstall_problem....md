---
title: "BIG uninstall problem..."
date: 2011-04-15
forum: General Help
---

### Post by mocklee on 2011-04-15
I have a computer which I upgraded to Windows 7. But when I upgraded it, I forgot about the Ubuntu Install Inside Windows partition I had, and when my disc was formatted, it deleted Ubuntu but not the partition. The partition isn't recognized by Windows AT ALL, but when I start it up the boot menu still gives me an option to boot into Ubuntu. The version I had was 10.10 (I think) I REALLY want to fix this. Thanks.

---

### Post by jerenept on 2011-04-15
Did you use WUBI to install Ubuntu, or did you set up partitions with the LiveCD?

---

### Post by mocklee on 2011-04-15
I used the live cd ISO. It did it automatically.

---

### Post by jerenept on 2011-04-15
ok, you need to boot up the LiveCD and install GRUB from there.

run "sudo grub-install /dev/sda" (assuming you have only one harddrive)

---

### Post by mocklee on 2011-04-15
The only livecd I have is 8.04, will that work??

---

### Post by jerenept on 2011-04-15
Yes, I do believe it would work.

---

### Post by mocklee on 2011-04-15
What do I do from there?

---

### Post by jerenept on 2011-04-15
download the boot info script [here]("http://bootinfoscript.sourceforge.net/") and post the 'results.txt' file produced.

---

