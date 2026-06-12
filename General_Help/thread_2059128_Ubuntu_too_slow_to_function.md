---
title: "Ubuntu too slow to function"
date: 2012-09-17
forum: General Help
---

### Post by thedudething on 2012-09-17
My Ubuntu has suddenly gone super slow. I cannot load any programmes without it freezing.

I'm not sure what the cause of the problem was.

I was trying to copy a programme called celtx into my usr/lib folder and to make it easier on myself I opened nautilus under sudo and opened the permissions to the folder to anyone on the computer. However that prevented me from using sudo again so to fix that, I found a webpage that told me I could sort it out by using "pkexec chmod go-w /usr/lib/sudo/sudoers.so" in terminal. I did that, and managed to fix sudo. Soon after that, my computer was being really slow, and it ran out of battery because I didn't have my charger on me. After fully recharging it, my Ubuntu has been incredibly slow.

Can anyone help me?

---

### Post by snowpine on 2012-09-17
> **thedudething said:**
> I was trying to copy a programme called celtx into my usr/lib folder and to make it easier on myself I opened nautilus under sudo and opened the permissions to the folder to anyone on the computer. 

On the basis of this I recommend backing up your data and reinstalling.

Never ever change the permission on system folders (anything outside your /home) and if you must run Nautilus as root (very dangerous!!) use 'gsku nautilus' not 'sudo nautilus'.

Good luck! :)

---

