---
title: "Ubuntu stopped working"
date: 2011-04-19
forum: General Help
---

### Post by miutsu on 2011-04-19
I orriginally posted this here "http://ubuntuforums.org/showthread.php?t=1732716" but no one responded after 14 hours and I think that I put this in the wrong spot.

> 
After Installing an nvidia driver my computer does not work. I uninstalled it and am having the same problems. When I try to boot I get the ubuntu logo and then the terminal comes up flickering when I try to type in my user name and password the buttons only work sometimes so I can't log in that way.

Later I tried to get in using recovery mode, which worked and after tring to start X it told me that I don't have any drivers. I can't get the actual message but it listed the nvidia module and my previous driver and said that neither was there.


---

### Post by Tclarkie on 2011-04-19
boot up
when it gos to grub, select recovery boot
let it loadand then scroll to "boot with failsafe X"
select reconfigure x
select reboot

---

### Post by nothingspecial on 2011-04-19
What happens when you type ```
jockey-text
``` in recovery mode?

Does it list any drivers?

You will need a wired internet connection for this.

---

### Post by Tclarkie on 2011-04-19
> **nothingspecial said:**
> 
You will need a wired internet connection for this.
and selec the option that allows networking in the recovery menu

---

### Post by miutsu on 2011-04-19
> **Tclarkie said:**
> boot up
when it gos to grub, select recovery boot
let it loadand then scroll to "boot with failsafe X"
select reconfigure x
select reboot

I don't have that option, I am using Ubuntu 9.10



I ran jockey-text, but didn't get anything.

---

### Post by Cypher2 on 2011-04-20
Try accessing another computer if possible and download and burn yourself the latest stable live image to access tour device and just clean it up after a backup.

I'm not saying it just like that: 9.10 is history compared to all the new WONDERFUL things that have been going on with Ubuntu eversince...

Try that as a rescue.. it'll work I bet you

---

