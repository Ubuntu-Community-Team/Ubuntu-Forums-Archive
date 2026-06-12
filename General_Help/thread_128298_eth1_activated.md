---
title: "eth1 activated"
date: 2006-02-11
forum: General Help
---

### Post by reskerix on 2006-02-11
Hi
I'm using a VAIO laptop FS295-VP and I configured the network and wifi with no problem except that:

when the system boots, eth0 and eth1 are activated.
I want that the network traffic goes through eth0 (wifi) but it goes through eth1 because it's activated (as default??). 
I've to run 'ifconfig down eth1' every time I boot the ubuntu because I haven't the network cable plugged in.

 I want that be automatic.
Any suggestions? thanks.

---

### Post by alamba on 2006-02-11
System>Admin>Networking
Click on eth1 and then click on deactivate.

Thank should fix it.

A

---

### Post by reskerix on 2006-02-11
I tryed it and works while the machine is not turned off.
But when I reboot I've the same problem.

I think that it's a hotplug problem or and error in the interfaces field..
:confused: 

suggestions? :rolleyes:

---

### Post by alamba on 2006-02-11
Does your laptop have a hard switch to switch on WiFi?

---

### Post by reskerix on 2006-02-11
yes. why?
this switch is on everytime...

---

### Post by reskerix on 2006-02-11
no more ideas?

---

### Post by SWAT on 2006-02-11
It's a weekend guys, have some more patience. Well, if you are really keen on disabling eth1, I would suggest just editing your /etc/network/interfaces file to fit your needs. 
By the way, do you only use your eth0 or do you switch between eth0 and eth1?

---

### Post by alamba on 2006-02-12
In my laptop I need to have the switch on before the system boots up for it to boot into eth1 without enabling eth0. (On means the wireless light should light up).

Akshay

---

### Post by reskerix on 2006-02-12
thank you alamba and swat but I've tryed all you suggest.

I always have the switch on when the laptop boots and when it is ready I've both interfaces up (the eth0 -wifi- and eth1 (where there isn't any cable)).

and I tryed to edit the interfaces file but i just want can switch to eth1 when I plug in a cable and I don't know how to configure this in the interfaces file...

:KS do you know how configure this?

---

