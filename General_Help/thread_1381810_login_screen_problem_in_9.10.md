---
title: "login screen problem in 9.10"
date: 2010-01-15
forum: General Help
---

### Post by mringer on 2010-01-15
I went from 8.04 to 9.10 and I dont like the way the login screen works.
Instead of you typing your username & password, the screen offers a list
of users. This works if your username is first in the list but not if you
are not first. If I click on (say) John in 3rd place, it usually offers a
small panel with "logon as John" and nowhere to type John's password. 
It doesnt always do this, usually on about the 5th try I do get a place 
to type John's password. 

Please is there any way to revert to the screen as it was in 8.04? I have
looked at previous posts, but as far as I can see they are about changing 
the colours or the background, which I regard as trivial. Thank you.

---

### Post by Brandon Williams on 2010-01-15
A quick forum search for 'karmic gdm config' found [this thread](http://ubuntuforums.org/showthread.php?t=1333683&highlight=karmic+gdm+config), which explains how to make the user list go away so that you type the user name.

---

### Post by mringer on 2010-01-17
THank you for the reply, and the trick suggested in that link does 
change things, but my login screen is still being very un-cooperative. 
It now shows a button labelled "login" and when I click it, most of 
the time it goes direct to the cell for me to enter my password without
giving me any chance to enter my login name first. If I type a password, 
it is then rejected, presumably because it has assumed a different 
username. The login screen does work sometimes, say 1 in 6, I have 
no idea why. Any advice?

---

### Post by Brandon Williams on 2010-01-18
Hmmm ... I've got karmic on 4 different machines, all of them configured to require the user name to be typed in.  I have not had the problem you describe on any of them. That said, I virtually never click the login button. Instead, I just press the enter key. Maybe there's a problem with mouse control for that button in the greeter. On one of my machines, it sometimes takes a few seconds to get the user name entry field after I've pressed the enter key. Is it possible that you are experiencing this delay and clicking the log in button more than once? That's the only thing I can think of.

If you continue having trouble with the login screen and you get to the point where you don't want to spend any more time trying to figure out a fix, you can always down grade to the older version of gdm (after filing a bug report, of course :-)

---

### Post by warfacegod on 2010-01-18
> **Brandon Williams said:**
> If you continue having trouble with the login screen and you get to the point where you don't want to spend any more time trying to figure out a fix, you can always down grade to the older version of gdm (after filing a bug report, of course :-)

Switching to gdm2.20 from 2.28 can be a major hassle. Reconfiguring xorg and what not.

---

### Post by warfacegod on 2010-01-18
I would try reinstalling gdm as a first step to solving this:

```
sudo apt-get remove gdm
```

```
sudo apt-get install gdm
```

---

### Post by Brandon Williams on 2010-01-18
As I indicated above, downgrading to gdm-2.20 should be the final option. However, someone shouldn't need to sink too much time into getting gdm-2.28 working correctly, and switching to gdm-2.20 is an option that isn't too complicated.
[LIST=1]
[*]get the packages: sudo aptitude install --download-only gdm-2.20
[*]log out of X, switch to a console with Ctrl+Alt+F1, and log in
[*]stop gdm: sudo service gdm stop
[*]remove gdm: sudo dpkg --purge --force-depends gdm
[*]install gdm-2.20: sudo dpkg -i /var/cache/apt/archives/{gdm-2.20,libdmx1}*.deb
[*]fix gdm.conf bug: sudo sed -i 's/X11R6\///' /etc/gdm/gdm.conf
[*]restart gdm: sudo service gdm start
[/LIST]

I agree that it's better to try to reinstall gdm-2.28 first, though. It's most likely that the problem is in the config, not the software, so a simple reinstall (sudo aptitude reinstall gdm) will possibly not be enough.
[LIST=1]
[*]download the package: sudo aptitude reinstall --download-only gdm
[*]log out of X, switch to a console with Ctrl+Alt+F1, and log in
[*]stop gdm: sudo service gdm stop
[*]remove gdm: sudo dpkg --purge --force-depends gdm
[*]reinstall gdm: sudo dpkg -i /var/cache/apt/archives/gdm_2.28*.deb
[*]restart gdm: sudo service gdm start
[/LIST]

---

