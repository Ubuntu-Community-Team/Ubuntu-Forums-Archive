---
title: "problem with grub, grub2 and windows!"
date: 2010-08-31
forum: General Help
---

### Post by Samic on 2010-08-31
hi
I used _[a file in this tutorial]("http://ubuntuforums.org/showthread.php?t=1519354")_ to move from wubi to a partition
I had Win7 but now I miss it!
I used "bootrec /fixmbr" to bring windows boot back and then _[used this tutorial]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")_ to recover ubuntu. but it just brings ubuntu back!

when i start my computer it immediately starts ubuntu without any boot menu!
none of Shift or Esc keys work!

Also _[here it says check for grub version]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")_:
> 
[LIST]
[*]**Grub Legacy** uses **boot/grub/menu.lst**.
[*]**Grub 2 uses** uses **boot/grub/grub.cfg**.
[/LIST]
But I have both!! (I attached both files)

Also "grub-install -v" gives me:  grub-install (GNU GRUB 0.97)

how can I fix this?!

---

### Post by bcbc on 2010-08-31
That howto migrate doesn't remove windows. So you should have been able to boot windows from the grub menu. 

Please post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and I'll take a look at what is going on.

---

### Post by Samic on 2010-08-31
thanks for your reply
that script didn't remove windows! it replaced mbr and forgot about windows boot menu!

by the way, I used _[this tutorial]("http://ubuntuforums.org/showthread.php?t=1298932")_ and now every thing is good :D

just a question! do you know how can i have the normal grub menu? (the orginal menu that you get when you install ubuntu from a liveCD)

---

### Post by bcbc on 2010-08-31
I'm not really sure what you mean. The grub menu you get after installing with the live CD should look the same as the one you get with Wubi, which should be the same as it was after you ran the migrate script, and now that you've installed grub-legacy I guess it's different.

---

### Post by Samic on 2010-08-31
thanks really
I'm now using _[this tutorial]("https://help.ubuntu.com/community/Grub2")_ to get back everything!
I really enjoy that ubuntu has this large amount of documents almost about anything!!
thanks again for your time

---

