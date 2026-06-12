---
title: "Ctrl + Alt + F* shortcuts don work (except in terminal 7)"
date: 2010-01-30
forum: General Help
---

### Post by goldencako on 2010-01-30
That's the problem in a nutshell. I can switch to any terminal if I'm originally on terminal 7 with the shortcuts. However, if I'm in a X-less terminal, I have to manually issue the command ```
chvt 7
``` to go back to the X terminal. I had this working until sometime ago and a couple of days ago I realized it wasn't working. I rebooted hoping the problem would go away but it did not. Any ideas?

Thanks in advance,

goldencako

---

### Post by pbrane on 2010-01-30
So if you are in VT7 (the GUI) you can CTRL+ALT+Fx to any of the other VTs, but if you are in a VT other than VT7 you can't ALT+Fx to go to any other VT? You don't need to use the CTRL key if you are in VT1-6 or VT8 but it still should work. 

What do you mean you "had this working until sometime ago"? Those key bindings are the default in most Xorg based systems I have worked on.

I can't think of any reason this wouldn't work.

---

### Post by goldencako on 2010-01-31
> So if you are in VT7 (the GUI) you can CTRL+ALT+Fx to any of the other VTs, but if you are in a VT other than VT7 you can't ALT+Fx to go to any other VT?

Yes.

> What do you mean you "had this working until sometime ago"? Those key bindings are the default in most Xorg based systems I have worked on.

What I mean is that I could switch between VTs at any time with those commands. Now, I can only do it from VT7. I have just tried going to VT8, and I couldn't come back; I had to restart.

> I can't think of any reason this wouldn't work.

Me neither. :(

---

### Post by pbrane on 2010-01-31
You might try re-installing xkb-data. I *think* like this
```
sudo apt-get --reinstall install xkb-data
```
I read in a forum where this fixed a similar problem for someone.

---

### Post by goldencako on 2010-02-01
Now the shortcuts don't work in terminal 7 either. Things like Alt+F2, Ctrl+Alt+D don't work either, while most of the shortcuts in Keyboard Shortcuts work. I'm lost here.

EDIT: Alt+Tab doesn't work!

EDIT2: I think I identified the problem. Alt key is seen as a key called "Mod5", and right Alt is seen as "ISO Level3 Shift"

Any ideas for switching it back?

EDIT3: I was wanting to reinstall Ubuntu, so I just went ahead and did it. No more need to worry.

---

