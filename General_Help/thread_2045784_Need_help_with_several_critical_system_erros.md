---
title: "Need help with several critical system erros"
date: 2012-08-21
forum: General Help
---

### Post by wiseguy12851 on 2012-08-21
I startup Ubuntu 12.04 and log into the normal Unity that comes packaged with 12.04. Everything works great, so I start to do some Qt programming with windows like Firefox, Nautilus, and the terminal open.

Sometime later Nautilus folder windows close on it's on with no error message, After many tries of getting the folder windows back open (they keep opening and immediately closing) it may or may not finally open and stay open.

After that other errors start happening such as the window theme remains the same but the window content is drawn very old and basic looking and many of the icons are switched to a simpler alternate theme.

After that tooltips become a solid white and flat window with no text and the scrollbar (and other controls) turn to look like 1990's controls (very flat and old looking).

From there it gets worse to the point where no windows open except the dasher although nothing can be launched from it. Requests to log out or shutdown does nothing either.

Finally I start getting error messages when trying to run a Qt application I might be working on, this is the only error message I explicitly got from all of this and it is

```
Gtk-WARNING **: cannot open display: :0
```

I'm finally left with no choice but switch to terminal 1 via "ctrl + alt + f1" and reboot the system from there.

It's important to note that this doesn't happen all at once but rather over a time of about an hour or two, it does happen repeatedly and I don't know how to fix many Linux errors yet. I've installed several packages on Linux but it's only 2 days old since installation.

Help would be appreciated.

---

### Post by mzaam on 2012-08-22
may you can open all the windows with terminal and see what error message u get

---

### Post by wiseguy12851 on 2012-08-23
I've attached 2 screenshots taken with an actual camera since none of the screenshot programs worked. One is of firefox open showing the very flat appearences of the mouse, window, and it's controls as well as other parts of the desktop. The other is of the crash that happens when I try to shutdown.

---

### Post by mzaam on 2012-08-23
for the flat screen, look like u accidentally used old theme, try change your theme, ubuntu tweak or LXappearance may help.

for screenshot can't you just hit printscreen button and paste to LO draw?

---

### Post by wiseguy12851 on 2012-08-23
I have a nice theme picked out and works great, the problem is after all these crashes the theme is one of the ones that goes out as well as the icons I use. The theme switches to an old flat theme and the icons switch as well from humanity to some other icon set.

The flatness is just one of many problems I'm having, larger ones being programs not opening and system programs failing such as nautilus and on to the point where Ubuntu can't even shut itself off (hence error screen attached).

---

### Post by wiseguy12851 on 2012-08-24
I really need help from the community or I'll be left with no choice but to switch back to Windows, I'm trying to permanently ditch Windows but I can't do that if I can't fix errors that popup because they'll just get more numerous, they way I learn to fix errors is by reference, if there is no reference then I turn to the community, if the community isn't helping me then there's nothing further I can do and have to seek other alternatives in operating systems.

I wish I could be more specific but with little error messages and such broad range of issues as well as my inexperience with Linux I don't know where to begin to find the error sources and fix them.

This may help narrow it down though, After scanning through some of the logs, it looks like gtk, nautilus, and gnome are giving off errors, but that's just a small possibility.

Could somebody from the community please help me.

Edit:
I have received 2 error messages before some of the crashes

/usr/bin/nautilus has crashed
 --- nautilus crashed with SIGSEGV in cario_surface_set_user_data()

/usr/lib/gnome-settings-daemon/gnome-settings-daemon
 --- gnome-settings-daemon crashed with SIGSEGV something to do with unable to access memory and segmentation fault, the stack trace is all question marks

---

### Post by black veils on 2012-08-24
all i can offer is:

-  check your hard drive for failures using Disk Utility. in the left pane of the app, choose your hard drive device, in the right pane look at SMART status and SMART data (at top-right)

-  choose memtest from the grub/boot loader menu, to check your ram.

these things can take a long time.

it may not be hardware, of course. do you have windows currently installed on that machine, to see if there is any odd activity there also? (and look at the windows device manager for errors)

---

### Post by wiseguy12851 on 2012-08-25
Checked my hard drive for errors and it passed perfectly. Did a memtest and that passed as well. I don't have Windows or any other operating system installed except for Ubuntu. Ubuntu was 2 days old (From installation) at time errors started.

I think the errors are more specific to Ubuntu such as the GNOME Desktop, Nautilus, or maybe something else Ubuntu specific.

---

