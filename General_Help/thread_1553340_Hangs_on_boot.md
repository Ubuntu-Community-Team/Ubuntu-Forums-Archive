---
title: "Hangs on boot"
date: 2010-08-14
forum: General Help
---

### Post by PianoMan256 on 2010-08-14
Hi,

I've been running Ubuntu 10.04 on my Toshiba Satellite Pro for a while now, quite happily and successfully, but the other day I accidentally did something stupid, and now it hangs whenever I try to boot it up normally. Here are my symptoms:

Everything appears normal until the part where it should display the splash screen, which it doesn't do--the screen remains black and the system hangs. No key strokes have any effect (including ^C and CTRL+ALT+F[1-7]). Curiously, however, when I push the power-off button, it displays the splash screen for a moment before shutting down. I AM able to "escape" to recovery mode before it hangs, and log in to a terminal as root. No GUI, though, just CLI.

The accidental, stupid thing I did that set it all off was to run an 'aptitude' command (instead of apt-get, which I normally use), and before I knew it, it had promptly auto-removed a whole bunch of packages it deemed unnecessary and obsolete. I couldn't tell you which ones it removed because I'm not that savvy with Linux to know where log files are, etc, etc.

Lastly, in the recovery menu, there was an option "dpkg Repair broken packages", which after a bit of manual page searching, I figured was the same or similar to "apt-get update" or "apt-get dist-ugrade". In any case, I've tried them all (even more aptitude commands) and as far as I can tell, it has repaired whatever packages it thought was broken. Now, whenever I try this, I get (for example):

```
root@mylaptop:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0b of additional disk space will be used.
Do you want to continue [Y/n] ? y
Setting up gnome-keyring (2.92.92.is.2.30.3-0ubuntu1.1) ...
/usr/bin/python: /usr/local/lib/libz.so.1: no version information available (required by /usr/bin/python)
dpkg: error processing gnome-keyring (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 gnome-keyring
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have no idea if gnome-keyring is responsible for the system hang. I just put it here in case it's relevant.

I don't know enough about how linux is set up to do things like check log files and change configuration settings, so if you are thinking of suggesting these actions, please include where to *find* these log files and configuration settings. I know my way around the CLI (in a relatively basic way), but don't have a clue about the inner workings of the OS.

Thanks in advance...

---

### Post by PianoMan256 on 2010-08-16
Um... I'm REALLY hoping someone can lend a hand... I'm kinda stuck at the moment...

Here is some more info:
When I log into a terminal (safely), and hit ALT+F7, I get the following messages displayed on the screen:

```
[FONT=Courier New][SIZE=2]fsck from util-linux-ng 2.17.2
/dev/sda1: clean 320204/7151616 files, 10903776/28599708 blocks
 * Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                           [ OK ]
 * Setting sensors limits                                  [ OK ]
Skip stopping firewall: ufw (not enabled)[/SIZE][/FONT]
```

Any guidance, anyone...?

---

### Post by Azazel on 2010-08-20
my system also hangs at "setting sensors limits" but i believe it from a different issue.

have you tried
```
sudo apt-get update
sudo apt-get upgrade
```

you may have to re-install the gnome desktop to get back the missing packages. doing this should keep most if not all of your personal settings.

---

### Post by PianoMan256 on 2010-08-22
It's fixed now, though it's hard to know exactly *how* it got fixed. In my particular case, I think it had more to do with an error that kept popping up in the oddest places, to do with gzopen64: "symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64". After fully removing and reinstalling several GNOME-related packages (just to see if it helped my original problem), I finally stumbled on this website ([https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/151045](https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/151045)), followed its suggestions, finished reinstalling a whole bunch of stuff, reboot, and voila! I'm back in action. Good luck to anyone else who has the misfortune to find themselves in my position.

("We don't know what went wrong any more than we know what went right."--Robin Williams, Awakenings)

---

