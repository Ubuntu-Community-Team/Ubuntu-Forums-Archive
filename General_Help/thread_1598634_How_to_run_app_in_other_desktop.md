---
title: "How to run app in other desktop"
date: 2010-10-16
forum: General Help
---

### Post by wgarciamachmar on 2010-10-16
How do I run an app from the terminal in an specific desktop?

I want to make evolution run at start up, but in the second desktop, not the main. I can't figure out how to do this.

---

### Post by hhh on 2010-10-16
I've never tried this, but see if it works for you...
[http://www.ubuntu-inside.me/2009/06/howto-make-applications-start-in.html](http://www.ubuntu-inside.me/2009/06/howto-make-applications-start-in.html)

---

### Post by oregonbob on 2010-10-16
Below is a perl script that I use to run Windows XP as a virtual machine on screen 2  (screens start with zero). Works great. Just change the second to last line to be the program you want to run. The last line makes sure you are in first screen after it runs. You have to install wmctrl command first with "sudo apt-get install wmctrl"

#!/usr/bin/perl
use strict;
use warnings;
system("wmctrl -s 2");
system("VBoxManage startvm Windows-XP");
system("wmctrl -s 0");

I have the above script in my startup so anytime I fire up my system, I always have Windows XP running on screen 2.

Update: I tried the above with evolution command and it didn't work right. Evolution has unusual control/process. The easiest way may be to start evolution manually in the screen (workspace or viewport) you want, then menu System -> Preferences -> Startup Applications -> Options tab -> Remember current applications. I tested it and it worked. I had to start evolution by clicking the little envelope icon in upper right of taskbar. Evolution is weird, you might try this guide to do it:
[http://www.omgubuntu.co.uk/2010/04/workspace-window-placement-hack-choose-which-apps-open-in-which-workspaces/](http://www.omgubuntu.co.uk/2010/04/workspace-window-placement-hack-choose-which-apps-open-in-which-workspaces/)

---

### Post by oregonbob on 2010-10-18
I have been continuing to experiment with start-up applications in specific workspaces. When one gets them all just such a way it is cool.

From my research it appears the best solution is a package called "devilspie" which is available in Synaptic package manager. It appears devilspie can handle the obscurities of evolution and get it right.

I also found this little script works great for starting my Windows XP virtual machine in screen 3 (2):

[COLOR="Blue"]# start-xp - a simple script to start a virtual machine in the third 
# workspace of gnome
wmctrl -s 2
VBoxManage startvm Windows-XP &
wmctrl -s 0
[/COLOR]
I got this to work with evolution, sort-of:
[COLOR="Blue"](wmctrl -s 3 && evolution) & 
wmctrl -s 0 && exit
[/COLOR]

devilspie (and gdevilspie?) allow you to write rules so specific apps always start in specific workspaces. Using workspaces in general sure ups my productivity on Ubuntu.

Hope that helps.

---

### Post by dcstar on 2010-10-18
> **wgarciamachmar said:**
> How do I run an app from the terminal in an specific desktop?

I want to make evolution run at start up, but in the second desktop, not the main. I can't figure out how to do this.
[http://ubuntuforums.org/showthread.php?t=75749t](http://ubuntuforums.org/showthread.php?t=75749t)
[http://ubuntuforums.org/showthread.php?t=844385](http://ubuntuforums.org/showthread.php?t=844385)
[http://ubuntuforums.org/showthread.php?t=898457](http://ubuntuforums.org/showthread.php?t=898457)
[http://ubuntuforums.org/showthread.php?t=913915](http://ubuntuforums.org/showthread.php?t=913915)
[http://brainstorm.ubuntu.com/idea/5448/](http://brainstorm.ubuntu.com/idea/5448/)

And I just found that launching this from my Startup Applications puts FF on my second Workspace at log in:
```
#!/bin/bash

sleep 2 && wmctrl -s1 && firefox &

exit 0
```

---

### Post by wgarciamachmar on 2010-10-18
Thanks. That was very complete. I'll give it a try.

---

