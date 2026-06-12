---
title: "mouse freeze after hitting enter key"
date: 2012-03-01
forum: General Help
---

### Post by enderlovesjane on 2012-03-01
Hello,

I'm still kinda new to ubuntu and subsequently lubuntu.

I'm running Lubuntu 11.10 on an AspireOne.  So far it's been working well.

The roblem is a mouse freeze.  After every boot, the mouse tends to freeze within the first 3-4 instances of pressing the Enter key.

it's easily unfrozen by entering 

> synclient touchpadoff=0

It's not the end of the world, but i do a lot of group work and my classmates are tired of passing the machine back to me to fix it.

Is there a way to prevent this from occurring?  
can i put this command in the /etc/fstab or something like that?

---

### Post by Tiganjero on 2012-03-01
Since I don't have a clue as to why your mouse is freezing when you press enter, and you also have a solution for it, the only solution that pops to mind is binding the command to the enter key. You can do this in ***System &#9656; Preferences &#9656; Keyboard Shortcuts***, or, if you have desktop effects activated, you're using compiz windowmanager and you'll need to install ***compizconfig-settings-manager*** and add your command in the ***Commands*** preferences. Hope this helps!

Cheers,
George

---

