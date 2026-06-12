---
title: "Ubuntu 10.10 backlight problem"
date: 2011-08-10
forum: General Help
---

### Post by saalloo on 2011-08-10
hello, I have Acer emachines E525 Laptop and I couldn't change
the screen backlight. I have done this
   1. sudo gedit /etc/default/grub
   2. find the line starting with GRUB_CMDLINE_LINUX_DEFAULT
   3. add "acpi_osi=Linux acpi_backlight=vendor" to the options
   4. sudo update-grub2
   5. reboot
and it worked, I can reduce the backlight by pressing FN and right arrow key,
but I have to do it on every log on. Is  any other solution?

---

### Post by IT Support on 2011-08-10
I had  same problem  on my leptop FUJITSU SIEMENS amilo pro 8010 and i  flash bios, after  this  everything is working great  :) maybe u have same problem  :)

---

### Post by saalloo on 2011-08-10
I flashed BIOS too, but the same situation, nothing changed :(

---

### Post by Basher101 on 2011-08-10
I got the exact same issue. I fixed it on my acer eMachines E725 by also editing the rc.loacal file in /etc/rc.local. Run gedit when pressing alt+f2```
gksudo gedit /etc/rc.local
```
There you change the file to look like this```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
setpci -s 00:02.0 F4.B=00
exit 0
```
add the line setpci -s 00:02.0 F4.B=00 ***_above_*** the exit 0.

---

### Post by IT Support on 2011-08-10
does any progress???

---

### Post by Basher101 on 2011-08-10
i wonder if he got it working..it should though after editing the rc.local

---

### Post by IT Support on 2011-08-10
> **Basher101 said:**
> i wonder if he got it working..it should though after editing the rc.local

she :)  
we will post  if this solution will work  :) she is my friend  and we together trying to solve  this problem :)

by the way thxs for replay u are kind man  :)

---

### Post by Basher101 on 2011-08-10
I think with my age of 17 i don't qualify as a man yet, but as a teenager^^ Thanks for the thanks btw :p

---

### Post by IT Support on 2011-08-10
> **Basher101 said:**
> I think with my age of 17 i don't qualify as a man yet, but as a teenager^^ Thanks for the thanks btw :p

hehe  u are welcome btw :P

---

### Post by Basher101 on 2011-08-10
:popcorn:

---

### Post by saalloo on 2011-08-10
It doesn't work :(

In /sys/class/backlight directory there is acpi_video0
and I have read that acpi_video0 backlight interface should be disabled

Any solutions? I try do this too - sudo apt-add-repository ppa:kamalmostafa/linux-kamal-mjgbacklight  but the same problem :(

---

### Post by IT Support on 2011-08-10
> **saalloo said:**
> It doesn't work :(

In /sys/class/backlight directory there is acpi_video0
and I have read that acpi_video0 backlight interface should be disabled

Any solutions? I try do this too - sudo apt-add-repository ppa:kamalmostafa/linux-kamal-mjgbacklight  but the same problem :(

I think linux don`t` like emachines leptops  :D :D


























p.s don`t beat me please  :( :D :D

---

