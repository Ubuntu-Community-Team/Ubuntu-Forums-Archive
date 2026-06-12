---
title: "Ubuntu 10.04 unable to mount /etc/cifspw after installation!"
date: 2010-05-01
forum: General Help
---

### Post by Elie-M on 2010-05-01
Please guys I need urgent help!!

Finally ubuntu 10.04 is installed and asked me for a reboot for changes to take effects. after the reboot on the log in screen an error appears as the following:

An Error Occurred while mounting credentials=etc/cifspw

Press S to Skip Mounting or M to start Manual Recovery.



from this point on I dunno what to do :( S puts me in a mode with login: and stays like this


and M puts me in a terminal mode as root and I dont know what to do next...

please I need help to solve this to login to my new 10.04 :S :(

---

### Post by toshin696 on 2010-05-01
Oh men... sorry, i can't help you...

I've a similar problem... but i've a black screen...

anyone have any idea????

I've a Aspire One D250 (Netbook) Atom 270, 1gb RAM, Intel GMA 950...

---

### Post by Elie-M on 2010-05-01
okay I solved this myself. I booted in recovery mode and then accessed fstab and commented out the windows shares I used to auto mount on startup with # and it works for now, I'll look in it later.

ur black screen would be probably from an xserver-xorg fail.

try to boot in recovery mode, use the netroot mode (the one with networking enabled)

use sudo apt-get purge xserver-xorg && sudo apt-get install xserver-xorg


this will remove it completly then reinstall it again. that worked for me

---

### Post by toshin696 on 2010-05-01
Thanks... but... it was a like poltergeist-like-thing... jjejejeje

I leave the partition of ubuntu alone for 2 hours and go back and LOOK... Boot UP!!!! But the next time maybe not... jejeje

Ubuntu love/hate relationship :lolflag:

---

