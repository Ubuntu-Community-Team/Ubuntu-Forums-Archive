---
title: "dosemu keyboard problem - Alt+F10 issue"
date: 2006-05-18
forum: General Help
---

### Post by mykrob on 2006-05-18
I have a friend who installed Ubuntu 5.10 on a system belonging to a pharmacist friend of his, The pharmacist uses and old applicaiton programmed in Wang Basic or something, that requires DOS to operate. He has some newer computers that came with WinXP, which of course, does not have true Dos. My friend, lets call him Don, got the application to run in dosemu and print to an older dot matrix panasonic printer, but has one last headache before he considers this a success..

The user needs to use Alt+Fn key combinations at times for some functions in the application. Pressing Alt+F10 makes the window mazimize instead of issuing the correct key code to dosemu. He has tried running dosemu with the "-k" switch, which is supposed to give full keyboard access to the application..

My guess is that the terminal or window is taking the key commands instead of them ever reaching dosemu..

How can he get around this and allow dosemu to receive the keypresses instead?

Thanks,
-myk

---

### Post by dirwood on 2006-05-18
I'm not sure if this will help with the app, but you can remove the window maximize functionality of Alt-F10 by going to:
System > Preferences > Keyboard Shortcuts.

Find Window Maximize, select it and press backspace.

---

### Post by mykrob on 2006-05-18
Thanks, perhaps that coupled with the -k switch will do the trick for him :)

---

### Post by drpaul on 2006-05-18
Could you find out how "Don" got dosbox to work with his printer?

TIA

Paul

---

### Post by mykrob on 2006-05-23
He was able to get everything working. He has documented everything here:

[http://pcpitstop.invisionzone.com/index.php?showtopic=117960](http://pcpitstop.invisionzone.com/index.php?showtopic=117960)

thanks,
-myk

---

