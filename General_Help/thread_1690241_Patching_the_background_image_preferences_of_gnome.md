---
title: "Patching the background image preferences of gnome-terminal 2.30.2 in Ubuntu 10.04.1"
date: 2011-02-18
forum: General Help
---

### Post by desibug on 2011-02-18
Hi, Yesterday I installed Ubuntu with wubi again and i wanted to configure  my own gnome-terminal as i want i to look. I want a background image and  the standard-preferences are not very good. i want the image to be  resized to the terminals size. I have found a patch which offers this  preference. But because I'm relatively new to ubuntu i don't know how to  patch the Terminal i tried it with:  patch -p1 < ../03457-Added-background-image-scaling-.patch but one Hunk is failing every time:
  ```
root@ubuntu:/home/gabriel/gnome-terminal-2.30.2# patch -p1 < ../03457-Added-background-image-scaling-.patch
patching file src/profile-editor.c
Hunk #1 succeeded at 142 (offset 1 line).
Hunk #2 succeeded at 818 (offset -51 lines).
patching file src/profile-preferences.glade
Hunk #1 succeeded at 1987 (offset -102 lines).
Hunk #2 succeeded at 2014 (offset -102 lines).
Hunk #3 succeeded at 2062 (offset -102 lines).
patching file src/terminal-profile.c
Hunk #4 succeeded at 1343 (offset 14 lines).
patching file src/terminal-profile.h
patching file src/terminal-screen.c
Hunk #1 succeeded at 72 (offset 2 lines).
Hunk #2 succeeded at 143 with fuzz 2 (offset 3 lines).
Hunk #3 succeeded at 624 (offset 107 lines).
Hunk #4 succeeded at 1019 (offset 110 lines).
Hunk #5 succeeded at 1240 with fuzz 2 (offset 106 lines).
Hunk #6 FAILED at 1142.
Hunk #7 succeeded at 1279 (offset 73 lines).
Hunk #8 succeeded at 1310 (offset 73 lines).
Hunk #9 succeeded at 2034 (offset 52 lines).

```

I have also tried to copy the file into the patches folder and then dpkg-buildpackage -b but then there is always a failure at this patch.
  Could you please tell me how to patch the gnome-terminal? Thanks in advance and i hope you can help me
  P.S. The Page where i Got the Patch is: [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/213830](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/213830) and the patch: [http://launchpadlibrarian.net/55553257/03457-Added-background-image-scaling-.patch](http://launchpadlibrarian.net/55553257/03457-Added-background-image-scaling-.patch)

---

### Post by desibug on 2011-02-18
no one got any idea? please help me

---

