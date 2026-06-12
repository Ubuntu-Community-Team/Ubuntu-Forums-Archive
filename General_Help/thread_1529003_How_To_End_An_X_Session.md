---
title: "How To End An X Session?"
date: 2010-07-11
forum: General Help
---

### Post by ks07 on 2010-07-11
Hi,
I've just installed ubuntu 10.04 server on an old box to use as a home server for network storage. I've managed to get wireless working, and now have started to tinker with the base system (it's more of an experimental machine than a critical backup server!). I've installed xorg-core and JWM, and have set it up to function as a basic GUI in case my main box goes down and I need access to these forums. I can start JWM by using ```
startx
```, but I need to know how to end the X server from inside the gui, so that I can create a kind of 'exit' button.

I know I can end the session by going back to tty1 with ctrl-alt-f1 and using ctrl-c, but is there a way of doing this from inside of the gui? Is it even possible? :P

---

### Post by ks07 on 2010-07-11
:rolleyes: :lolflag:

I must be a bit slow today, in the .jwmrc documentation ([see here]("http://joewing.net/programs/jwm/config.shtml")) it shows a few ways of ending JWM, including an aptly named 'exit' item that can be easily added to the menu. I also read the command 'jwm -exit' will work as well.

MArking thread as solved. :p

---

