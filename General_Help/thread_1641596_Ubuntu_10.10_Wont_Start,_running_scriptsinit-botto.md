---
title: "Ubuntu 10.10 Wont Start, running /scripts/init-bottom"
date: 2010-12-09
forum: General Help
---

### Post by Chiller89 on 2010-12-09
Hi I was wondering if you could help me.
I have had Ubuntu 10.10 AMD64 running perfectly for about three weeks, then the other day, i go to switch it on and nnothing happens, just the blinking cursor.
I boot it in recovery mode and see that it is hanging at Begin: Running /scripts/init-bottom...done

The only way I can get into any sort of terminal to run commands is if I change the boot parameter " ro single" to "rw single"

I have tried many other commands and I can get it to boot.  Any help is appreciated!

Thanks

---

### Post by killfall on 2010-12-15
I am having the same problem. Help would be greatly appreciated.

But when I boot normally it freezes on the login screen. But the clock continues to change so I'm guessing that its an issue with my input.

---

### Post by killfall on 2010-12-15
Just fixed my issue. I managed to find a USB mouse and plug it on on boot. Then when I got to the frozen screen I unplugged it and plugged it back in and the mouse started working. 

I pulled up the onscreen keyboard and logged in. Then had to edit the menus and add the onscreen keyboard to the menu.

Then was asked if I wanted to do a partial upgrade and typed my pass and after rebooted and all is fine now. I assume if you're not asked to do the upgrade that ```
sudo apt-get update; sudo apt-get upgrade
``` would do the trick.

---

### Post by alex86 on 2011-04-28
I had a similar problem

[http://ubuntuforums.org/showthread.php?t=1733840](http://ubuntuforums.org/showthread.php?t=1733840)

The difference was that I could see the login screen. I also solved the problem with a USB keyboard and typing 

```
sudo apt-get -f install
```

which actually detected a problem and solved it.

---

### Post by 1script on 2011-05-25
Thanks for the tip, guys! Fixed my Acer Aspire One netbook which got frozen login screen after a botched attempt to run a routine update on an unreliable hotel WiFi. Plugged USB mouse, then USB keyboard, logged in using those and run 
```
sudo apt-get -f install
``` in the terminal. I'm back in business!

---

### Post by RamWZ on 2011-08-04
Hi guys,
 
I am running into the same issue. I can recover mouse and keyboard functionality by using USB mouse and keyboard as suggested. I can get the on-screenkeyboard as well. But there is no field where I can type my login credentials! I only see the Ubuntu logo and my computer name below it. When I right click on the computer name I get "Ubuntu 10.10". I must be missing something simple. I am relatively new to Linux. How can I log in?? 
 
Thanks for your help in advance.

---

