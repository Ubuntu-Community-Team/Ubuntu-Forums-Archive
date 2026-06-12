---
title: "desktop disappears, only terminal"
date: 2012-02-22
forum: General Help
---

### Post by Matt26 on 2012-02-22
i've recently installed ubuntu 11.10 on my computer (fresh install, no other OS on hard drive) and haven't done much with it yet other than trying to install virtualbox and i've installed a couple of firefox extensions.  i've also installed all available ubuntu updates.

a couple of times now i've noticed that my desktop has disappeared and the screen only shows a terminal/command line interface- i can't remember the details of the output displayed.

when this happens i've had to restart the computer by pressing the reset button on the case since nothing that i type shows up in the terminal and pressing ctrl + alt + delete does nothing.

i'm not sure where to start in order to troubleshoot this issue.  any suggestions?

thanks!

---

### Post by roelforg on 2012-02-22
If it happens again;
press CTRL-ALT-F7
and hold the 3 keys for a 5 secs

---

### Post by Frogs Hair on 2012-02-22
If press Crtl+Alt+F1 you will enter a different run level and roelforg's suggestion will return to the desktop . [http://www.skullbox.net/init.php](http://www.skullbox.net/init.php)

---

### Post by HavarN on 2012-02-22
Are you running mdadm?

The same thing happened to me after i installed mdadm for my raid setup.

If you have the same problem as I did, you could try just waiting some seconds, then type exit and press enter. Because:

I realized after removing the keywords quiet and splash from the boot options in the grub-menu that Ubuntu really dropped me into an initram shell when the boot process stopped. There seemed to be a bug in usplash which didn't seem to notice that the boot process had halted into an initram shell.

Check this post for a solution, if you have the same problem as I did:
[http://www.bomski.com/2012/01/ubuntu-11-10-with-raidnot-booting-after-installing-mdadm-read-on/](http://www.bomski.com/2012/01/ubuntu-11-10-with-raidnot-booting-after-installing-mdadm-read-on/)

If you are not using mdadm, however you could try removing the quiet and splash options from the grub boot menu to see if there is really something halted in the background that usplash hides from you.

---

### Post by Matt26 on 2012-02-22
thanks for the suggestions, but is there a way for me to troubleshoot this issue?

i'd like to figure out why this is happening and hopefully prevent it from happening again.

thanks!

---

### Post by roelforg on 2012-02-22
> **Matt26 said:**
> thanks for the suggestions, but is there a way for me to troubleshoot this issue?

i'd like to figure out why this is happening and hopefully prevent it from happening again.

thanks!
If my answer helped, try appending
```

vt.handoff=7

```
to your kernel cmdline.

---

### Post by Matt26 on 2012-02-22
> **HavarN said:**
> Are you running mdadm?

The same thing happened to me after i installed mdadm for my raid setup.

If you have the same problem as I did, you could try just waiting some seconds, then type exit and press enter. Because:

I realized after removing the keywords quiet and splash from the boot options in the grub-menu that Ubuntu really dropped me into an initram shell when the boot process stopped. There seemed to be a bug in usplash which didn't seem to notice that the boot process had halted into an initram shell.

Check this post for a solution, if you have the same problem as I did:
[http://www.bomski.com/2012/01/ubuntu-11-10-with-raidnot-booting-after-installing-mdadm-read-on/](http://www.bomski.com/2012/01/ubuntu-11-10-with-raidnot-booting-after-installing-mdadm-read-on/)

If you are not using mdadm, however you could try removing the quiet and splash options from the grub boot menu to see if there is really something halted in the background that usplash hides from you.

no RAID setup.

what are the quiet and splash options that you're referring to in the grub boot menu?

---

### Post by Matt26 on 2012-02-22
> **roelforg said:**
> If my answer helped, try appending
```

vt.handoff=7

```
to your kernel cmdline.

how do i do this?  what does this code do?

---

### Post by roelforg on 2012-02-22
> **Matt26 said:**
> how do i do this?  what does this code do?

First a tmp mod to see if it works:
reboot your pc; when GRUB shows, hit e
Now use the arrow keys to navigate to the line starting with vmlinuz and insert it at the end of the line (put a space before it)
Hit CTRL-X
and post wherether it displays your login screen.

---

