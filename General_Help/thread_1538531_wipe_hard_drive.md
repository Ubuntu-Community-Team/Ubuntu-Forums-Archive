---
title: "wipe hard drive"
date: 2010-07-25
forum: General Help
---

### Post by archeryrob on 2010-07-25
I am trying to get a dual boot with XP and Ubuntu. I can't get the bios to boot from CD and stays at hard drive boot priority. So XP will not run and I can't load DBAN.

Can i run Ubuntu CD and stop in the middle to crash it? Options?

---

### Post by sikander3786 on 2010-07-25
Hi.

Is your PC capable of booting Ubuntu CD? If so then it shouldn't have any problem booting up Windows CD as well.

What happens if you insert the Windows CD?

Regards.

---

### Post by sidzen on 2010-07-25
Why DBAN?
If you really want to, this will do the same thing, just boot to any live cd and either go to a terminal or to console (Ctrl-Alt-F2) and enter the command

dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync

---

### Post by archeryrob on 2010-07-25
No, it's not booting from CD now. I cant figure out why in the AMD bios.

I can't get the ctrl alt f2 thing to work.

I just want to erase and start over. I could if I could get the CD to launch and Bios is not working for me and Ubuntu will not let me run a exe file.

---

### Post by sikander3786 on 2010-07-25
You have to refer to the manufacturers bios and see the options for booting off a cd.

I think the easies practice is to find out 1, The cd rom is detected in the bios, 2, It is the first boot device, 3, Turn off all other boot devices including the HDD and see what happens.

Ubuntu eventually has nothing to do to a PC's Bios.

---

