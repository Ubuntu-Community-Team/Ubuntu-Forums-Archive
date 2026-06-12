---
title: "shift does not get me single user mode"
date: 2011-09-10
forum: General Help
---

### Post by hwttdz on 2011-09-10
I'm having an issue with sudo, apparently it's parsing a file that I didn't expect it to and it's complaining about multiple definitions.  Of course because of the issue I don't have sudo access so I'm trying to get into single user mode to fix.  

It seems that holding shift no longer does the trick.  Any suggestions?

---

### Post by drs305 on 2011-09-10
If you are referring to getting the Grub2 menu to display, here are a couple of things you can try.

The SHIFT key depends on a keystatus check being accomplished. In some configurations, such as if no other OS is present, the keystatus check may not be incorporated.

1. Try pressing the ESC key repeatedly during the early stages of the boot. If G2 didn't provide the keystatus check, it may check for the ESC key instead.

2. Grub2 also looks for a 'recordfail' event, which forces the menu to display if a boot fails. You could try CTRL-ALT-DEL about halfway through the boot (if you get that far). This may result in the menu being displayed on reboot. The menu will display until you make a selection, so you will have time to select the recovery mode or edit the normal entry so it boots in 'single user' mode.

---

### Post by fdrake on 2011-09-10
if the previous post does not help, use a live cd and look at this file(i am using Lucid, so the name may be a little bit different from mine)

```
sudo cp /etc/init/rc-sysinit.conf /etc/init/rc-sysinit.conf_backup
sudo gedit /etc/init/rc-sysinit.conf
```

and change this line:
> 
# Default runlevel, this may be overriden on the kernel command-line
# or by faking an old /etc/inittab entry
[COLOR="Red"]env DEFAULT_RUNLEVEL=2[/COLOR]


to 
> env DEFAULT_RUNLEVEL=1
save, close and when you reboot you should be in runlevel 1. fix your problem with sudo and replace the default runlevel to 2.

---

### Post by hwttdz on 2011-09-10
First post solved it, I cut power halfway through boot (I realize this is probably not a good idea and not generally recommended) and the next time I got grub.  Started in recovery mode dropped to root prompt and was good to go.

---

