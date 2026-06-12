---
title: "can't boot into ubuntu"
date: 2010-06-13
forum: General Help
---

### Post by saturnblackhole on 2010-06-13
it says this:

Alert! /dev/disk/by-uuid/b573ab4-f00d-489e-ba0c-d6ee3bda73bc does not exist. Dropping to a shell

BusyBox v.1.13.3 (ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)

i entered "help" but it spewed out alot of jibberish that i didn't understand. 

does anyone know what causes this?

[IMG]http://imgur.com/iFmlS.jpg[/IMG]

[IMG]http://imgur.com/08s0o.jpg[/IMG]

[IMG]http://imgur.com/MNTWW.jpg[/IMG]

---

### Post by Ozymandias_117 on 2010-06-13
Boot to a liveCD, mount your Ubuntu drive and post the results of ```
sudo blkid
``` and post the contents of your fstab (Should be in /media/long_string_of_letters_and_numbers/etc/fstab )

---

