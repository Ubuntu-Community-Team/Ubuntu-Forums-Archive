---
title: "Fixing recursive faults but reboot is needed"
date: 2011-11-09
forum: General Help
---

### Post by quiquednst on 2011-11-09
I'm working as a volunteer for a non-profit NGO which recycle, and refurbish, computers.
 Last year we got some hundreds old PC (Compaq Deskpro EN, Pentium III, 320MB) which work quite well with xubuntu 10.04. Therefore we distributed some dozens of computers based on this SO.
 Last month I tried to install xubuntu 11.04 and I'm getting into troubles.
 After the grub page and before the login page you will see white spots instead of text but later on you get the right login screen and things seem to work. Putting 'GRUB_TERMINAL=console' on /etc/default/grub I avoided the spots point but not the real problem
 But if you try to logout, to close a session, once each two tries, you will get a crash (Fixing recursive faults but reboot is needed).
 Hereafter you will see a trace from kern.log.
 Looking at the forums it seems (I'm not sure) it could been related with the graphic card (i810e 82815 CGC) and the current Kernel (2.3.6.38. ).
 Is there any plan to correct this problem or should I go back to the xu 10.04?
 Can anyone suggest anything? 

Thanks in advance
Quique

---

### Post by mike555 on 2011-11-09
Why 11.04 ? the latest is 11.10 , perhaps the newer version might work better .

---

### Post by quiquednst on 2011-11-10
Often we send computers to places without any support. Therefore we try to be conservative, prudent.
 So it seems better to use LTS and not too recent releases. 

 Otherwise, if the problem is related with new kernels may be the solution will be a downgrade and not an upgrade.
 In any case if you suggest 11.10 I would try it.
Quique

---

### Post by mike555 on 2011-11-10
Perhaps you should stick with 10.04 , till 12.04 then. but 11.10 Xubuntu works great for me (with a few tweaks.

---

