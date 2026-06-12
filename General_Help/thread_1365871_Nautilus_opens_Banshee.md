---
title: "Nautilus opens Banshee"
date: 2009-12-27
forum: General Help
---

### Post by dtr1001 on 2009-12-27
Hello. I have spent the last two days, (literally) trying to get my ipod to mount and be read by a variety of programs, songbird, then settled on Banshee but I had to use killall -9 nautilus command to allow Banshee to mount it, (or see it). It wont eject as it seems to be trying to use HAL to do this. Anyway, just completed an system update and since then nautilus doesnt work from the gui but instead opens Banshee. Did I screw up a kernel compile when I completed the update?

Nautilus works ok from CLI just not from the menu, unless I select to see the network, and then its ok.

Can someone help me get nautilus working again then maybe offer something in relation to the ipod. I'm on Karmic.

Thanks

David

---

### Post by dtr1001 on 2009-12-28
This is the output I see when i launch nautilus from terminal;

XXX@XXXdesktop:~$ nautilus

(nautilus:4313): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
XXX@XXXdesktop:~$ 

Can anyone tell me what this means? I still get banshee opening when I try to open any home folder from gui.

Thank-you.

David

---

### Post by dtr1001 on 2009-12-28
Fixed the nautilus problem after reading this thread;

[http://ubuntuforums.org/showthread.php?t=980451](http://ubuntuforums.org/showthread.php?t=980451)

...and assigning nautilus as the default program for opening folders

Now to try and resolve the HAL / podsleuth problem.

thanks

David

---

