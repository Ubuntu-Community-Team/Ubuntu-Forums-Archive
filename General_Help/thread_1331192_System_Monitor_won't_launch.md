---
title: "System Monitor won't launch"
date: 2009-11-19
forum: General Help
---

### Post by xxhopingtearsxx on 2009-11-19
I've tried many things and system monitor just won't launch. The dock blinks when I try loading it and that's it.. Help.

---

### Post by emigrant on 2009-11-19
what is the output for this:

```
/usr/bin/gnome-system-monitor
```

---

### Post by xxhopingtearsxx on 2009-11-19
```
joey@ubuntu:~$ /usr/bin/gnome-system-monitor

** (gnome-system-monitor:3369): WARNING **: SELinux was found but is not enabled.


GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to class after it was derived
aborting...
Aborted
joey@ubuntu:~$ 


```

Btw I'm using Gnome2-Globalmenu.. Just thought you might need to know that since I saw the words "GtkMenuBar".

Tried installing but I got:

```
joey@ubuntu:~$ sudo apt-get install selinux 
[sudo] password for joey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  selinux: Conflicts: apparmor but 2.3.1+1403-0ubuntu27.2 is to be installed
E: Broken packages

```

---

### Post by emigrant on 2009-11-19
this would help
untick gnome global menu by going to

```
gconf-editor
```

apps>gnome_setting_deamon>gtk_modules

[IMG]http://2.bp.blogspot.com/_DPdQE6b-uQw/SZ3B2bdxirI/AAAAAAAAABc/JDmNlT8_2HM/s1600/Screenshot-Configuration%2BEditor%2B-%2Bgtk-modules.png[/IMG]

---

### Post by Peter K Nicol on 2009-11-21
I thought I was there but unfortunately when I get to the gtk-modules screen there is only 1 entry, the first one-  gail:atk-bridge....
(I have the same problem - SELinux not enabled).
I am using 9.10 and system monitor appears on the screen as a mess of blue and red with no visible text or icons although it can be closed on clicking where the cross should be. 
Any suggestions would be welcome.

---

### Post by ROY.G.BIV on 2009-11-21
its complaining about apparmor not being installed... what happens when you try?

---

### Post by Peter K Nicol on 2009-11-22
Thanks for the reply. Apparmor is installed so I re-installed it and rebooted but the message is the same 

** (gnome-system-monitor:2463): WARNING **: SELinux was found but is not enabled. 

I now know there is a bug associated with this problem but I do not understand how to fix it.

---

### Post by Vostrocity on 2009-11-28
Same problem here. Please link to a solution if anyone's found it.

@Peter Are you using Global Menu? If not I think you might have a different issue.

@emigrant I did notice that Global Menu was preventing System Monitor from opening, in fact when I reenbabled it with System Monitor open System Monitor instantly disappeared. Do you know why there's a conflict and if there's a workaround for it?

---

### Post by raktarok on 2009-11-28
@Vostrocity
Gnome global menu from this ppa works fine in karmic and does not conflict with gnome-system-monitor. (he is one of the developers, I believe) Remove the old global menu, add this ppa to your sources, and install the package again. 
[https://launchpad.net/~abhidg/+archive/ppa](https://launchpad.net/~abhidg/+archive/ppa)
Hope this helped!

---

### Post by Vostrocity on 2009-11-28
Thanks for the response. That worked beautifully. Now I have my System Monitor back. :D

---

### Post by arboreal on 2010-01-07
Peter and others who aren't running Global menu.  If you look up the bug it mentions strace to figure out what causes System Monitor to not load.

If you enter this in a terminal
```
strace /usr/bin/gnome-system-monitor
```


it will give you an output which shows the error at the end.  For me it was a problem associated with the names in glass-icons that I use.  The other posts in the bug look like the main issue for other folks are also icons that have different names that system monitor is looking for and can't find.
I needed to make some symlinks to icons and everything worked fine.  (I remember having to do the same with this icon set when I upgraded to Jaunty and it was looking for different icon names).

Best

---

