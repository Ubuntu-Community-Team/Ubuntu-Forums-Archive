---
title: "Remove Hibernate from logout menu"
date: 2012-01-05
forum: General Help
---

### Post by gregalynch on 2012-01-05
On the logout dropdown menu in Oneric (the one you get by clicking the gear in the top right) Hibernate is right above Shut Down.  A couple of times now, when I've been meaning to shut down I've accidentally clicked hibernate.  This is a problem because after my machine hibernates I can't figure out how to awaken it again.  I have to do a hard power off and then power on again.

So ...

Either of these would be helpful to know:
1. How do I wake my machine up from hibernate?  Am I just missing something?
2. Is there a way to remove the hibernate option from the logout menu.  This would be preferable, since I only ever click it on accident, anyway.

Thanks

---

### Post by imachavel on 2012-01-05
umm, I thought by clicking the mouse, hitting a key on the keyboard, or simply pushing the power button once lightly that the machine would wake up.

remove the hibernate button from the menu? I suppose ubuntu would be customizable to that extent wouldn't it? I don't know, and before I get guff for giving out bad advice, this guy apparently never got a reply either:

[http://ubuntuforums.org/showthread.php?t=1710747](http://ubuntuforums.org/showthread.php?t=1710747)

---

### Post by 2F4U on 2012-01-06
What are your hardware specs, graphics card and what graphics driver are you using?

---

### Post by gregalynch on 2012-01-06
HP pavilion dm4t laptop, i5 processor with integrated IntelHD graphics card.  I'm not sure what the graphics driver is (how do I find that?).

Keyboard, mouse, and light push of power button don't work to resume from hibernate.  Those were the things I expected would do it, but they don't.

---

### Post by gregalynch on 2012-01-20
bump

---

### Post by guestolo on 2012-01-20
Hibernate never did work that great on my laptop
Suspend works like it should

I removed Hibernate from the logout dropdown 
following this link
[http://askubuntu.com/questions/50443/way-to-disable-hibernate-from-within-gconf-editor-so-button-disappears](http://askubuntu.com/questions/50443/way-to-disable-hibernate-from-within-gconf-editor-so-button-disappears)

---

### Post by gregalynch on 2012-01-21
Worked like a charm - thanks!

---

### Post by guestolo on 2012-01-22
Your welcome, you should mark this thread as Solved

---

### Post by ppqq on 2012-02-03
not solved for me!

Xubuntu 11.10 64bit on Compaq cq40
I followed the trick with the file in 
/usr/share/polkit-1/actions/org.freedesktop.upower.policy

result: no choice of hibernate in power settings (greyed out)
hibernate still appears on the logout menu (but I haven't tried it)

---

### Post by Pilot6 on 2012-02-03
The hibernate problew when some systems do not wake up from hibernate or sleep in 11.10 can be easily solved.
Just install kernel 3.2. That problem started with 3.0 kernel. Now it is fixed in 3.2.

---

