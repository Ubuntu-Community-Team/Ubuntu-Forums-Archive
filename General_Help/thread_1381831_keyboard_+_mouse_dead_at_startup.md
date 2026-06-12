---
title: "keyboard + mouse dead at startup"
date: 2010-01-15
forum: General Help
---

### Post by jesuisbenjamin on 2010-01-15
Hello Forum,

I use Jaunty on Dell Vostro 1510. Since i installed jaunty it happens my keyboard and mouse are not responding when starting up, so i cannot log in.
After restarting several times (sometimes 2x sometimes 10x) it suddenly works.

My questions are:
[LIST=1]
[*]How can i fix this? I would like to be able to log in without error of this kind, it's really frustrating.
[*]How is it possible that something like this doesn't work for several times and that after so many start-ups it works again? What could possibly change on my computer while it is off? Isn't the data supposed to be unchanged when the computer is off (except for date and time?)?
[/LIST]


Thanks for your help.
B.

---

### Post by khelben1979 on 2010-01-15
Are the mouse and keyboard connected through USB? And if it is, have you tried with using other USB ports?

I suspect that this is a hardware problem and have nothing to do with Ubuntu other than how Linux tries to use it.

---

### Post by jesuisbenjamin on 2010-01-15
I use keyboard and touch-pad of the laptop. I can use the F-keys before Ubuntu starts up: doesn't it disprove the hardware question?

---

### Post by DarkHorse8 on 2010-01-15
I have a similar problem running Kubuntu, I have an Acer E-machine. I know this isn't a hardware problem as when I boot into Windows the keyboard is fine, and when I (using the recovery mode) drop directly into a shell, the keyboard is fine. I have a handy USB keyboard, if I startup the machine with it plugged in, it doesn't respond until I have unplugged the darn thing and then plugged it in again. I don't believe this is in any way a hardware issue!

---

### Post by khelben1979 on 2010-01-15
> **jesuisbenjamin said:**
> I use keyboard and touch-pad of the laptop. I can use the F-keys before Ubuntu starts up: doesn't it disprove the hardware question?

I don't think so. It can still be a hardware problem, although I don't say that it is. Did you try using the other USB ports?

---

### Post by DarkHorse8 on 2010-01-16
Doesn't matter which USB port it's plugging into. BTW, I am also using a laptop, so unplugging my primary keyboard is not an option.  could this not be an X or KDE problem as the laptop's keyboard only stops working once it enters kde? like I said, the keyboard works fine in the shell before entering into the window manager. is there some way that I can remove KDE/x completely and re-install from scratch to see if that will solve the problem.

---

### Post by jesuisbenjamin on 2010-01-16
> **khelben1979 said:**
> I don't think so. It can still be a hardware problem, although I don't say that it is. Did you try using the other USB ports?

No, as Dark explained, it's a laptop, there is no way to plug or unplug anything. And again the issue begins when Ubuntu starts up, not before. If i can enter Bios and use the keyboard or chose a boot option with Grub but cannot use it when Ubuntu starts up, then the issue is not keyboard-mouse related only, there is a software issue.


> **DarkHorse8 said:**
> could this not be an X or KDE problem as the laptop's keyboard only stops working once it enters kde

I use Gnome, so it would remove the option of a KDE-only issue.

Cheers.

---

### Post by jesuisbenjamin on 2010-01-18
Please help! :)

---

### Post by khelben1979 on 2010-01-18
Maybe there is something wrong with the graphical login manager then? If that's the case, you have the option of using [GDM]("http://en.wikipedia.org/wiki/GNOME_Display_Manager") or [KDM]("http://en.wikipedia.org/wiki/KDE_Display_Manager").

Is it GDM that is being used right now?

---

### Post by DarkHorse8 on 2010-01-19
I doubt it, JB is probably using GDM and I'm using KDM, could this be something with USB, as some laptops use the USB bus for the keyboard and touchpad? I'm going to try updating to 9.10 (I need to anyway) I'll let you know if anything is resolved.

---

### Post by DarkHorse8 on 2010-01-20
I'm now running 9.10, no joy :(

---

### Post by jesuisbenjamin on 2010-01-20
GDM, KDM? How can i find out?

Graphical login manager does that mean there is another way to log in?
And if so i surely have to use my keyboard to turn to a non-graphical login method. If my keyboard is not working then i cannot switch and if i switch before the issue occurs then i cannot make out whether it has to do with the graphical login manager...

or?

Thanks

---

### Post by khelben1979 on 2010-01-21
> **jesuisbenjamin said:**
> GDM, KDM? How can i find out?

Graphical login manager does that mean there is another way to log in?

If you checked the Wikipedia pages you should see differences in how the login managers looks like. GDM uses [Gnome]("http://en.wikipedia.org/wiki/Gnome_%28linux%29") while KDM uses [KDE]("http://en.wikipedia.org/wiki/KDE").

I guess you don't have the possibility on attaching a USB keyboard on to that laptop?

---

### Post by jesuisbenjamin on 2010-01-21
I have GDM and i can plug in a USB keyboard.

---

