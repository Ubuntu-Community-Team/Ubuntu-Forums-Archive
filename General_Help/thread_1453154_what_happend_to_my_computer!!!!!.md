---
title: "what happend to my computer!?!?!?!?!"
date: 2010-04-12
forum: General Help
---

### Post by Dans564 on 2010-04-12
i was away from my imac (with linux mint 8 installed) for about 30 mins, and when i got back the screen was black and unresponsive (it was on though, I could see the backlight).  Then I did a hard shutdown and powered back on.  When logged in i realized compiz was disabled.  So then I went to check my ati driver was on and i was not.  Tried to activate it and i would not let me.  I also realized that my wifi no longer worked.  Tried to enable that driver (the broadcom driver) and it would let me do that either.  Also, one other thing I noticed that might help diagnose the problem.  I have awn installed with a shiny desktop switcher installed.  Usually it shows 4 desktop, but now it shows 6!  2 rows of 3.

Im pretty good with computers, but this has me very confused.

thanks in advance...

---

### Post by pastalavista on 2010-04-12
> **Dans564 said:**
> i was away from my imac (with linux mint 8 installed) for about 30 mins, and when i got back the screen was black and unresponsive (it was on though, I could see the backlight).  Then I did a hard shutdown and powered back on.  When logged in i realized compiz was disabled.  So then I went to check my ati driver was on and i was not.  Tried to activate it and i would not let me.  I also realized that my wifi no longer worked.  Tried to enable that driver (the broadcom driver) and it would let me do that either.  Also, one other thing I noticed that might help diagnose the problem.  I have awn installed with a shiny desktop switcher installed.  Usually it shows 4 desktop, but now it shows 6!  2 rows of 3.

Im pretty good with computers, but this has me very confused.

thanks in advance...

Are you dual booting? What was the last change you made before you went away?

---

### Post by prodigy_ on 2010-04-12
Have you installed any kernel updates lately?

---

### Post by Dans564 on 2010-04-13
No, I am not dual booting. I have a MAC install on an external hard drive, but I don't think that counts as dual booting.  
What was I doing right before? Nothing other than normal ussage; FireFox, email.  That sort of thing.  Although, on that same uptime, a few hours before, I.had to do some tinkering to get sound to work.

---

### Post by Dans564 on 2010-04-13
Please help my computer is unusable

---

### Post by oldos2er on 2010-04-13
If you've got a LiveCD handy, boot from it and run fsck on your partition(s).

---

### Post by Dans564 on 2010-04-13
thanks oldos2er, i will do that the second i get home.
What do u think might have been the cause of this though?

---

### Post by Dans564 on 2010-04-13
oh and also, cant i run fsck from safe mode without the livecd?

---

### Post by nothingspecial on 2010-04-13
> **Dans564 said:**
> No, I am not dual booting. I have a MAC install on an external hard drive, but I don't think that counts as dual booting.  
What was I doing right before? Nothing other than normal ussage; FireFox, email.  That sort of thing.  Although, on that same uptime, a few hours before, I.had to do some tinkering to get sound to work.

Type ```
history
``` and post the sound related tinkering output, if fsck doen`t throw out any worries.

---

### Post by samigina on 2010-04-13
Maybe yo0ur energy management suspend/hibernate the machine after 30min without use; and maybe the suspen/hibernate option dont work fine in your computer, so it was unable to go back, then you make a brute force shutdown, so something may be broken.

That my May be...

---

### Post by Dans564 on 2010-04-13
dan@dan-desktop ~ $ history
    1  sudo nano /etc/modprobe.d/options
    2  sudo apt-get install compizconfig-settings-manager wmctrl
    3  aptitude install linux-backports-modules-alsa-karmic-generic
    4  sudo aptitude install linux-backports-modules-alsa-karmic-generic
    5  alsamixer 
    6  ./configure
    7  make
    8  make /usr/local/
    9  sudo make
   10  ./make
   11  sudo bash -c "echo 'deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) ubuntu_version main' >> /etc/apt/sources.list"
   12  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
   13  sudo apt-get update && sudo apt-get install avant-window-navigator-trunk
   14  sudo apt-get install python-awn-trunk python-awn-extras-trunk awn-applets-python-extras-trunk awn-applets-c-extras-trunk
   15  sudo apt-get install python-awn-trunk python-awn-extras-trunk awn-applets-python-extras-trunk awn-applets-c-extras-trunk
   16  /.xsession-errors
   17  ./xsession-errors
   18  dmesg
   19  history

---

### Post by Dans564 on 2010-04-13
fsck showed no errors btw

---

### Post by Dans564 on 2010-04-13
also booting the live cd reminded me something.  without the ati driver there are major graphics issues, tearing ect.  But right now there is no tearing just no compositing, even though it says the ati driver is not active.

---

### Post by nothingspecial on 2010-04-13
> **Dans564 said:**
> dan@dan-desktop ~ $ history
    1  sudo nano /etc/modprobe.d/options

What did you change here?

I`m not on to anything but changes to /etc/modprobe can stuff things up.

---

### Post by Dans564 on 2010-04-13
that was when i was trying to get sound to work.  It ended up being successful.
This is the tutorial i followed
 [http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=64&p=84#p84](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=64&p=84#p84)

---

### Post by Dans564 on 2010-04-13
thanks for all your help guys.  But i just fixed it.  Instead of trying to activate the wireless driver first, i tried the ati first.  It activated so i restarted.  On restart all drivers where reactivated.  Very weird bug.  I still dont really under stand what happened.

---

