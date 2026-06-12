---
title: "Question on dual booting,.."
date: 2011-03-20
forum: General Help
---

### Post by Zerocool Djx on 2011-03-20
I wanna do a dual boot with windows 7 on main HD and Ubuntu on  Secondary. I know this is done with grub,.. but where do I set the  parameters? Where is thew config file again?

---

### Post by Zerocool Djx on 2011-03-20
Bump,.. please help....

---

### Post by Mark Phelps on 2011-03-20
> **Zerocool Djx said:**
> I wanna do a dual boot with windows 7 on main HD and Ubuntu on  Secondary. 
If you have two physical drives, the best way to do this is as follows:
1) Disconnect the Win7 drive
2) Install Ubuntu to the other drive
3) Reconnect the Win7 drive -- but continue to boot from the ubuntu drive
4) Boot into Ubuntu, open a terminal, enter "sudo update-grub".  This will regenerate the GRUB menu with an entry for Win7.

>  I know this is done with grub,.. but where do I set the  parameters? Where is thew config file again?

There is no menu.lst file for GRUB2 and you should NOT mess with the grub.cfg file.  You're better doing startup customizing by installing startup-manager and using that.

---

### Post by Zerocool Djx on 2011-03-20
yea that's a way to do it, thanks!

But really, I don't mind messing with the grub file cause I got back up things if it gets jammed and I already moved the menu order once before. I kinda wanted to do the same thing with this one make win 7 the default on the C: drive and have the seccond option be ubuntu on the secondary drive.

---

