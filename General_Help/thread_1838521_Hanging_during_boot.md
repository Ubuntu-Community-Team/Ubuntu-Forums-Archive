---
title: "Hanging during boot"
date: 2011-09-03
forum: General Help
---

### Post by jdgleaso on 2011-09-03
Running Ubuntu 10.10 on a Dell Inspiron N7010

I shut down my laptop last night and everything seemed fine, now it's hanging when it goes to boot.  The last thing on the display is...

init: ureadahead-other main process (954) terminated with status 4
 * Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
[OK]
 * Setting sensors limits [OK]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Starting the Winbind daemon winbind [OK]
 * Pulse Audio configured for per-user sessions
saned disabled; edit /etc/default/saned
 * Enabling additional executable binary formats binfmt-support [OK]
 * Checking battery state... [OK]

and it just sits there.  If I press the power button it responds and seems to shut down properly.

I really don't know much about the inner workings of linux but I tried booting in recovery mode and run "startx" as root.  X start's up and the desktop displays but I don't have any keyboard/mouse input.

Any help would be greatly appreciated!

---

### Post by raja.genupula on 2011-09-03
> **jdgleaso said:**
> Running Ubuntu 10.10 on a Dell Inspiron N7010

I shut down my laptop last night and everything seemed fine, now it's hanging when it goes to boot.  The last thing on the display is...

init: ureadahead-other main process (954) terminated with status 4
 * Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
[OK]
 * Setting sensors limits [OK]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Starting the Winbind daemon winbind [OK]
 * Pulse Audio configured for per-user sessions
saned disabled; edit /etc/default/saned
 * Enabling additional executable binary formats binfmt-support [OK]
 * Checking battery state... [OK]

and it just sits there.  If I press the power button it responds and seems to shut down properly.

I really don't know much about the inner workings of linux but I tried booting in recovery mode and run "startx" as root.  X start's up and the desktop displays but I don't have any keyboard/mouse input.

Any help would be greatly appreciated!


[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502) 

i hope this link gonna help you

---

