---
title: "Meerkat Maverick only Restarts, Wont Shutdown."
date: 2010-11-07
forum: General Help
---

### Post by TBerk on 2010-11-07
I can chose Shutdown from the menu but the system gets to the point where the power supply should 'click' and shut off. It doesn't, it cycles and the system reboots.  It wasn't doing this in 10.04, at least not towards the end prior to updating to 10.10 beta/rc/final.

Also, 10.10 didn't do this either, until recently. (Current default = 2.6.35-22-generic)

Here's the funny thing though; if I choose a previous version from the GRUB2 menu, 2.6.32-21-generic for example, the login screen won't allow mouse nor keyboard control but will shut down normally w/ a single, momentary push of the Power Button.

Now, there are folks w/ a seemingly similar problem, but in their case they can't shutdown at all. My trouble is a shutdown just triggers a restart.


TBerk

---

### Post by dino99 on 2010-11-07
at first sight im thinking about a bios setting (mine have it) but i suppose you have not set it to reboot on shutdown :)

logs might be helpfull to find errors about that issue (services and/or apps running behind the scene and refusing to stop, like on a wan/lan with shared data)

---

### Post by TBerk on 2010-11-07
> **dino99 said:**
> at first sight I'm thinking about a bios setting (mine have it) but I suppose you have not set it to reboot on shutdown :)

logs might be helpful to find errors about that issue (services and/or apps running behind the scene and refusing to stop, like on a wan/lan with shared data)


Thx Dino.  

- Tried different BIOS Settings, no PXE or Wake On LAN setting active, no change w/ 'how to handle Sleep Mode' (S1 vs S3 states), etc.

(btw- I'm running a dual core Intel Pentium @ 3Ghz, 2Gig RAM, on an old Gateway [re: Intel OEM] motherboard.) There is no 'latest BIOS update for me...

- The system was working OK w/ Meerkat but at one point I bork'd my GRUB2 during my current kludgey shutdown procedure (catch the system during restart and prior to POST, hit the power button one time...).  

I've since recovered a GRUB2 menu but I hadn't changed anything (hardware, bios) to cause this in the 1st place; either a 'apt-get upgrade' or Synaptics update did it.

Any clue which logs I'm looking to post?, (gimme a Terminal Command, I can take it...).


TBerk

---

### Post by dino99 on 2010-11-07
what to fight ?

- if you have some doubts about grub2: remove/purge then reinstall it with synaptic

- if the keyboard keymap is corrupted (or have had issue with it (coffee, ...): clean it, check it settings into: system pref keyboard

be sure of the model detected

---

### Post by blueridgedog on 2010-11-07
Try the following, you can always back out if it is not the solution:

```
sudo gedit /etc/default/grub
```

and change:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci"

Then run:

```
sudo update-grub
```

shutdown then restart, then see if it will work as expected.

---

### Post by TBerk on 2010-11-07
> **blueridgedog said:**
> Try the following, you can always back out if it is not the solution:

```
sudo gedit /etc/default/grub
```

and change:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci"

Then run:

```
sudo update-grub
```

shutdown then restart, then see if it will work as expected.


I am not sure this is going to help me; I have no '/etc/default/grub'

```
$ ls /etc/default/ -a
.             apport         cron    irqbalance  rcS                tmpfs
..            avahi-daemon   cups    kerneloops  rsync              ufw
acpid         bootlogd       dbus    locale      rsyslog            useradd
acpi-support  brltty         devpts  ntpdate     saned
alsa          console-setup  halt    pulseaudio  speech-dispatcher

```

Plus, from what I have read that is a command/setting useful for folks who  cant reboot/shutdown except by holding the power button in and cutting power manually. In my case a Shutdown command, either from the command line or from the pull-down menu, ala GUI, just shuts down, then bounces the power supply creating a Restart.

Keep trying though.


TBerk
and in the interest of trying, I'll create that file and try it, but wouldn't I be entering THIS code?:

```
sudo update-grub**2**
```

---

### Post by TBerk on 2010-11-07
> **dino99 said:**
> what to fight ?

- if you have some doubts about grub2: remove/purge then reinstall it with synaptic



OK, sounds reasonable. I think this should accomplish that:

```

$ sudo apt-get purge grub2

```


> 


- if the keyboard keymap is corrupted (or have had issue with it (coffee, ...): clean it, check it settings into: system pref keyboard

be sure of the model detected

Now I'm puzzled, why would the keymap have anything to do w/ it? I'll check the settings though, I can even swap it out to divide and conquer...

[checking keymap via   ...wait, I don't have anything under System.Preferences.Keyboard except Keyboard Shortcuts. I haven't ever changed those.

Hmmm....

---

### Post by TBerk on 2010-11-07
OK, so I used the Synaptic's 'complete removal' option for grub-pc & grub-common. 

Now I'm going to reinstall GRUB2 (a dummy package that will reinstall grub-pc & grub-common.)

Then a reboot.

And I have my LiveCD nearby to recover from if this all goes horribly wrong somehow. 


TBerk

---

### Post by TBerk on 2010-11-07
Well, one "Oh No!" & one "Aha!" moment a piece; 

Synaptic's purge of GRUB and reinstall didn't help w/ the shutdown = restart trouble. (That was the Oh No! part.)

The 'Aha!' is that [*now* I _do_ have a
```
/etc/default/grub
```  to edit on. 

I'll try that next...

(edit) Well, that seems to do nothing whatsoever.

OK, I'm back to enticing Google to be my friend, and Forum Dumpster Diving and what the heck, logging bugs that no one will believe I actually have. (sigh)...


TBerk
thx fellas

---

### Post by Nemo_bis on 2011-02-25
There's a bug for this, [#654042]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/654042") (from the original poster of [http://ubuntuforums.org/showthread.php?t=1586979](http://ubuntuforums.org/showthread.php?t=1586979)).

---

### Post by njined on 2011-02-26
reply is here and please subscribe to the bug report.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/654042](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/654042)
Thanks
Fabio

---

