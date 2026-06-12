---
title: "Running some root commands at startup?"
date: 2011-12-04
forum: General Help
---

### Post by FallenUnia on 2011-12-04
Hey all,

I'm using the opensource ATi drivers, which don't fuction too good at powermanagement. To solve this I can make my card run at the low clock speed all the time by using this command as root (so no sudo, but su):

```

# echo "low" > /sys/class/drm/card0/device/power_profile
```Is there some place I can add that line of code, so it automatically does that at start up? On Arch, I think I'd have put it in /etc/rc.local. This script is also there in Ubuntu, so is that the place to put it?

Thanks in advance!

---

### Post by Lars Noodén on 2011-12-04
Yes, putting things in [font=Courier New]/etc/rc.local[/font] will work.  I'm not sure when, in relation to the systemv init scripts, it gets executed, but it does run some time at startup.

Edit:  I just tested it and [font=Courier New]/etc/rc.local[/font] seems to run after the systemv init scripts.

---

### Post by FallenUnia on 2011-12-04
I don't care when it is run, as long as it runs at startup so I don't have to do it manually :P

Can I also place multiple lines after eachother?
I might have to use the command to tell the driver to use the "profile" powermanaging method

---

### Post by Lars Noodén on 2011-12-04
It's a regular shell script using [dash](http://manpages.ubuntu.com/manpages/precise/en/man1/dash.1.html) instead of [bash](http://manpages.ubuntu.com/manpages/precise/en/man1/bash.1.html).  You can put as many statements in it as you want or you can simply refer to an external script.

---

### Post by FallenUnia on 2011-12-04
Alright, fixed! Thanks!

---

