---
title: "Gnome/XORG freezes when closing the laptop lid"
date: 2011-05-17
forum: General Help
---

### Post by IQAndreas on 2011-05-17
Gnome (or XORG, I'm not sure which name to give it) freezes up not always, but about once every 24 hours after I close the laptop's cover/lid. I know this happens when I close the lid rather than open it judging by the time the clock is locked at.

The cursor will move around on the screen, but noting will react to it in any way. Other services such as FTP and Samba still work just fine when the computer is "locked down". 

Without more details to why the problem is ocurring, I have no idea what to search for or where to get started solving the problem.

I have attached the XORG logs (found in var/log) in case they are of any use. If anything else is needed, let me know.

---

### Post by wildmanne39 on 2011-05-17
> **IqAndreas said:**
> Gnome (or XORG, I'm not sure which name to give it) freezes up not always, but about once every 24 hours after I close the laptop's cover/lid. I know this happens when I close the lid rather than open it judging by the time the clock is locked at.

The cursor will move around on the screen, but noting will react to it in any way. Other services such as FTP and Samba still work just fine when the computer is "locked down". 

Without more details to why the problem is ocurring, I have no idea what to search for or where to get started solving the problem.

I have attached the XORG logs (found in var/log) in case they are of any use. If anything else is needed, let me know.
Hi, I just wanted to let you that I looked at the files that I could open and I did not see anything that would cause your problem from the files, but I am not an expert.:D

---

### Post by quantumfunk on 2011-06-13
I have this problem as well in Gnome3. The only way I could solve it was by changing the setting to 'do nothing' when lid was closed. It seems the problem comes from the 'suspend' option. Hibernate doesn't seem to do it *as much*. I was wondering if you got any further in your exploration of this problem, or perhaps anybody else can share some insight.

---

### Post by IQAndreas on 2011-06-14
Nope, even with the most up to date version (public release, not nightly build) I'm still having problems with it (and it's getting quite difficult to deal with all the time!

I still haven't found any way to get out of the freeze in any way other than holding down the power button and killing the computer. Is there any "magic key combination" which will restart XORG or whatever is the root of the problem?

I am able to hit the sleep button to cause the laptop to "snooze" like it would normally, but waking up from that sleep just returns me to a locked up desktop. :(


These problems didn't start until I upgraded to 11.04, if that helps diagnose the problem.

---

### Post by Halverneus on 2011-07-01
I'm having a similar problem. You can restart Xorg by going to your System Settings->Keyboard->Layouts->Options->Key Sequence to Kill the X Server and place a check next to ctrl+alt+backspace. Next time it locks up, just press that key combination and log back in. (Something I always enable after an install)

---

### Post by IQAndreas on 2011-07-03
> **Halverneus said:**
> Next time it locks up, just press that key combination and log back in.
Perfect! Thank you so much. It crashed on me just a few hours ago, and restarting it that way did the trick.

I just wish all currently running programs wouldn't have to restart as well. This is getting quite difficult. :/


Anyway, I fiddled around with the screensaver and power settings, but it didn't seem to make any difference.

One thing I have found is, time between closing and opening the lid makes no difference. It has sometimes gone 3 minutes to overnight and it's frozen, or 3 minutes to overnight and yet it remains in perfect working condition when the lid is opened.


**Can anyone help sniff out the source/details of this problem so we file a proper bug report?** I would be more than happy to upload log files or run nightly builds rather than release builds, or whatever it takes to get this issue solved!

---

### Post by IQAndreas on 2011-08-08
I did another Google search, since this problem is still bugging me (I'm still in Natty)

This bug seems to be just what the problem is. 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/780653](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/780653)
I have activated the "Lock screen when screensaver is active" to see if it will make any difference.


Just one thing I noticed (which may be coincidence) the problem is less likely to occur if on the desktop directly (every window minimized) rather than having a Window such as Chrome open. Could just be a fluke, as I have only tested it a few dozen times so far.

---

### Post by IQAndreas on 2011-08-28
Success! I have found a way to stop the freeze from occurring.

It's definitely the screensaver causing the issues. Changing the setting "Lock screen when screensaver is active" seemed to help some of the time, but the problem would still occur frequently.


The problem can be removed completely though by disabling the screensaver entirely. 
[LIST=1]
**Disabling the screensaver**
[*]Go to "System Settings > Personal > Screensaver". 
[*]Uncheck "Activate screensaver when computer is idle."
[/LIST]

The downside is, now you won't have a screensaver, but you can still set the laptop to turn off the screen if the computer is idle for too long, which creates the same effect as having the "Blank screen" as a screen saver.
[LIST=1]
**"Sortof" enabling the blank screensaver** (which doesn't cause Gnome freezes)
[*]Go to "System Settings > Personal > Screensaver". 
[*]Click the button labeled "Power management".
[*]Adjust the "Put display to sleep when idle for" setting for both the "On AC power" and "On battery power" to your liking.
[/LIST]

---

### Post by IQAndreas on 2011-11-03
Great news is the computer has not locked up once since the update to Ubuntu 11.10, so whatever was causing the problem was fixed or no longer exists in the new release.


I have marked this thread as solved (which I have been doing to quite a few of my old threads, sorry for bringing all those old ones to the top again), but it can be closed as well if necessary (I'm not sure what the policy for solved threads is).

---

### Post by IQAndreas on 2012-05-05
I did a complete reinstall when updating to 12.04 and I'm afraid **the problem is back**; even though 12.04 doesn't have the classic style screen savers (but it does still use "gnome-screensaver" which is most likely where the problem is at.

I set the post as "unsolved" again, but I did find an official bug report for this problem. It's quite old, but I hope it will be fixed eventually. :(
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/762918](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/762918)

---

### Post by bradshawd on 2012-05-11
MMMmmmm. Getting the same since an upgrade to 12.04.

Oldish Toshiba M2 which ran 11.10 no problems but as soon as I close the lid now the machine just freezes and refuses to come back up when opening the lid. I am just looking at a backlit screen.

Have yet to try the Kill XORG trick but will give it a go and report back shortly.

Derek

Can report that I have no response from the mouse or keyboard once re-opening the lid. No choice but to power down and power up again.

---

### Post by IQAndreas on 2012-05-13
> **bradshawd said:**
> Oldish Toshiba M2 which ran 11.10 no problems but as soon as I close the lid now the machine just freezes and refuses to come back up when opening the lid. I am just looking at a backlit screen.

Can report that I have no response from the mouse or keyboard once re-opening the lid. No choice but to power down and power up again.By "backlit", do you mean a black screen, but you know the computer is on because the screen is receiving power (because it is giving off a small amount of light)? If so, I do believe you are having a different issue.

In my case, the desktop and any open windows are visible when opening the lid. It looks just fine except the clock is frozen to when the computer froze and nothing reacts to any clicks or typing. It's like someone took a screenshot of the desktop.


> **bradshawd said:**
> Have yet to try the Kill XORG trick but will give it a go and report back shortly.
Just make sure you enable it, as the shortcut is disabled by default.

The setting seems to have moved, but can now be found in:
**System Settings > Keyboard Layout > Options**
Then scroll down to *"Key Sequence to kill XServer"* and make sure it's checked.

---

### Post by IQAndreas on 2012-05-13
I found a solution! *(sort of)*
[SIZE="3"]**EDIT: Nope, solution didn't work.** Eventually I got another screen lockup, and have gotten several more since. [/SIZE]

It was apparent after some searching that gnome-screensaver was the root of the issue (see [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/762918](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/762918) )

So, I uninstalled the package:
```
sudo apt-get remove gnome-screensaver
```

So far (48 hours and counting), I haven't had a single problem! :) (but I'll be sure to report back if I run into any issues)

Note that the "Turn screen off when inactive for x minutes" settings are in "Brightness and Lock" and don't require the gnome-screensaver packages, so I still get a black screen as a "screensaver".

---

### Post by bailunrui on 2012-07-01
Did you ever stumble upon a solution to this problem? I'm having the same difficulties.

---

### Post by IQAndreas on 2012-07-02
> **bailunrui said:**
> Did you ever stumble upon a solution to this problem? I'm having the same difficulties.
No "good" solution, but one something previously seems to be working (though, it may just be a coincidence and the bug was fixed in one of the updates released at around the same time I tried the workaround ;) )

Go to "System Settings > Brightness and lock". Then turn on the options for locking the screen when inactive.

It's quite annoying to have to re-type my password in every time I get on the computer, but you get used to it.

---

### Post by magnuslen on 2012-10-17
Hello man.

Have you tryed disable the Ubuntu native screensaver (Pangolin). It's seems to be the problem.

Just type this on Terminal:

gsettings set org.gnome.desktop.screensaver idle-activation-enabled false


I've found this here:

[http://www.liberiangeek.net/2012/04/disable-screensaver-black-screen-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/disable-screensaver-black-screen-in-ubuntu-12-04-precise-pangolin/)

---

