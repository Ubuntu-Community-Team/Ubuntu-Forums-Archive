---
title: "Ubuntu does not load"
date: 2009-08-06
forum: General Help
---

### Post by MrNatewood on 2009-08-06
I got home and booted my PC, after logging in the desktop seemed to load properly but the keyboard and mouse did not respond.
The keyboard's lights(caps lock, scroll lock) were blinking.

So I made a hard reset(manual, clicked on the button on the computer itself since the keyboard and mouse did not respond).

And now every time at boot, when the bar under the ubuntu logo gets to about 90% the screen turns black and shows "no signal".

What could be the problem and how can I fix it?

---

### Post by ubudog on 2009-08-06
When you turned it off like that, it messed it up.  You need to start up using the live cd, and on the menu, select "Repair a damaged system" or something like that.  Follow the instructions afterwards.  Hope that helps. :)

---

### Post by ubudog on 2009-08-06
As for the keyboard, maybe try unplugging it and plugging it back it.  That happened to me before and that's all I had to do.  Hope that helps! :)

---

### Post by thezood on 2009-08-06
> **MrNatewood said:**
> I got home and booted my PC, after logging in the desktop seemed to load properly but the keyboard and mouse did not respond.
The keyboard's lights(caps lock, scroll lock) were blinking.

So I made a hard reset(manual, clicked on the button on the computer itself since the keyboard and mouse did not respond).

And now every time at boot, when the bar under the ubuntu logo gets to about 90% the screen turns black and shows "no signal".

What could be the problem and how can I fix it?

If nothing else works you can always reinstall without formatting. This will keep most of your settings and files. You might want to take a backup of your home folder first, though.

---

### Post by martinbaselier on 2009-08-06
What happens when you choose an older kernel when booting (press esc to enter grub menu and choose an older version)

The flashing leds could indicate kernel-panic.

---

### Post by MrNatewood on 2009-08-06
I tried loading the previous kernel, but that resulted with the exact same "no signal"
Tried the oldest available and the system loaded, though with no nvidia driver which seems to broken. currently cannot re-install it. clicking "activate" in jocky does absolutely nothing. 

System seems to be running fine now, except the propriety driver.

---

### Post by ubudog on 2009-08-06
Burn a cd if you want, and reinstall. :)

---

### Post by ubudog on 2009-08-06
Just use the link in my signature.  :)

---

### Post by sydbat on 2009-08-06
> **MrNatewood said:**
> I tried loading the previous kernel, but that resulted with the exact same "no signal"
Tried the oldest available and the system loaded, though with no nvidia driver which seems to broken. currently cannot re-install it. clicking "activate" in jocky does absolutely nothing. 

System seems to be running fine now, except the propriety driver.When you get the GRUB choices, choose the recovery option (which should be under the first kernel) and "fix X" (or something similar to that wording) then "Normal Boot". It should fix x-org and give you a working desktop.

Let us know if that works.

---

### Post by ubudog on 2009-08-06
Good Luck!

---

### Post by MrNatewood on 2009-08-06
Thanks for all the help :)
I do have a working desktop right now.

Though there is still that pesky nvidia problem.
What can I do to install the nvidia driver? jocky now doesn't even offer me to install it. Any ideas?

I should note that I did the xfix and it didn't make the nvidia driver installable.

---

### Post by ubudog on 2009-08-06
Look in restricted drivers.

---

### Post by MrNatewood on 2009-08-07
OK, this is solved, for future reference, what fixed the nvidia issue was to re-install all the nvidia packages in synaptic and than run
"sudo nvidia-xconfig"

---

