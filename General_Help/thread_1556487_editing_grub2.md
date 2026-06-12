---
title: "editing grub2"
date: 2010-08-19
forum: General Help
---

### Post by irisblaze on 2010-08-19
hello, i had to leave the country for about a month, since only my mom lives with me and the only thing she can do is push the power button and wait for oovoo to automatically log her in so she can call me, i set the default os to windows and timeout to 0, now i am back and want my ubuntu back, so i boot from live cd and mount the ubuntu partition, and i was surprised that i can only open grub.cnf as read only.. i just want to edit grub.cnf .. how can i do that?

---

### Post by sydbat on 2010-08-19
> **irisblaze said:**
> hello, i had to leave the country for about a month, since only my mom lives with me and the only thing she can do is push the power button and wait for oovoo to automatically log her in so she can call me, i set the default os to windows and timeout to 0, now i am back and want my ubuntu back, so i boot from live cd and mount the ubuntu partition, and i was surprised that i can only open grub.cnf as read only.. i just want to edit grub.cnf .. how can i do that?Press 'Esc' just after the computer posts and it should bring up the grub menu. From there you can go into Ubuntu to edit grub or choose to edit grub from the grub menu by pressing 'e'.

---

### Post by irisblaze on 2010-08-19
> **sydbat said:**
> Press 'Esc' just after the computer posts and it should bring up the grub menu. From there you can go into Ubuntu to edit grub or choose to edit grub from the grub menu by pressing 'e'.

tried that, grub loads windows before i can press anything, timeout is 0 (how stupid of me)

---

### Post by c2tarun on 2010-08-19
hello
i am trying to run a wired internet connection on linux
i run "ifconfig eth1" and got the message device not found.
then i read on a forum about installing my lan driver.
i downloaded the driver but unable to install it.
on that forum it is also mentioned to install kernel-source and gcc.
i have absolutely no idea what does it mean.
i am using ubuntu 10.4
can anyone please help me

---

### Post by sydbat on 2010-08-19
> **irisblaze said:**
> tried that, grub loads windows before i can press anything, timeout is 0 (how stupid of me)Maybe reboot and start hitting 'Esc' right away? Might be fast enough to open grub.

Let us know if that works. If not, I think you can open a terminal in the LiveCD and you have to change the permissions on the grub file before editing it. Try 'sudo' or 'gksudo' when opening the grub file/folder.

---

### Post by irisblaze on 2010-08-19
> **sydbat said:**
> Maybe reboot and start hitting 'Esc' right away? Might be fast enough to open grub.

Let us know if that works. If not, I think you can open a terminal in the LiveCD and you have to change the permissions on the grub file before editing it. Try 'sudo' or 'gksudo' when opening the grub file/folder.

i also tried both solutions you suggested, grub executes too fast, as for opening the file as root i think i mentioned i tried that before using sudo, it opens it as read only

---

### Post by drfox on 2010-08-19
You have to hit the shift key while booting, right after CMOS loads to get into Grub2
HTH
Larry

---

### Post by sydbat on 2010-08-19
> **irisblaze said:**
> i also tried both solutions you suggested, grub executes too fast, as for opening the file as root i think i mentioned i tried that before using sudo, it opens it as read onlyWell...poo...

I know there is a way to reinstall grub via the LiveCD.

Here it is. Try this - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Mark Phelps on 2010-08-19
I believe that with GRUB2, since in the situation where there is only one OS installed on the machine, it automatically boots into that OS without showing a menu, you hold down the Shift key when booting to force it to show a menu.

Also, make sure you do NOT edit the grub.cfg file; instead, you can install startup-manager if you want a GUI for editing defaults easily.

---

### Post by c2tarun on 2010-08-19
sorry sydbat
i started my own thread see there if you can help me
thanx

---

### Post by irisblaze on 2010-08-19
> **Mark Phelps said:**
> I believe that with GRUB2, since in the situation where there is only one OS installed on the machine, it automatically boots into that OS without showing a menu, you hold down the Shift key when booting to force it to show a menu.

Also, make sure you do NOT edit the grub.cfg file; instead, you can install startup-manager if you want a GUI for editing defaults easily.

of course i have 2 os :P ubuntu + win7 as i said the grub2 installation is perfect i just want to edit it so it can show ubuntu, i'll try drfox's method then sydbat's

thanx

---

### Post by sydbat on 2010-08-19
> **irisblaze said:**
> of course i have 2 os :P ubuntu + win7 as i said the grub2 installation is perfect i just want to edit it so it can show ubuntu, i'll try drfox's method then sydbat's

thanxAnd don't forget Mark Phelps suggestions too.

---

### Post by irisblaze on 2010-08-19
so now i get the grub command line not menu :( ? help? i told you i don't want to reinstall grub *sigh* why is it hard to edit a file from live cd? :P

---

