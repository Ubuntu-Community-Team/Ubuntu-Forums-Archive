---
title: "ubuntu 9.1 internet icon on task bar?"
date: 2009-10-30
forum: General Help
---

### Post by chisle on 2009-10-30
so i decided today that i would take the leap of faith and upgrade from jaunty to karmic kaola. i loved jaunty and never had any issues with it and i know it is in good advice that if it isnt broken don't fix it, or in this case dont upgrade. the upgrade pretty much went flawless accept for a error in installing a package for GIMP, so really no big deal there, nothing of too importance for the system. Anyway, my question is one probably met with a simple answer but yet i havent been able to find the solution. after i upgraded i no longer have the icon for my internet on my task bar. the one that tells me if i am connected to wireless or wired and where i am able to decide what wireless connection to connect to. Any answers on how to put this back on the task bar is appreciated.

---

### Post by Tibuda on 2009-10-30
very weird. press alt+f2 to bring the run dialog, and run
```
nm-applet
```
if you can't see the network manager icon after this, try running this same command from a terminal and see if there's an error message or something.

---

### Post by chisle on 2009-10-30
ok so i ran the code in the terminal and this is what i got. 
"** (nm-applet:2222): WARNING **: <WARN>  request_name(): Could not acquire the session service as it is already taken.  Return: 3


** (nm-applet:2222): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager."

---

### Post by Tibuda on 2009-10-30
this means the network manager was already running. no idea, sorry.

---

### Post by redman5087 on 2009-10-30
exactly the same problem

---

### Post by girto on 2009-10-30
Right click on the task bar on the top, then add to panel. You can add applets from a list. Could it be simply that?

---

### Post by Slim Odds on 2009-10-30
Ubuntu releases are **date based** it's 9.10 not 9.1

October 2009

Tell all of your friends.........

---

### Post by redman5087 on 2009-10-30
There is an empty space on the notification area?
I get the icon back with typing from the shell:
killall nm-applet
nm-applet 

nm-applet is loaded but for some reason is not showing the notification icon.
Strange bug

right-click on the panel, add to panel: doesn't help, the option fort adding
the network applet is gone and this not the problem: the nm-applet is loaded but not showing

---

### Post by mbeach on 2009-10-30
sounds like:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/449910](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/449910)

and:
[http://ubuntuforums.org/showthread.php?t=1274185&page=3](http://ubuntuforums.org/showthread.php?t=1274185&page=3)
although that one is a few weeks old, and appears that the fix had made it into the final release.

---

### Post by redman5087 on 2009-10-30
> **mbeach said:**
> ]

and:
[http://ubuntuforums.org/showthread.php?t=1274185&page=3](http://ubuntuforums.org/showthread.php?t=1274185&page=3)
although that one is a few weeks old, and appears that the fix had made it into the final release.

Thanks for the tip, didn't solve the problem.
Anyone else has an idea?

---

### Post by redman5087 on 2009-10-30
Also, I did an upgrade, not a new fresh install

---

### Post by mlissner on 2009-10-30
Try a reboot? It's old advice, but it might just work.

---

### Post by redman5087 on 2009-10-30
> **mlissner said:**
> Try a reboot? It's old advice, but it might just work.

Nope, already tried that, thanks for the advice

---

### Post by redman5087 on 2009-10-30
Problem solved by using another icon theme, appearently the problem comes up with the SimplyGrey icon theme.
I will look into the problem further

---

### Post by redman5087 on 2009-10-30
> **redman5087 said:**
> Problem solved by using another icon theme, appearently the problem comes up with the SimplyGrey icon theme.
I will look into the problem further

Nope , the problem is the same with all icons themes.
What strange is that:

not only doing "killall nm-applet & nm-applet" temporarily solves the problem until a reboot.
you can also solve the problem temporaly until a reboot with adjusting the panel taskbar height. When you change the height , it magically appear!

Another problem , has Empathy an panel icon? It doesn't show up?

---

### Post by redman5087 on 2009-10-31
any help?

---

### Post by redman5087 on 2009-10-31
problem solved, it seems that it doesn't show up if you set the height of the panel at a certain height, I have set it now to 25 it show up , even when I reboot

---

### Post by gmplague on 2009-10-31
I'm having the same issue, but it appears to be independent of icon theme or panel height. The "Network Manager" applet icon does not appear as an option when I hit "add to panel". 

I've tried un-installing and re-installing the software, but no luck. 

Any other suggestions?

---

### Post by grandtoubab on 2009-10-31
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/435856](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/435856)
Actually, the following workaround worked for me.
 **sudo ln -s /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0**
 Then, restart gdm
 [B]sudo /etc/init.d/gdm restart

[/B]
The new icon is a kind of satellite :KS

---

### Post by redman5087 on 2009-10-31
> **gmplague said:**
> I'm having the same issue, but it appears to be independent of icon theme or panel height. The "Network Manager" applet icon does not appear as an option when I hit "add to panel". 

I've tried un-installing and re-installing the software, but no luck. 

Any other suggestions?

This is another problem which I have also

---

### Post by redman5087 on 2009-10-31
> **grandtoubab said:**
> [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/435856](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/435856)
Actually, the following workaround worked for me.
 **sudo ln -s /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0**
 Then, restart gdm
 [B]sudo /etc/init.d/gdm restart

[/B]
The new icon is a kind of satellite :KS

This doesn't help for me, What I found about it, is that it used to be a bug in 9.10 beta's and alpha, it should be fixed in the final release of 9.10! I already tried that, it doesn't help!

---

### Post by Kevin Z on 2009-11-06
I have same problem after upgrade to 9.10

The network manager icon is missing from the task bar, but apparently it's working. And the network is working fine. Just the icon doesn't show up. But it's a blocker for me, since i cannot access vpn now. 

I have tried almost all suggested resolution above, none of them works for me. 

- Adjust the height of panel bar
- Change Themes
- sudo ln -s /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0 ; sudo /etc/init.d/gdm restart

Any idea ?

---

### Post by Kevin Z on 2009-11-06
No worry about my previous post, it's totally my fault. 

By some reason, i removed "Notification Area" from the panel and i forgot about it, of course the icon is gone. How stupid i am.

---

