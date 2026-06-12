---
title: "installing on top of existing ubuntu"
date: 2011-09-03
forum: General Help
---

### Post by Lakeside5 on 2011-09-03
Long shot but here goes..As usual, I was away from trying to be a hoster for months, now dusting off my old pentiunm 3 to host a site and..decided to replace the ubuntu on there now with 11.04. I set pc to boot from usb drive, have usb with the 11.04 ubuntu on a jump drive..rebooted and, it keeps going to the old ubuntu. Sometimes it asks me for my password but after all this time I forgot it and can't find it. So, am I stuck with the older ubuntu server edition, and not knowing my password?  Or is there some way to start again, and be able to use it as a server with 11.04 installed? Thanks for any help.

---

### Post by switch10 on 2011-09-03
Make sure you are set to boot from your USB drive first in your BIOS.

To remove that password and set a new one, boot a liveCD/USB and open /etc/passwd with a text editor.  

remove the "x" between the ":" and ":"

```
root:x:0:0:root:/root:/bin/bash
```

so it looks like this;

```
root::0:0:root:/root:/bin/bash
```

Save the file.  

Boot your system and run the passwd program to set a new password.

---

### Post by Lakeside5 on 2011-09-04
Thanks switch10, I will try the bios thing again, for starters. I restarted the computer and as it was booting I pressed  f11 (also tried f2, and f12 which is supposed to work), saw a menu to set boot order, and picked 'boot from usb drive', and I have the usb jump drive plugged in (it has the ubuntu 11.04 on it). BUT it still loads the old ubuntu, 10.04, as though it is NOT booting from the jump  drive. Don't know what I am doing wrong :(

---

### Post by Lakeside5 on 2011-09-04
I went into that password file in ETC, and removed the X and tried to save but it says I don't have permission, am not the owner.  Trying to remember how to change ownership, will google it :) edit   I guess I really can't do anything if I can't remember the password, it asks for the password of course, at the terminal when I do any sudo command, such as to change ownership of a folder (so I can save the edited password file) so pretty much a catch-22.  I have to wipe out the whole operating system, and then install the new linux from the jump drive?  Not sure how to do that.

---

### Post by switch10 on 2011-09-04
Yeah, in order to change the password you would have to be in some kind of live environment, otherwise you would have to provide a password. 

Have you tried using a different USB port?

Have you checked the integrity of the liveUSB stick?  Does it boot on other machines?

---

