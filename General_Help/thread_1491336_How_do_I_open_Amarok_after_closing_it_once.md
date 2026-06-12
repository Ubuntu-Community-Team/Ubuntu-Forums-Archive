---
title: "How do I open Amarok after closing it once?"
date: 2010-05-23
forum: General Help
---

### Post by andrewkk on 2010-05-23
This is probably a stupid question, but I haven't been able to figure it out on my own.

If I run Amarok and then click on Amarok -> Quit, the main Amarok window disappears but a tray icon remains:

[IMG]http://img179.imageshack.us/img179/1183/amarokicon.png[/IMG]

How do I open Amarok again?

Choosing Amarok from the main menu does nothing. Running amarok in the terminal produces:

[FONT="Courier New"]multi@aux:~$ amarok
Amarok is already running![/FONT]

Clearly I must just be missing something simple.

---

### Post by happyhamster on 2010-05-23
Left-clicking the tray icon should maximize amarok again. That's how it works on my Jaunty box though.

---

### Post by andrewkk on 2010-05-23
Left-clicking the icon produces the menu shown in the above screenshot. Right-clicking produces the following:

[IMG]http://img232.imageshack.us/img232/1053/screenshothz.png[/IMG]

Middle-clicking does nothing.

---

### Post by happyhamster on 2010-05-23
Just installed amarok on my laptop (lucid), and left-clicking the icon produces the same popup you posted, but it also shows a Restore and a Quit option. Weird. (Clicking the Restore option maximizes amarok again.)

- To restart amarok, run:

killall amarok

- then start it from a terminal to see if you get any output. Other ideas to test: re-login, or choose a different theme, or disable Visual Effects (both found under System-->Preferences-->Appearance). Good luck.

---

### Post by mc4man on 2010-05-23
amarok 2 is yet again broken - (don't use it here, but installed to ck. -see the same, amarok will not exit cleanly

It's again behaving as it did during lucid development - this was a bug filed but was somewhat ignored. (and I guess it resolved itself for a while at least

There is a way to fix  or you can wait it out for a more 'proper' one

To fix now is to install mysql-server-core-5.1 (which will install several other packages)
You'll be asked 2 or 3 times to create a password, I just pressed 'enter' (no password

(or use the old 1.4 (pana fork is good - use here

---

### Post by andrewkk on 2010-05-23
> **happyhamster said:**
> Just installed amarok on my laptop (lucid), and left-clicking the icon produces the same popup you posted, but it also shows a Restore and a Quit option. Weird. (Clicking the Restore option maximizes amarok again.)

I do see this behavior, but only *before* having clicked the Quit menu item. Once I click Quit, Amarok disappears and the tray icon loses the Minimize/Restore and Quit menu items.

> **mc4man said:**
> To fix now is to install mysql-server-core-5.1 (which will install several other packages)
You'll be asked 2 or 3 times to create a password, I just pressed 'enter' (no password

I don't understand why, but this appears to have solved the problem. Thank you! Do you know if there is a bug report for this?

---

### Post by mc4man on 2010-05-23
I believe the issue actually centers around amarok finding/parsing your local collection, the unclean/stalled shutdown being a by-product, installing the mysql server pack's resolves both
bug
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269)

---

### Post by jasontan6 on 2010-05-24
> **mc4man said:**
> I believe the issue actually centers around amarok finding/parsing your local collection, the unclean/stalled shutdown being a by-product, installing the mysql server pack's resolves both
bug
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269)

yes indeed installing mysql-server-core-5.1 fixed it - I also had the problem where Amarok couldn't catalog my files and add them to the collection, and the unclean exit. Thanks a lot for the tip! :)

---

