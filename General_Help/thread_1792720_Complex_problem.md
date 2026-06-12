---
title: "Complex problem"
date: 2011-06-28
forum: General Help
---

### Post by Antipacket on 2011-06-28
I am wanting to compile Firefox 5, which requires GTK+ 2.10, which requires glib 2.28, which requires zlib 1.2.5.

When I install zlib 1.2.5, Ubuntu 10.04 brakes and I have to remove the zlib files for it to work again.

Anyone got an idea why is this happening?

Try it in a virtual machine and watch Ubuntu 10.04 fail.

---

### Post by Dangertux on 2011-06-28
Are you installing the package from the repos or the most current version?

I have no problem when installing it from the current version on the zlib site. 

Also make sure you have build-essential.

---

### Post by Antipacket on 2011-06-28
I'm installing the official version. The Ubuntu repository don't have zlib, it has some folked version that Canonical picked up and modified.

All necessary packages are installed.

Did you install it in Ubuntu 10.04.1 LTS?

---

### Post by Antipacket on 2011-06-28
What I am going to try and do is remove Ubuntu's modified zlib, and then install the real zlib.

So, I have deleted Ubuntu's zlib, not much works now, so I have booted into a live enviornment... Now I am going to make install zlib onto the drive. Does anyone know how I can target an install to a directory? Maybe something along the lines of 'make install /dev/sda'?

---

