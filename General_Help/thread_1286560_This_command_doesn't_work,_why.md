---
title: "This command doesn't work, why?"
date: 2009-10-09
forum: General Help
---

### Post by TwinStinger on 2009-10-09
*noob warning on TwinStinger*

Hi, can't figure out why this command doesn't work.

terminator --command=atq
 
          or

terminator --command="atq"

A terminator screen opens up for a micro second but that's all.

Get a lot of different png's missing 
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:54: Unable to locate image file in pixmap_path: "stock_bottom.png"

But I get these messages on commands that work as well.

Any one with an idea? 

/Twinned

---

### Post by akakingess on 2009-10-09
> **TwinStinger said:**
> *noob warning on TwinStinger*

But I get these messages on commands that work as well.

Any one with an idea? 

/Twinned

You get what messages even when a command works? And all of this is in the terminal, right? Sorry to be so blunt.... If you could provide just a little more info like what you are trying to do and what messages you are getting (unless it's the one about missing pngs) that might help us sort it out, of course knowing some of the bright people on this forum they may not need anymore clarification like I do.

---

### Post by TwinStinger on 2009-10-09
When the command is launched in terminal I get these messages 

/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:99: Unable to locate image file in pixmap_path: "stock_apply.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:104: Unable to locate image file in pixmap_path: "stock_cancel.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:109: Unable to locate image file in pixmap_path: "stock_ok.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:114: Unable to locate image file in pixmap_path: "stock_apply.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:119: Unable to locate image file in pixmap_path: "stock_refresh.png"
twinned@twinned-laptop:~$ 

But when launching other commands that opens a terminal and executes a command it works even tough I get the same messages. 

What I'm trying to accomplish is make an entry in my openbox menu that opens a terminal window and shows me queued at-jobs.


/ Twinned

---

### Post by OpenGuard on 2009-10-09
```
terminator --command="atq && read confirm"
 
```

Still immediately closes ?

---

### Post by TwinStinger on 2009-10-09
Openguard

Thank you!
Works great.

A lot to learn about command line.... 8-[

/ Twinned

---

