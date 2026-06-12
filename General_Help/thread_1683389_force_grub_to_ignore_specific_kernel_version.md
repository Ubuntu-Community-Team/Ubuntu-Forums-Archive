---
title: "force grub to ignore specific kernel version?"
date: 2011-02-07
forum: General Help
---

### Post by thinking on 2011-02-07
hi all

i just upgraded my storage server to maverick and it seems the 2.6.35-25 kernel doestn like the hardware im using
since im pretty sure its a hardware related problem and the previous kernel hastn the issue im currently booting this old kernel everytime i need the server by hand (using Shift during boot for the grub menu to appear)

well, it narrows down to the following question:
how can i exclude a specific grub entry - in my case the current kernel 2.6.35-25 - so only previous kernels OR future kernels from the next updates will have a chance to boot?

i see two solutions which im not sure IF they work or what would be further problems:

1) using apt to remove the current kernel so only the old one would be left and grub should boot the right kernel, but whats with future updates? will new kernels be installed if the package linux-current (i think thats the packagename) is removed?
maybe my problems are fixed in future LTS releases

2) just removing the /boot files for the kernel version
afaik, grub uses /boot to find the entries for the menu and thus this method would result in booting the right kernel and having the package installed for future updates altough the package itself would be broken

hope you get an idea of what im facing with and try to do
any other options/opinions on what i can do or which method i should prefer?

thx

---

### Post by mcduck on 2011-02-07
I'd say the simplest solution would be to just change the default boot option so Grub would boot your older kernel instead of the latest one. That way you wouldn't have to break anything, and could just change it back after next kernel update (or increase the offset a bit more to keep still using your current kernel, if even the updated kernel fails to work for you).

To change the default boot option you need to edit /etc/default/grub, and change the number on the "GRUB_DEFAULT=0"-line. The numbering starts from 0, and there are two entries per kernel version so if you want the normal boot option for the previous kernel you'd change that to "GRUB_DEFAULT=2".

After editing the file run "sudo update-grub"

(and pay attention to kernel updates, after next update the "2" would point to the kernel you are now trying to avoid from booting...)

---

### Post by jim_deadlock on 2011-02-07
I did this on an old laptop, and I'm pretty sure you don't have to worry about the future kernel updates, it fixes it for you automatically so you shouldn't need to keep messing with it after you've done it once.

---

### Post by thinking on 2011-02-07
excellent
thanks

---

### Post by mcduck on 2011-02-07
> **jim_deadlock said:**
> I did this on an old laptop, and I'm pretty sure you don't have to worry about the future kernel updates, it fixes it for you automatically so you shouldn't need to keep messing with it after you've done it once.
Then you must have done it by editing a wrong file... :)

Changes to /etc/default/grub (or any of the other actaul Grub config files) will not be removed by updates.

Perhaps you edited /boot/grub/grub.cfg instead (which isn't supposed to be edited by hand at all), or it was the old grub version and you edited the menu.lst file but didn't edit the default options section?

Of course in this very situation it might actually be helpful for the change to disappear on the kernel update, though.... :D

---