### Post by khelben1979 on 2010-01-21
> **jesuisbenjamin said:**
> I have GDM and i can plug in a USB keyboard.

Okay, so the solution could be that you replace GDM with KDM because something is messed up with GDM, perhaps?

You can check if the problem is with GDM and not the desktop enviroment itself if you log in with your usb keyboard and then from within gnome try to access the keyboard from there. Does it work?

---

### Post by sgaap on 2010-01-31
I got exactly the same issue in 9.10, keyboard works fine in the CLI, but once im in an X environment the keyboard doesnt work at all (no issues in 9.0.4), its not a login manager issue, nor does it has any relation to the window manager used (ive tested gnome, kde, gdm, kde, and all kinds of sessions without using a login manager).
The mouse stops moving if theres keyboard input.

It looks like a problem with the xorg version or the xorg.conf thats generated in 9.10, ive tried with different videodrivers even (altough i cant see any correlation between that and this issue) but the issue is not going away, i do get x errors but there is no x log in /var/log (last time i used linux before ubuntu was gentoo so the location might be diferent in ubuntu, unfortunatly no info about that is to be found)

Oh, and ive tried with multiple usb keyboard (my pc lacks a legacy ps/2 port so cant test that)

so to summarize:

- problem starts in 9.10
- it has no relation to any login manager of window manager
- its not keyboard or usb port related
- mouse movement halts if there is keyboard input

If i get the time ill try to get my xorg config and try find a way to enable logging for X so i can relay that output to here

---

### Post by Stan_1936 on 2010-01-31
> **DarkHorse8 said:**
> I'm now running 9.10, no joy :(

It **may** be the same as **[COLOR="Red"]this[/COLOR]** problem:
[http://ubuntuforums.org/showthread.php?t=1137378](http://ubuntuforums.org/showthread.php?t=1137378)

I experience the **[COLOR="Red"]above problem[/COLOR]** with a Dell machine.  The mouse and keyboard become unresponsive....sometimes immediately after startup....sometimes ten - 20 minutes after startup.  No solution has been found.

I've removed Ubuntu from that machine and won't be wasting any more of my time with Ubuntu on that system.

PS:  They should be addressing real issues(such as this one) rather than trying to make it look better!

---

### Post by DarkHorse8 on 2010-02-03
[QUOTE=Stan_1936;8754414]It **may** be the same as **[COLOR="Red"]this[/COLOR]** problem:
[http://ubuntuforums.org/showthread.php?t=1137378](http://ubuntuforums.org/showthread.php?t=1137378)

Doubt it, the problem starts before the update. Don't think it's a login manager either, I think the problem is lower than that.

---

### Post by jesuisbenjamin on 2010-02-03
Strangely the issue appears on an irregular frequency, it has not happened since a while now, but i expect it to happen at any moment.

---

### Post by jesuisbenjamin on 2010-02-08
Extra info:
There are also instances of dead keyboard with active mouse (while in most cases both are either active or dead).

---

### Post by sgaap on 2010-02-08
I managed to fix the problem for me after removing fglrx form the list of modules to be loaded, after that it worked fine, even after multiple soft reboots.

the issue is back after a cold reboot now so that discards fglrx being the issue here for me, the only thing i can think of might be udev and X not being nice to each other.

---

### Post by sgaap on 2010-02-10
not sure if its relevant but running the latest development build now, which featured the same bug.
It only occurs when i boot normally however, not when i use the recovery method, drop to a networked root shell and invoke gdm from there, so its not X or videocard drivers, but something thats not happening (service/configuration options etc) during a recovery boot.

---

### Post by scarn on 2010-02-13
> **sgaap said:**
> not sure if its relevant but running the latest development build now, which featured the same bug.
It only occurs when i boot normally however, not when i use the recovery method, drop to a networked root shell and invoke gdm from there, so its not X or videocard drivers, but something thats not happening (service/configuration options etc) during a recovery boot.
Yeah, same thing happening for me, also I have similar access through invoking the graphical desktop out of a shell. Can't figure out what it is that isn't happening in the recovery mode, though!

---

### Post by jesuisbenjamin on 2010-06-18
Hi there,

Do we have any update on this? Is this fixed in 10.04?
It's funny how this is completely random: i haven't had the problem for 2 months or so and then suddenly i starts again. I'm a bit annoyed that i have to reboot 5 to 6 times before it wishes to recognise my keyboard.

Thanks.
B.

---

### Post by gOLdenHaWK3D on 2010-09-05
Problem exists in 10.04 too!

---

### Post by tvdkolk on 2012-01-08
I'm still having the very same problem in Ubuntu 11.10. 

Apparently this is already a known issue for two years, and still no solution?

---

### Post by sirkeith on 2012-01-08
I am experiencing the problem now as well after moving up to 11.10 and also in Mint 12. Both have the same kernel so I am thinking it is a kernel issue. 3.0.0.14 because I did not have the issue with 3.0.0.12 nor a couple of PPA kernels. I have tried different ports and different mice. Normally it is pretty random but today it happened on 2 reboots in a row. When it happens ya just gotta go away for awhile but it is pretty frustrating.

---

