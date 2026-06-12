---
title: "HELP! ubuntu hangs after login"
date: 2009-08-25
forum: General Help
---

### Post by Brandon.Viking on 2009-08-25
I am running Ubuntu 9.04 fully updated as of yesterday. Tried to boot today ... no problems up to GDM ... login ... starts to load my desktop and the whole system hangs. No more keyboard input, no more mouse movement, no ability to turn numlock off or on again.

Anyone have any ideas?:confused:

Brandon.

---

### Post by Brandon.Viking on 2009-08-25
I am currently pursuing graphics drivers ... anyone else got something that could completely lock up a machine?

:confused:

---

### Post by x33a on 2009-08-25
maybe hal problem, just guessing.

take a look at the logs (use a live cd).

---

### Post by P4man on 2009-08-25
acpi problem..?

Try adding acpi=off to your kernel parameters (grub, press esc / then e to edit.. add it behind "quiet splash"). Good chance it wont boot without acpi, but worth trying. 2 other options you can test: napic nolapic.

---

### Post by Brandon.Viking on 2009-08-26
After uninstalling all of the restricted drivers the machine still hangs. I can boot to the login screen, no problem. Can then CTRL-F2 or other to work via the CLI without an issue. Something that loads during a login is causing the machine to hang. I noticed some other bugs being raised in launchpad relating to pulseaudio and this latest kernel 2.6.28-15. This only started happening after the update on Monday.

Any ideas will be appreciated. Off to hack pulse audio now. :(

Brandon.

BTW, acpi=off made no difference and the machine still hung after logging into a session.

---

### Post by Brandon.Viking on 2009-08-27
Im not sure what the problem was but after uninstalling a few things and trying again ... its working.

Got me stumped :confused:

---

### Post by x33a on 2009-08-27
all's well, that ends well :popcorn:

---

### Post by only4manni on 2010-04-19
hey i have the same problem 
but im a new user o ubuntu can you please tell me this step by step for how to solve such a problem.
THANKS

---

