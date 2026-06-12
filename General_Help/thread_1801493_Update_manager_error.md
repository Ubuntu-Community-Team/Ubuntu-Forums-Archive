---
title: "Update manager error"
date: 2011-07-10
forum: General Help
---

### Post by Johnsen9000 on 2011-07-10
```
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ubuntu.uib.no_archive_dists_natty_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

```

i don't know what to do.
any help?

---

### Post by drs305 on 2011-07-10
You can run the following from a terminal to remove the list files, which will be regenerated. Be very careful and make sure you either copy or proof the command, as a misplaced space could erase your system:
```
sudo rm -vf /var/lib/apt/lists/* 
sudo apt-get update
```

---

### Post by Johnsen9000 on 2011-07-11
enter wont work, so since i have to enter the password to get it to do the first action, then i can't go on. any idea how to re-calibrate the laptop keyboard? or an alternative command i can use instad of the enter button?

EDIT: never mind, i fixed. don't know how, but i did.
but thank you for the help:D

EDIT 2:The desktop is still not 100%. the firefox  shortcuts doesn't work, the desktop picture doesn't show, the top panel is coverd up when any type of window pops up, and probably abit more. any idea how to restart the settings or search for errors...

EDIT 3: I've reinstalled everything xubuntu there is, and firefox works almost fully. the shortcuts works, but the suggestions doesn't.
but changing and adding work spaces doesn't work, and window manager doesn't work at all. No inputs?

---

### Post by Johnsen9000 on 2011-07-12
Okay, i thought that maybe it was xubuntu that didn't work, so i was gonna install kubuntu and i got this error:
```
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/core.py", line 510, in _set_space
    self._space = dbus.Int32(size)
OverflowError: Value -1940799488 out of range for Int32
```

what can i do to fix this then?

---

### Post by drs305 on 2011-07-12
> **Johnsen9000 said:**
> Okay, i thought that maybe it was xubuntu that didn't work, so i was gonna install kubuntu and i got this error:
```
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/core.py", line 510, in _set_space
    self._space = dbus.Int32(size)
OverflowError: Value -1940799488 out of range for Int32
```

what can i do to fix this then?

When were you getting this error? Given the history, I'd probably backup any important data files and then completely reformat and reinstall whichever release you wish to use.

---

### Post by Johnsen9000 on 2011-07-13
i used it on the airport, watched a film, turned it off. it was abit slow to turn off, but it went okay in the end. then when i started it, this happend. no new programs installed, just a sudden crash. i have reported the problem to ubuntu itself. But im reinstalling i guess. trying out kubuntu this time. heard it's better with hyper threading...

---

### Post by Johnsen9000 on 2011-07-15
I've reformated the whole computer, installed kde for a change, and the problem is back. The computer acts more normal, i can see the edges of the windows and so on, so that's a plus, but the aptdaemon is still there. It started to happen when i tried to install "full Kubuntu Plasma Desktop". but i had "Kubuntu plasma Desktop/netbook system" allready installed. i couldn't find "Full Kubuntu Plasma Desktop/netbook system" without the "Kubuntu plasma Desktop/netbook system" package installed. probably a glitch from my part so i'll try to uninstall the regular and then try to install the full. (just did it, and it just acts up on "full kubuntu plasma/netbook system". I've even uninstalled and installed normal plasma system, and installed another program to check if it happends to any other program.. it installed fine. is there something special with "full kubuntu plasma/netbook system" that should be ignored or be installed differently? and what does full plasma have that normal have not? even tried to install it while using gnome, but nothing.)

But i've reported the error a couple of times on the ubuntu launchpad, so they got the error summary hopefully, but is there any information i can give you to better understand the problem?

im starting to wonder if im not supposed to have the amd 64 version installed.
i've got a brand new laptop from packard bell with pentium i3 processor in it. i know the package i install is called _AMD_64, but i couldn't figure out if it's just amd or if pentium 64 is included. it says on my i3 specs that i have a 64bit instruction set:
[http://ark.intel.com/products/46472/Intel-Core-i3-530-Processor-%284M-Cache-2_93-GHz%29]("http://ark.intel.com/products/46472/Intel-Core-i3-530-Processor-%284M-Cache-2_93-GHz%29")

could this be the problem?

---

### Post by drs305 on 2011-07-15
The amd64 package is for any AMD or Intel 64-bit processor, not just AMD, so that's not the problem. Other than that, you have entered areas I know very little about.  :-(

---

### Post by Johnsen9000 on 2011-07-15
i've solved it.
first off, there where three different problems i think.
1 the crash. i still don't know what caused it, but it crashed.
the first fix fixed the updater, but there still was a problem
2 the window problem was fixed through a reinstall.
3 not all the packages that works with kubuntu can not be installed via gnome, or xfce, only through kde's little program called kpackagekit. kde's own little software manager. if you install some packages in software manager that is not supported through software manager, like kubuntu-full, the error will occour. im now installing kubuntu full through kpackagekit with no problem. but thanks for the help anyway

:D

---

