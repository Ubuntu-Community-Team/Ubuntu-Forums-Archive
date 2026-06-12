---
title: "I can't see the menu bar"
date: 2010-12-27
forum: General Help
---

### Post by sij5183 on 2010-12-27
I just installed Ubuntu 10.04.1 last night and it was fine. I was checking out the applications and everything. I went to bed and shut it off. Now, I turn it on and I can't see either menu bar. The only thing on the screen is the terminal which, thankfully, I made an icon on my desktop for. So, what should I do?

---

### Post by Verbeck on 2010-12-27
is it a white box (terminal) with an ugly font? like [URL="http://mos.futurenet.com/techradar/Review%20images/Linux%20Format/LXF%20131/LXF131.howitworks.xterm_01-420-90.jpg"]this
[/URL] then, you might have accidentally logged in to an xterm session

edit 2: reply to the post below ;
so er.. could you describe it a little more?
do you still have the panel?

---

### Post by sij5183 on 2010-12-27
I haven't seen any kind of whitebox.

---

### Post by garvinrick4 on 2010-12-27
You mean you do not have upper panel?
```
gnome-panel &
```
Does that give you a panel or say there is one running?

---

### Post by sij5183 on 2010-12-27
it says there is one running

---

### Post by garvinrick4 on 2010-12-27
```
gnome-session-save --kill
```
#Should be able to log out and log back in.
#Before log-in look and see if there is a tab on bottom to select gnome desktop and
then login.

---

### Post by sij5183 on 2010-12-27
I just have my terminal icon. and that's it.

---

### Post by garvinrick4 on 2010-12-27
Have you rebooted?
```
sudo reboot
```

---

### Post by sij5183 on 2010-12-27
still nothing

---

### Post by Verbeck on 2010-12-27
could you give a screenshot

---

### Post by sij5183 on 2010-12-27
not really. the screen is just the default ubuntu background image and a terminal icon. that is it. nothing else.

---

### Post by garvinrick4 on 2010-12-27
See what happens when you boot into recovery to low graphics mode, if panels show up look into System/ Admin  to drivers. 
Want to see if you have proprietary drivers for Video card.

---

### Post by garvinrick4 on 2010-12-27
If you hit alt/f1 the menu's will show but is temporary fix. If gnome panel is running like
when you ran gnome-panel & then the gnome panel shortcut keys will work. Right click
on and check properties I think it is, not in gnome now  Make sure they are not in autohide or hide or one of those. What did the recovery to low graphics do?

---

