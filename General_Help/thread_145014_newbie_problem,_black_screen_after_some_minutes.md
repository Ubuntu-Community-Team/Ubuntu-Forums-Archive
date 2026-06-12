---
title: "newbie problem, black screen after some minutes"
date: 2006-03-15
forum: General Help
---

### Post by IGNIZ on 2006-03-15
my screen becomes black after some minutes of inactivity, i totally uninstalled xscreensaver so it's not it, what could it be?

---

### Post by aggiechemist on 2006-03-15
Might be a power management thing, like suspending or hibrenationg after a while. I can't remember off the top of my head where that stuff is stored, but it should be under the preferences or administration menus.

 It happens to me too, but I don't have a screensaver. I've just never tried to change it.

---

### Post by IGNIZ on 2006-03-15
it's not, it's the first thing i thought but it's not it :cry:

---

### Post by aggiechemist on 2006-03-15
Hmmmm well I can try and offer up a few more ideas. Most of the power management stuff is under APCI if I remember right. You might try playing around with that, though I have never done it. You can see what is in the manual files.

You could also try disabling APCI with rcconf (sudo apt-get install rcconf) so that no power management happens when you boot. If it is an APCI thing, it should stop the monitor from going off. Of course, you also won't be able to suspend the computer anymore either.

---

### Post by 5-HT on 2006-03-15
Could be DPMS power management for the monitor kicking in.

 Check if DPMS in enabled for X ```
 xset -q 
``` 
If it is, to disable try ```
xset -dpms 
``` 
I'm not sure if such a change will persist after a reboot, so you may need to get rid of the DPMS option under the monitor section of xorg.conf for a permanent fix if not.

HTH

P.S. I'm hoping 'xset -dpms' will do the trick; as such I haven't gotten into detail about editing xorg.cong. If you don't know how to edit xorg.conf properly post again if needed and I or someone else can walk you through it, but there are many many threads on the topic. If you edit it yourself though, it goes without saying to make a backup of the file beforehand.

---

### Post by IGNIZ on 2006-03-18
thanks, it was that! i deleted the dpms line in xorg.conf and now it doesn't start anymore, thanks a lot!

---

