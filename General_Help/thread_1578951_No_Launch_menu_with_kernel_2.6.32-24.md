---
title: "No Launch menu with kernel 2.6.32-24"
date: 2010-09-21
forum: General Help
---

### Post by james.euless on 2010-09-21
I am running Ubuntu 10.04 kernel 2.6.31-22-generic.  On the boot menu, I have the option to run 2.6.32-24, but after the log in screen, nothing happens.  No panels show up.  I can cntl+alt+delete and shutdown, but thats it.  

I do have an older Nvidia card that might be contributing, but I'm just not sure.

---

### Post by MorleyPotter on 2010-09-21
can you Ctrl + Alt + F1?

Then login and type 'startx'

---

### Post by james.euless on 2010-09-22
I tried Ctrl + Alt + F1, but when I type in my user and PW, it says login fail.  I also tried it in 2.6.31-22 with the same results.  It should just be the same user and PW as the GUI login right?

---

### Post by gordintoronto on 2010-09-22
Did you get the case right? "James" is not the same as "james". I'm so used to using the shift key with the first letter of my name, that it is difficult for me to type "gord".

---

### Post by MorleyPotter on 2010-09-22
> **james.euless said:**
> I tried Ctrl + Alt + F1, but when I type in my user and PW, it says login fail.  I also tried it in 2.6.31-22 with the same results.  It should just be the same user and PW as the GUI login right?

Hi James,

Yes - Should be exactly the same.

---

### Post by james.euless on 2010-09-23
OK, the login trouble seems to be because I was using the number pad.  Even wit the num lock on, it didn't like it.  So I logged in and typed startx and this is the result:

Fatal Server Error:
Server is already active for display 0.  If this server is no longer running, remove /temp/.x0lock and start again.

---

### Post by james.euless on 2010-09-27
Apparently I have to solve my own troubles through a lot of trial and error.  The trouble appears to be some sort of conflict between nVidia X Server software and the gnome panel.  

To solve the problem I log in as normal.  There are no panels showing.  Pressing Alt + F1 allows me to get to a terminal.  IN the terminal I type:

$ killall gnome-panel

This restarts the the panels and allows me to get to the nVidia settings.  I just save the new settings (whatever has changed, I'm not sure) and it merges to the xorg.conf file.  Next start up, all is well.

---

