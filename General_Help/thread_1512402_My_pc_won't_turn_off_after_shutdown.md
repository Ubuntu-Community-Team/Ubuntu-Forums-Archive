---
title: "My pc won't turn off after shutdown"
date: 2010-06-18
forum: General Help
---

### Post by JUOKAS on 2010-06-18
Hi, guys. 
I instaled to my pc ubuntu 10.04, and now pc dont want to turn off after shutdown, I need to swith a buton to shutdown. 
Do you have any solution? :confused:

---

### Post by jesuisbenjamin on 2010-06-18
Hi there,

perhaps you should try to shut down with the "shutdown" command. See ```
shutdown --help
``` for more info. You might want to run ```
shutdown -h -v 0
``` -v (verbose) may return the information you need. 0 is the countdown in minutes before shutdown, i don't know if it accepts 0 actually, so 1 may be the minimum.

Hope this helps.

---

### Post by JUOKAS on 2010-06-18
there is all the same. In other wersions of os I just type *acpi=off* in /boot/grub/menu.lst file, but now I donnt have such file. I make one and place the line but it dont work..

---

### Post by jesuisbenjamin on 2010-06-18
Ha, did you see this thread? [http://ubuntuforums.org/showthread.php?t=1469501](http://ubuntuforums.org/showthread.php?t=1469501)

It doesn't seem solved yet though. :(

---

