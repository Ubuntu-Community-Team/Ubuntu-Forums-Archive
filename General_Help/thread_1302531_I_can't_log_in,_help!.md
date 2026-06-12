---
title: "I can't log in, help!"
date: 2009-10-27
forum: General Help
---

### Post by Sam123ni on 2009-10-27
Hello. I was using this internet guide 

[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23]("http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23")

to make my ubuntu look like Mac OS X as an experiment to see how well it worked, but when I got to the stage that had to install the Global Menu Applet it installed alright, but whenever I added it to my panel it said there was an error, and that I should remove it from my directory. I clicked delete, but at this point my computer crashed and I was forced to crash it. When I turned it back on again, the same thing happened; error message and total freezing over of the computer, me being forced to crash it etc. Is there anything I can do about this in the failsafe terminal mode, or will I just have to format my drive and reinstall? If there is something really obvious I could have done, bare in mind that I have only been using Linux for about a month and a half. 

Thank you very much indeed in advance for any help you may give.

---

### Post by Giblet5 on 2009-10-27
Boot to the login prompt.

Flip to the console via CtrlAltF1 and log in (text mode).

```
mkdir dotfile-backups
mv .gconf* .config dotfile-backups
exit
```

Flip back to the GUI login via CtrlAltF7 and log in.

You'll need to reconfigure email, IM, and your interface, but all of your data is intact and you can log in...

---

### Post by Sam123ni on 2009-10-27
> **Giblet5 said:**
> Boot to the login prompt.

Flip to the console via CtrlAltF1 and log in (text mode).

```
mkdir dotfile-backups
mv .gconf* .config dotfile-backups
exit
```

Flip back to the GUI login via CtrlAltF7 and log in.

You'll need to reconfigure email, IM, and your interface, but all of your data is intact and you can log in...

Thank you- I can log in now.

---

