---
title: "Kpilot not working"
date: 2006-06-05
forum: General Help
---

### Post by jeremy on 2006-06-05
I did a fresh breezy kubuntu install, and kpilot doesn't work, I set it up ok using the wizard (it found my tungsten t2 fine), but when I try to sync, ...nothing.

---

### Post by jeremy on 2006-06-05
Found the answer elswhere;

Settings -> Configure KPilot -> Device -> Speed = 9600

And it seems to be ok now.

---

### Post by jethro10 on 2006-06-05
[QUOTE=jeremy]Found the answer elswhere;

Settings -> Configure KPilot -> Device -> Speed = 9600

And it seems to be ok now.[/QUOTE]

Spped can be an issue, my Treo 600 works at 5600 and my wifes Treo 600 works at double the speed with the same cable and PC!

Perhaps you could up the speed a little at a time till it fails?

---

### Post by jeremy on 2006-06-06
I'm afraid I spoke too soon, having set the speed to 9600 it works fine and repeatedly until I use another USB device (usb stick or HD), after that it won't work until I have rebooted.

---

### Post by paul cooke on 2006-06-24
[QUOTE=jeremy]I'm afraid I spoke too soon, having set the speed to 9600 it works fine and repeatedly until I use another USB device (usb stick or HD), after that it won't work until I have rebooted.[/QUOTE]

try using /dev/pilot as the device, not /dev/ttyUSB0 or /dev/ttyUSB1

---

### Post by jeremy on 2006-06-24
Thanks Paul, but it is exactly the same as if I use /dev/ttyUSB0

---

### Post by paul cooke on 2006-06-26
[QUOTE=jeremy]Thanks Paul, but it is exactly the same as if I use /dev/ttyUSB0[/QUOTE]

one other thing I did getting my Kpilot working again on this box (was originally warty, then upgraded to breezy then upgraded to dapper) was to set the permissions of /dev/ttyUSB0 & /dev/ttyUSB1 to "others can read and write" as well as owner & group can read/write. I did it using Konqueror running as su (sudo konqueror). I can never remember the command line for messing with permissions, so find it easier doing it in the gui as root


the other box which was a default ubuntu 6.06 install followed by adding kubuntu-desktop to it had /dev/pilot as default and it worked straight off.

---

### Post by jeremy on 2006-06-28
I just had a look, and /dev/ttyUSB0 & /dev/ttyUSB1 are in the 'dialout' group, of which I am a member.

I should add that the problem started when I did a fresh install of Dapper, the same Palm tungsten t2 always worked perfectly before on warty, hoary, and breezy.

---

