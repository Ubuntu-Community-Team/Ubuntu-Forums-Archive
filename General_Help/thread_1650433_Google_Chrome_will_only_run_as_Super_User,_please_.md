---
title: "Google Chrome will only run as Super User, please help"
date: 2010-12-21
forum: General Help
---

### Post by Nerotriple6 on 2010-12-21
Hello.

After I updated Ubuntu I ran into some problems. I shall describe it as best as I can.

First after reboot Ubuntu failed to mount my /home directory in which I have a hard drive mounted. I pressed "M" as prompted for manual mount in the shell and mounted /dev/sdc1 as /home successfully.

I am working to fix (if possible) some bad sectors on another hard drive (/dev/sdb1) which is supposed to have Ubuntu and Windows swap files on separate partitions. So at the moment I am running without swap at all in Ubuntu.

Well I logged into Ubuntu and proceeded to continue the attempted fix of bad sectors but Chrome wouldn't start. I tried Firefox it started so I tried running "google-chrome" in the command line and got errors and Chrome failed to start again.
I tried re-installing Chrome. And something else, not sure what helped but I'm one step closer. I will list my current errors below.
Compiz doesn't seem to be loaded correctly with my theme. (I tried Compiz --replace which didn't do any good).

Operating system: Ubuntu 11.04 Natty Narwhal 32-bit (Released April 2011..?:confused::confused:) (How long did I sleep..?)
Google Chrome version 8.0.552 from the stable rep.

Ok, now Google Chrome starts when I start it normally from Terminal, but there is some weird transparency going on. It seems to be in the transparency I set in Compiz for windows in front of the one the mouse pointer hovers on. (If I explained that well enough). When starting Chrome as super user this is not a problem.

Here is my terminal output:
```
nero@HAL9000SYSTEM:~$ google-chrome

(google-chrome:1623): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
[1623:1623:69580447:ERROR:chrome/common/json_pref_store.cc(48)] Error reading Preferences: Can't read file. /home/nero/.config/google-chrome/Local State: Permission denied
[1623:1623:69741978:ERROR:chrome/common/json_pref_store.cc(48)] Error reading Preferences: Can't read file. /home/nero/.config/google-chrome/Default/Preferences: Permission denied
nero@HAL9000SYSTEM:~$ sudo google-chrome
[sudo] password for nero:
```

Please help me, and I'll tell Santa about you. ;)

***EDIT: I have searched on Google and tried several solutions. Please help me.***

---

### Post by Verbeck on 2010-12-21
try
```

sudo chown -R nero:nero /home/nero/.config/google-chrome

```> **Nerotriple6 said:**
> Hello.
Operating system: Ubuntu 11.04 Natty Narwhal 32-bit (Released April  2011..?:confused::confused:) (How long  did I sleep..?)

you didn't oversleep :P, its a bug in one of the updates (according to launchpad)

---

### Post by Nerotriple6 on 2010-12-21
LOL well that's really good news. If I overslept for 6 months I think my boss would give me the sack hahahaha. :p

Thanks you very very much Verbeck. Chrome works almost like a charm now. I will give Santa an offer he can't refuse and tell him to put your wishlist on the top. :D

sudo chown -R nero:nero /home/nero/.config/google-chrome

Seemed to do the trick but the buttons for the BB editor doesn't seem to work on this forum anymore. I will mark this as solved but I wonder if something else is wrong. I will do some testing.

Thanks a bunch and merry christmas. :D

***EDIT: LOL I forgot ...OMG.. See attachment please. Uhmm I can't attach... Err Not solved, but one step closer, thanks.
Please look at image.

[img]http://sphotos.ak.fbcdn.net/hphotos-ak-ash2/hs560.ash2/148218_483480179770_841414770_5597170_5978577_n.jpg[/img]

---

### Post by Verbeck on 2010-12-21
still permission issues...
[s]sudo[/s] chmod -R 775 /home/nero/.config/google-chrome
 
or if you dont mind loosing bookmarks/personal settings
mv /home/nero/.config/google-chrome /home/nero/.config/google-chrome.backup
and restart chrome

---

### Post by Nerotriple6 on 2010-12-21
Thanks a lot, Chrome starts normally. You are my hero today!

Also thanks for warning me about bookmarks, I need them for my swapfile and bad sectors fixing.


sudo chmod -R 775 /home/nero/.config/google-chrome
Did the trick

---

### Post by Verbeck on 2010-12-21
glad it got fixed
remember to mark the thread as solved from thread tools at the top

---

