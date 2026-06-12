---
title: "Persistent keymap change"
date: 2012-02-13
forum: General Help
---

### Post by cddt on 2012-02-13
Hi all, I'm running Lubuntu 11.10. 

I can change my keymap to US alternative international by going to preferences -> LxKeyMap. However this change is not persistent, so whenever I reboot my laptop I have to change it again. 

I'm not sure how to do it via the command line. I know to use "loadkeys", but I can't find what the code for this keyboard is...

---

### Post by WasMeHere on 2012-02-13
Hi cddt,

Try ```
setxkbmap
``` according to

[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1839628_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1839628")

If you autostart a terminal window, when the command is entered into [FONT="Courier New"][SIZE="3"].bashrc[/SIZE][/FONT], I think you will get the selected keyboard map for the whole session.

Have fun finding out :-)
Olle

---

### Post by Rodney9 on 2012-02-13
This may help also - 

[http://ubuntuforums.org/showthread.php?t=1874069](http://ubuntuforums.org/showthread.php?t=1874069)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

