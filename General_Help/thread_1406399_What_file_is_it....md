---
title: "What file is it...?"
date: 2010-02-13
forum: General Help
---

### Post by emoric on 2010-02-13
Hello,

I keep my /home on a separate partition. After every clean install of Ubuntu my old panel configuration is loaded. Meaning, shortcuts on my panel and different applets I've put on my panels as well.

My question is, what file in the /home folder is keeping these settings? Simply, I'd like to delete so I can have that "fresh" install feeling on my desktop.

Thank you!
Ubuntu 9.10

---

### Post by flippo on 2010-02-13
I'm not entirely sure which one but its in one of the .gconf .gnome .gnome2 or .local directories.  You can try moving the directories and see if it fixes it, if not move them back.

---

### Post by sgosnell on 2010-02-14
Depending on how many you have, it might be easier to just delete them from the panel.

---

### Post by r_s on 2010-02-14
To have the "fresh" install feeling , you need to remove the directory .gnome and all settings would be restored as if a fresh install.

---

### Post by emoric on 2010-02-14
> **r_s said:**
> To have the "fresh" install feeling , you need to remove the directory .gnome and all settings would be restored as if a fresh install.

Thank you!

Now, one last question. Lets say I kept those settings there as I do from installation to installation. Will anything be affected when switching from 32 to 64bit?

Thank you again guys!

---

### Post by Richard1979 on 2010-02-14
Unlikely,
I've had the same /home for ages.

64/32 specific code will be in /usr/bin and other things like that.

---

### Post by r_s on 2010-02-14
[http://ubuntuforums.org/archive/index.php/t-1130753.html](http://ubuntuforums.org/archive/index.php/t-1130753.html)

---

### Post by emoric on 2010-02-14
Awesome!

Thanks again fellas. I'll mark this as solved. :D

---

