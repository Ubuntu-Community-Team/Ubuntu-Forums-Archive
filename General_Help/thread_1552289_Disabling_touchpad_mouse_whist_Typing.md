---
title: "Disabling touchpad mouse whist Typing?"
date: 2010-08-13
forum: General Help
---

### Post by kgs01 on 2010-08-13
Hello. (Newbee to Linux)

I've installed Ubuntu 10.4 onto Eee Pc 1015PE.

The mouse touch pad is a pain when your typing.

Is it possible to Disable it whilst I'm typing.

(I saw a post somewhere but it somewhere else but it was not very newbee friendly.)

Thanks.

---

### Post by chihwahli on 2010-08-17
I am having the same problem. Most internet pages are outdated. So far I did not find anything about disabling it.  I tried syndaemon -d -t, I get error message: can't open display.  I wonder: Why is such feature not standard for ubuntu? It's a nightmare if you type on a laptop.  Is there really no one who knows how to help us new users? (you wonder why people use windows?? c'mon help us out. Thanks!)

---

### Post by TNT1 on 2010-08-17
Weird... I go to menu/preferences/mouse... There's a touchpad tab, that has a "disable touchpad while typing option"...

Ubuntu 10.04...

---

### Post by chihwahli on 2010-08-17
@TNT1  Thanks, but I m using Ubuntu 10.0.4 LTS standard packages installed, nothing added that would influence mouse etc.  My menu looks like: System / preferences / mouse: I see 2 tabs:    tab general:   mouse orientation, locate pointer, pointer speed, drag and drop, double click timeout     --------------------------------------------------  tab accessibility,simulated second click,dwell click.  I do not have a touchpad tab...or anything with touch pad....=(

---

### Post by TNT1 on 2010-08-17
Ok, look at these:
[http://newyork.ubuntuforums.org/showthread.php?p=9526706](http://newyork.ubuntuforums.org/showthread.php?p=9526706)
[http://www.webupd8.org/2009/11/ubuntu-automatically-disable-touchpad.html](http://www.webupd8.org/2009/11/ubuntu-automatically-disable-touchpad.html)
[http://lgjsheron.wordpress.com/2010/04/21/disabling-annoying-touchpad-while-typing-in-ubuntu/](http://lgjsheron.wordpress.com/2010/04/21/disabling-annoying-touchpad-while-typing-in-ubuntu/)

Maybe you need to install syndaemon?

---

### Post by kgs01 on 2010-08-17
kristian@kristian-netbook:~$ syndaemon -d -t -i
syndaemon: option requires an argument -- 'i'
Usage: syndaemon [-i idle-time] [-m poll-delay] [-d] [-t] [-k]
  -i How many seconds to wait after the last key press before
     enabling the touchpad. (default is 2.0s)
  -m How many milli-seconds to wait until next poll.
     (default is 200ms)
  -d Start as a daemon, i.e. in the background.
  -p Create a pid file with the specified name.
  -t Only disable tapping and scrolling, not mouse movements.
  -k Ignore modifier keys when monitoring keyboard activity.
  -K Like -k but also ignore Modifier+Key combos.
  -R Use the XRecord extension.
kristian@kristian-netbook:~$ syndaemon -d -t -i 1
Unable to find a synaptics device.
kristian@kristian-netbook:~$ 

Syndaemon is installed but not seeing a device?

---

### Post by KeyserSoze93 on 2010-08-17
> **kgs01 said:**
> kristian@kristian-netbook:~$ syndaemon -d -t -i
syndaemon: option requires an argument -- 'i'
Usage: syndaemon [-i idle-time] [-m poll-delay] [-d] [-t] [-k]
  -i How many seconds to wait after the last key press before
     enabling the touchpad. (default is 2.0s)
  -m How many milli-seconds to wait until next poll.
     (default is 200ms)
  -d Start as a daemon, i.e. in the background.
  -p Create a pid file with the specified name.
  -t Only disable tapping and scrolling, not mouse movements.
  -k Ignore modifier keys when monitoring keyboard activity.
  -K Like -k but also ignore Modifier+Key combos.
  -R Use the XRecord extension.
kristian@kristian-netbook:~$ syndaemon -d -t -i 1
Unable to find a synaptics device.
kristian@kristian-netbook:~$ 

Syndaemon is installed but not seeing a device?

Try just running "syndaemon" on it's own, without any parameters.

---

### Post by kgs01 on 2010-08-17
kristian@kristian-netbook:~$ syndaemon
Unable to find a synaptics device.

Still trying?

---

### Post by mocha0range on 2010-09-17
I'm also having trouble figuring out how to do this.

I'm running Ubuntu Netbook Remix 10.04 on an eee 1005PN.

syndaemon reports "Unable to find a synaptics device."

It would appear that I'm NOT using a synaptics device, I'm actually using a virtual device that's calling itself a pair of USB mice. I think this is the necessary setup for multitouch gestures, which is great, but I would rather  sacrifice my multitouch and have the ability to disable the trackpad.

Any ideas how to revert to a simpler setup here?

---

### Post by dmitryme on 2010-09-18
Looks like you have the same problem, which I had have with my Eee PC 1015 - touchpad is not recognized as Synaptic touchpad.

You need to patch & rebuild psmouse.ko module according to this manual:

[http://ubuntuforums.org/showthread.php?p=9175201&highlight=elantechpatch1#post9175201](http://ubuntuforums.org/showthread.php?p=9175201&highlight=elantechpatch1#post9175201)

---

