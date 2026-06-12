---
title: "Cannot Display This Video Mode"
date: 2006-06-04
forum: General Help
---

### Post by JaredG on 2006-06-04
I did a fresh install of Ubuntu twice on my Windows XP machine. Each time I've done it, I've completed the installation. When the time comes I need to log onto my account, the left screen (Running dual monitors, two dell monitors) is black and contains this message: ' Cannot Display This Video Mode'. However, the right screen has the logon screen. When I go to log on, the desktop is completely blank, and it never fixes itself.

I've tried all the fail-safe modes. Please help!

My version is the Breezy Badger Ubuntu 5.10.

---

### Post by blackjack6.21.91 on 2006-06-04
You probably need to configure your system to work for two monitors.  Try a google search or if someone here knows how??

---

### Post by JaredG on 2006-06-04
Thats the problem, I don't know how to configure it considering I can't get into the desktop. ](*,)

---

### Post by taurus on 2006-06-04
What video card do you have?  Maybe you want to make it real simple for you first.  Use one monitor to get X running and then search for "twin view" to configure for two monitors...

[http://www.ubuntuforums.org/showthread.php?t=59650&highlight=twin+view](http://www.ubuntuforums.org/showthread.php?t=59650&highlight=twin+view)

---

### Post by JaredG on 2006-06-04
eVGA 7800 GT OC SE.

Thats the thing.. there IS display on the right monitor, I can log in, just nothing shows up on the bronze-coloured desktop. It's just a blank-bronze display.

---

### Post by JaredG on 2006-06-04
Bump. I need help with this soon :-)

If not.... I'm taken er' off and putting SuSE on!! Oh noes! [-(

---

### Post by JaredG on 2006-06-04
Anyone.... ?](*,)

---

### Post by jobezone on 2006-06-04
Did you try what **taurus** said? Stick with only one monitor for now, then follow the link he gave.

---

### Post by tarkus on 2006-06-04
If you press Ctrl-Alt-F1 it will drop you to a console login - that should allow you to edit your /etc/X11/xorg.conf if need be...

---

