---
title: "Weird keyboard issue  - SHIFT key dies"
date: 2009-07-16
forum: General Help
---

### Post by swappa on 2009-07-16
Hello
I have what I would describe as a very strange issue with my keyboard layout. Since my Jaunty upgrade I have been fighting some issues with getting AltGr to work, but that seems ok now.



This is my conf today;

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option    "XkbModel"  "pc105"
    Option    "XkbLayout" "no"
## Below is me trying to fix the AltGr problem
    # Option "XkbOptions" "nodeadkeys" 
    Option "XkbOptions" "lv3:lwin_switch"

But;
Whenever I remotely access a server using rdesktop with a different keyboard layout than mine, my SHIFT key stops working when I switch back to my desktop after ending the remote session. It's not like the layout changes to the remote server layout, my SHIFT key apparently just doesn't work anymore. 

Example - SHIFT 7 is supposed to be / on my keyboard, but it just ends up as 7 after i come back from my remote desktop session.

Are there anyone out there who have experienced anything like this, or could shed some light on a possible reason? Maybe my AltGr fix in xorg.conf is making things unstable? 

I do a lot of work remotely so this is really irritating...

Thanks

---

