---
title: "Menubar Bug for Ubuntu tech wizzes??"
date: 2010-12-20
forum: General Help
---

### Post by ventrical on 2010-12-20
Hi,

 I keep having my little <SHUTDOWN> icon come on and off the menubar using Maveric Meerkat. Like, it will just disappear .. and then come on at random on a re-boot.

Any suggestions?

Acer Aspire 3620,1.5GHz,1.5Gddr,Ubuntu Maveric.

---

### Post by wiebeest on 2010-12-20
> **ventrical said:**
> Hi,

 I keep having my little <SHUTDOWN> icon come on and off the menubar using Maveric Meerkat. Like, it will just disappear .. and then come on at random on a re-boot.

Any suggestions?

Acer Aspire 3620,1.5GHz,1.5Gddr,Ubuntu Maveric.

Same issue here. PC specs are in my signature. Totally different system. 
I suppose it's an unsolved bug.

**BTW:** Logging out and then log back in again does also help. 
No need to completely reboot. 
Re-enabling CTRL+ALT+BACKSPACE as a shortkey to log out makes you able to do so without the ,SHUTDOWN> button visible. 

**_Here's how:_** (source: [theopenhelp.com]("http://www.theopenhelp.com/2010/10/how-to-enable-ctrlaltbckspace-in-ubuntu.html"))
[PHP]The “Ctrl-Alt-Backspace” key combination which was used to restart X was disabled by default 
from Ubuntu 9.04 onwards. 
In order to re-enable this key combo, 
run the following command in your terminal window:

setxkbmap -option terminate:ctrl_alt_bksp
or

Go to System->Preferences->Keyboard menu.
Select the “Layouts” tab and click on the “Layout Options” button.
Then select “Key sequence to kill the X server” 
and enable “Control + Alt + Backspace”.[/PHP]

---

### Post by ventrical on 2010-12-20
Thanks.  I got it back. There is another thread on this I just noticed.

Will be back.

---

### Post by ventrical on 2010-12-20
other thread here
[http://ubuntuforums.org/showthread.php?p=10262145#post10262145](http://ubuntuforums.org/showthread.php?p=10262145#post10262145)

---

