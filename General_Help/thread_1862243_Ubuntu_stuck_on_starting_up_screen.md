---
title: "Ubuntu stuck on starting up screen?"
date: 2011-10-16
forum: General Help
---

### Post by mozozo4 on 2011-10-16
I have an hp dv6000 laptop and it was running ubuntu 11.04. 
I decided to update to 11.10. In the middle of the process of upgrading, the power plug got disconnected from my laptop and the laptop just shut down in the middle of the process. 

So now it is stuck on the boot up screen which says starting up...
is the computer broken for good?

Is there any way to fix this issue?

please someone help me

---

### Post by mozozo4 on 2011-10-16
can someone please help me
it was a very good working computer and i want to know how to fix it.
I've been looking at the forum every 30 minutes but nobody gives an answer.

---

### Post by collisionystm on 2011-10-16
> **mozozo4 said:**
> can someone please help me
it was a very good working computer and i want to know how to fix it.
I've been looking at the forum every 30 minutes but nobody gives an answer.

reboot your computer

immediately after the bios screen, hold the shift key down

you will be at the grub menu

go to system rescue

at the rescue menu, choose resume normal boot

you will be at a text login

put in your user name then your password

type

sudo dpkg --configure -a

---

### Post by mozozo4 on 2011-10-16
thank u for actually answering
but i dont understand wat u mean by the bios screen
but now that i reboot it loads up and then days ubuntu is running in low-graphics mode
it gives me an option to press ok, but the mouse is inactive and i have pressed all the keys. its just stuck on this screen now

anything i can do?

---

