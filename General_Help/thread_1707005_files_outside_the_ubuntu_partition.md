---
title: "files outside the ubuntu partition"
date: 2011-03-14
forum: General Help
---

### Post by mercilessj on 2011-03-14
[FONT=Arial][SIZE=3]recently windows decided to conviently die on me and get the bluescreen of death on startup of said os. Luckly i had ubuntu installed onto the D:/ drive of my computer which is the same drive that i have my music, videos, pictures, and other files onto. i can access the drive that windows was installed onto from ubuntu, the C:/ drive, but i cannot access anything that is located outside of space that i alotted to ubuntu on the D:/ drive when i partitioned it. i am running ubuntu 10.10 if that helps. TL;DR how can i access files on the same drive that are outside the ubuntu partition from ubuntu[/SIZE][/FONT]

---

### Post by dozycat on 2011-03-14
what is the format of windows partition?
maybe you need to add to ubuntu the support to that kind of format?
I did that with my computer with windows ntfs some time ago.

---

### Post by Hugh971 on 2011-03-14
Can you explain your setup a bit more? Did you install Ubuntu with wubi?

How where the drives set up within Windows?

---

### Post by bcbc on 2011-03-14
> **mercilessj said:**
> [FONT=Arial][SIZE=3]recently windows decided to conviently die on me and get the bluescreen of death on startup of said os. Luckly i had ubuntu installed onto the D:/ drive of my computer which is the same drive that i have my music, videos, pictures, and other files onto. i can access the drive that windows was installed onto from ubuntu, the C:/ drive, but i cannot access anything that is located outside of space that i alotted to ubuntu on the D:/ drive when i partitioned it. i am running ubuntu 10.10 if that helps. TL;DR how can i access files on the same drive that are outside the ubuntu partition from ubuntu[/SIZE][/FONT]

Look in the /host folder: 
ALT+F2, nautilus /host

PS if you are using Wubi and windows is toast you might want to consider [migrating]("http://ubuntuforums.org/showthread.php?t=1519354") to a normal install. At least, take a backup of your data.

---

