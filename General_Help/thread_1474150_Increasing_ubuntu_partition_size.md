---
title: "Increasing ubuntu partition size"
date: 2010-05-05
forum: General Help
---

### Post by AmuletOfNight on 2010-05-05
Well I just wanted to try UBUNTU before and now I like it and I'm going to resize the partition to 50GB's instead of 10, because I'm dual booting. But I don't even know where to start. How do I increase the partition size? I'm trying to use GParted live CD I can't get unetbootin (or fdisk) to recognize my flash drive (cannot open /dev/sdb1). I'm still a noob at linux, so i need help :)

---

### Post by ubunterooster on 2010-05-05
I've used the ubuntu LiveCD and went to system>administration>Gparted.

---

### Post by AmuletOfNight on 2010-05-05
I tried it and the partition is made at the end of the hard drive and I can't move it to the front so I that I can increase the space it needs.

---

### Post by ubunterooster on 2010-05-05
You need to reduce another partition first.

Edit: Assume you are trying to enlarge dev/sda3. You will need to shrink dev/sda1 or dev/sda2 and then enlarge dev/sda3. Middle, end, or beginning does not matter.

---

