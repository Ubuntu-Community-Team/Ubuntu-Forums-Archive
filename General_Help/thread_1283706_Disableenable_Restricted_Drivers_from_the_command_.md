---
title: "Disable/enable Restricted Drivers from the command line?"
date: 2009-10-05
forum: General Help
---

### Post by emarkay on 2009-10-05
Is it possible?
If so, how?

---

### Post by anonymous_user on 2009-10-05
For nvidia drivers, you just install the driver "nvidia-glx-*xxx*" and afterwards you run "sudo nvidia-xconfig".

---

### Post by tuxxy on 2009-10-05
Then you would do the same for ATI and fglrx or for the latest drivers wget them from ATI website and compile in terminal.

---

### Post by KeyserSoze93 on 2009-10-06
If you have the drivers set up already (for which I would recommend envy, which also has a text mode), then you should be able to simple switch between two xorgs.conf's

Make a copy of the non-restricted version, with a name like /home/user/xorg_free, and a copy of the restricted xorg.conf, like /home/user/xorg_restricted.

Then do something like create a script which goes something like:

```
#!/bin/bash

if [[ $1 == "on" ]]; then
 cp $HOME/xorg_restricted /etc/X11/xorg.conf
else
 cp $HOME/xorg_free /etc/X11/xorg.conf
fi

sudo /etc/init.d/gdm restart
```

and give it a name like xorg_swap.sh, default it to switch to the non-restricted driver, but with the parameter "on", it will switch the the restricted driver.

(please note that this will restart X, so you'll loose any unsaved work)

This may not be anything like what you want, but I can't help more unless you explain somewhat more what you want to do.

---

### Post by emarkay on 2009-10-08
> **KeyserSoze93 said:**
> This may not be anything like what you want, but I can't help more unless you explain somewhat more what you want to do.

Thanks - acceptable.  I see how to Install and I presume a remove command undoes it?

The purpose is if I get a bum driver or a video mode on a monitor that pukes and so I can get the GUI in the default mode - as if I can't get to the GUI!

---

