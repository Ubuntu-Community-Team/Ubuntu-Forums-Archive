---
title: "No GUI interface"
date: 2006-02-11
forum: General Help
---

### Post by craY21 on 2006-02-11
I just installed Ubuntu on a clean laptop (no OS what so ever)

I downloaded the intel cpu .iso from the download section and installed it from an external CD-rom as the internal one is faulty.  I followed all the instructions set everything up, set up the network, and rebooted.  After reboot I was prompted for some more language options and whatnot then it gave me a command line interface to login.  I logged in under the username I specified and then it just sat there waiting for my next command.

I read through many posts on the forum as well as some help questions under support.  From everything I gathered, after I login it should take me to a desktop, but it didn't do that.  I tried to exec gnome but to no avail.  Is the install currupt and should I re-do it or did I do something wrong somewhere along the lines?

It's a gateway laptop 4520GZ with hatachi 60GB HD and NO operating system, what-so-ever.

---

### Post by sup on 2006-02-11
Have not you done a server install? If so, type sudo apt-get install ubuntu-desktop and then reboot
(but I would rather advice another clean install, not sure if this installs everything that usual install does)

---

### Post by Robgould on 2006-02-11
something is awry.  I agree with SUP.  Do another install.  Do NOT type server when you are pompted to boot...just hit enter.  In the partition options tell it to erase everything else.
 
If the same thing happens again, get a new iso and try again.

---

### Post by craY21 on 2006-02-11
ok thanks for the help I'll try the new install.

---

### Post by Jedeye on 2006-02-11
try typing ```
startx
``` at the command line after logging in. if the desktop is installed it should load. But if not you may have done the server install or something else is wrong.

---

