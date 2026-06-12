---
title: "Is it possible to use a Live CD to reset xorg and screen display?"
date: 2011-02-18
forum: General Help
---

### Post by maddbaron on 2011-02-18
Can I copy the setting of the live cd in my current 10.10 build? If Not can I do a new clean install of 10.10 over my current upgraded 10.10 build? My display is screwed & I don't know how to fix it

---

### Post by dabl on 2011-02-18
No, that's not gonna work. There is more involved than just the files in /etc/X11/.

From a Live CD you can do a number of things, including chrooting into the borked installation and running dpkg-reconfigure xserver-xorg, running update-grub, freeing up filesystem space, etc. etc. -- unfortunately your problem description is too vague to know exactly what the problem is.  However, that's a little complicated for a new user.  If you don't have a ton of energy and time invested in the system that you have, reinstallation is probably quicker and easier in this case. (and then don't do whatever you did to bork the video).  ;)

---

### Post by maddbaron on 2011-02-18
> **dabl said:**
> No, that's not gonna work. There is more involved than just the files in /etc/X11/.

From a Live CD you can do a number of things, including chrooting into the borked installation and running dpkg-reconfigure xserver-xorg, running update-grub, freeing up filesystem space, etc. etc. -- unfortunately your problem description is too vague to know exactly what the problem is.  However, that's a little complicated for a new user.  If you don't have a ton of energy and time invested in the system that you have, reinstallation is probably quicker and easier in this case. (and then don't do whatever you did to bork the video).  ;)

my screen resolution is bad, there is a black bar at the bottom blocking the bottom... words and applications are cut off from top and bottom and whats left is difficult to read and everything is the size of how things look in safe graphics mode. 

I then rebooted heard my screen music and the screen in default mode is black. In safe graphics mode I cant minimize or close anything and everything is overlaying one another.

Before this, when I upgraded from 10.04 I was unable to access my desktop & was in an infinite login loop, was told how to reset my xorg.conf then I saw m screen stuttering apparently my ati driver went bad so i had to reinstall that then with that fixed my compiz screwed up and my screen looked like safe graphics mode. 
I removed compiz and now i'm stuck with the above.

I'd rather not reinstall but I don't know what to check or fix to get my resolution & screen back to normal, I am not skilled in the check & repair CLI's

---

### Post by Habitual on 2011-02-18
You could try resetting your panels to default, but this will remove any customizations you may have.

Logout of the desktop (or just don't login on next session)
Ctrl+Alt+F1

login.
```
mv ~/.config ~/.config.org
mv ~/.gconf ~/.gconf.org
exit
```

Login to Desktop and see.

let us know...

---

