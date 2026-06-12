---
title: "monitor wont stay on"
date: 2010-02-10
forum: General Help
---

### Post by fasmide on 2010-02-10
Hello

I'm having this problem with a older ibm thinkcentre with some:
[INDENT]00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
[/INDENT]video controller in it. 

The problem is the monitor connected has to stay on all the time, but something keeps shutting down the video card then the machine has been idle for some time, and the monitor goes "No video signal" until someone touches the mouse or keyboard.

The system is the newst updated 9.10, and ive set "Put monitor to sleep = never" in the power management settings. Ive also disabled the screen saver. 

Now, i dont think its Xorg that shut the video card down, i believe its the framebuffer (or kernel console or whatever its called). If i jump to the console with ctrl-alt + F1, log in and turn off Xorg with lets say sudo service gdm stop, the video card still turns off after like 15-20 minutes.

Other things ive tried:
completely disabling framebuffer in the grub configuration (with vga=normal and nofb and even combining both, this however doesn't  really disable the high resolution framebuffer at all. Its still on now matter how much i try to disable it..hmm (and the grub settings is used by grub as I'm able to set nosplash witch is effective))

and the last thing I've tried was setterm -powersave off, no luck there.

Before thinking it may be the console doing the video poweroff, I tried disabling DPMS in Xorg config, (and disabling it with xset) this dosent help, although i'm able to turn on the video signal again from a ssh session with xset -dpms -display :0.0 or xset dpms force on -display :0.0. However after some idletime the video signal shutsdown again. 

The only solution i can think of right now is to do some bash script with some infinite loop doing xset dpms force on -display :0.0 every 1-2 minutes or something like that, but erhm .. any thoughts?

---

### Post by gmargo on 2010-02-10
I found a clue here: [http://alexis.m2osw.com/console.html](http://alexis.m2osw.com/console.html)

If you set the blank timeout to zero and the VESA powerdown to zero, you should hopefully get what you want.  I have confirmed that zero does not blank it immediately (which would be really fun!).  But I haven't waited long enough to see if it is totally disabled. [Update: more than 30 minutes and still no blanking!]

Arrange for this to run at boot time:
```

#!/bin/bash
# See `man console_codes` for more info
# Don't blank screen 
# Don't powerdown
echo -e "\033[9;0]"  >/dev/console
echo -e "\033[14;0]" >/dev/console

```

---

### Post by fasmide on 2010-02-11
> **gmargo said:**
> 
```

#!/bin/bash
# See `man console_codes` for more info
# Don't blank screen 
# Don't powerdown
echo -e "\033[9;0]"  >/dev/console
echo -e "\033[14;0]" >/dev/console

```

yay that actually did the trick when viewing the framebuffer console, however, not the Xorg session. 

Well, I guess it's the Xorg Session I should focus on, now the framebuffer console don't turn of the video card anymore :) 

at least that's a little progress, thanks :)

---

### Post by patchwork on 2010-02-11
You could try adding the line

```
Option "DPMS" "False" 
```

to the "Monitor" section of your xorg.conf if your monitor supports this

see the man page in the Monitor section for more info

```
man xorg.conf
```

---

### Post by scouser73 on 2010-02-11
> **fasmide said:**
> Hello

I'm having this problem with a older ibm thinkcentre with some:
[INDENT]00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
[/INDENT]video controller in it. 

The problem is the monitor connected has to stay on all the time, but something keeps shutting down the video card then the machine has been idle for some time, and the monitor goes "No video signal" until someone touches the mouse or keyboard.

The system is the newst updated 9.10, and ive set "Put monitor to sleep = never" in the power management settings. Ive also disabled the screen saver. 

Now, i dont think its Xorg that shut the video card down, i believe its the framebuffer (or kernel console or whatever its called). If i jump to the console with ctrl-alt + F1, log in and turn off Xorg with lets say sudo service gdm stop, the video card still turns off after like 15-20 minutes.

Other things ive tried:
completely disabling framebuffer in the grub configuration (with vga=normal and nofb and even combining both, this however doesn't  really disable the high resolution framebuffer at all. Its still on now matter how much i try to disable it..hmm (and the grub settings is used by grub as I'm able to set nosplash witch is effective))

and the last thing I've tried was setterm -powersave off, no luck there.

Before thinking it may be the console doing the video poweroff, I tried disabling DPMS in Xorg config, (and disabling it with xset) this dosent help, although i'm able to turn on the video signal again from a ssh session with xset -dpms -display :0.0 or xset dpms force on -display :0.0. However after some idletime the video signal shutsdown again. 

The only solution i can think of right now is to do some bash script with some infinite loop doing xset dpms force on -display :0.0 every 1-2 minutes or something like that, but erhm .. any thoughts?

Try Caffeine to keep your monitor on, use these command in Terminal.

> **sudo add-apt-repository ppa:caffeine-developers/ppa**

> **sudo apt-get update**

> **sudo apt-get install caffeine**

[http://www.webupd8.org/2009/10/caffeine-10-for-linux-released.html](http://www.webupd8.org/2009/10/caffeine-10-for-linux-released.html)

Caffeine can be used upto 168 hours & 59 minutes before the screen turns to power saving mode.

I use it on my pc as I was fed up of the screen going black when I was watching a film.

---

