---
title: "power management from command line"
date: 2010-04-04
forum: General Help
---

### Post by axaard on 2010-04-04
Hi!

I installed an Ubuntu 9.10 to an old IBM Thinkpad laptop. It's pretty old, so I installed in command line mode.

It hibernates itself when I close the display. I do not want to hibernate itself, when I close it. How can I edit it from the command line?

Thanks, and sorry for my english...
ax

---

### Post by gzarkadas on 2010-04-04
You may try to fiddle with /etc/acpi/lid.sh (maybe set it to an empty script?) since it is run by the lidbtn event (in /etc/acpi/events). Just a hint, I have **never** **actually tried it**.

---

### Post by axaard on 2010-04-05
I do not have /etc/acpi/lid.sh file...

```
axaard@aTop:~$ ls -a /etc/acpi
. .. events powerbtn.sh
```

---

### Post by gzarkadas on 2010-04-05
This maybe be because your install method is different or because your laptop is too old and not all acpi functions are supported; I have 9.10 also and my /etc/acpi is full of scripts:
```

root@laptop:/etc/acpi# ls
asus-brn-down.sh    lockbtn.sh       sleepbtn.sh
asus-brn-up.sh      mailbtn.sh       sleep.sh
asus-touchpad.sh    mediabtn.sh      start.d
asus-wireless-2.sh  mutebtn.sh       stopbtn.sh
asus-wireless.sh    nextbtn.sh       thinkpad-stretchortouchpad.sh
batterybtn.sh       playbtn.sh       tosh-wireless.sh
ejectbtn.sh         powerbtn.sh      videobtn.sh
events              power.sh         voldownbtn.sh
hibernate.sh        prevbtn.sh       volupbtn.sh
ibm-wireless.sh     rotatescreen.sh  webbtn.sh
lid.sh              screenblank.sh

```What events do you have inside the /etc/acpi/events folder and what scripts do they have as action? also what is the exact model of the laptop (to search what power management functions it supports)?

I have verified that /etc/acpi/lid.sh is called when I close the lid of my laptop, so a hook can be installed there. We just have to find where to put it.

---

### Post by axaard on 2010-04-06
```
axaard@aTop:~$ ls -a /etc/acpi/events
.
..
powerbtn
```

The powerbtn event is called, when I power button, and it calls /etc/acpi/powerbtn.sh

The laptop is an IBM Thinkpad 600. It's a fresh installed command line system, I just installed these packages with their dependencies: acpi, gcc, gdc, mc, screen.

Here is the list of the installed pacgakes: [http://pastebin.com/fPEXxxvw]("http://pastebin.com/fPEXxxvw")

---

### Post by gzarkadas on 2010-04-06
I am searching it; but in the mean time please check whether the ThinkPad's BIOS Setup has a Power Management section.

PS: If it has, check if a `Will not suspend even if LCD is closed' option is present.

---

### Post by axaard on 2010-04-06
It's BIOS don't have Power Management section and any option like that...

Thanks for your help :-D

---

### Post by gzarkadas on 2010-04-06
Ok, not having the hardware to play with is indeed a limiting factor. However, before I admit that ](*,), here are a couple of ideas to check out:

1. You may try to make a lid event file (inside /etc/acpi/events) and lid.sh executable file - with chmod 755 - (inside /etc/acpi) that will do either nothing (ie just #!/bin/sh) or 
```

#!/bin/sh
test -f /usr/share/acpi-support/key-constants || exit 0
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_WAKEUP

```to wake the computer instead of hibernating it. Restart acpid before testing it. Have it echo something to a file (say in /root/acpi-msg) to confirm that it indeed gets called.

2. If the above does not work, you may try to install pm-utils and possibly HAL; this may enrich your events inside /etc/acpi and supply a lid event. Then retry with 1. 

3. Also check your logs to see what acpi messages get generated when you close the lid; they may provide guidance on what needs tweaking.

4. If nothing of the above works, you may try to study the stuff in some links I gathered during searching for this issue; they provide directions but they generally lead to more involved processes, such as compiling a custom kernel and the like:

These are general pages for thinkpad and acpi/power management:[INDENT][http://www.thinkwiki.org/wiki/How_to_configure_acpid](http://www.thinkwiki.org/wiki/How_to_configure_acpid)
[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#ibm-acpi_events](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#ibm-acpi_events)
[http://www.gentoo.org/doc/en/power-management-guide.xml](http://www.gentoo.org/doc/en/power-management-guide.xml)
[/INDENT]and one with some clever hacks:[INDENT][http://mihai.bazon.net/blog/acpi-suspend-resume-your-linux](http://mihai.bazon.net/blog/acpi-suspend-resume-your-linux)
[/INDENT]This is from Lenovo support for older kernels where apmd was used:[INDENT][http://www-307.ibm.com/pc/support/site.wss/MIGR-4BP6Q6.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-4BP6Q6.html)
[/INDENT]See also the section `Why doesn't my IBM laptop have the brightness sliders in Power Preferences?' in [http://live.gnome.org/GnomePowerManager/Faq?action=recall&rev=28#head-b8b1280115b0a51c2cc27b13a57121130ebf36cb](http://live.gnome.org/GnomePowerManager/Faq?action=recall&rev=28#head-b8b1280115b0a51c2cc27b13a57121130ebf36cb); that setting maybe useful in your case also.

I wish success :); if I come up with something more I 'll let you know.

---

