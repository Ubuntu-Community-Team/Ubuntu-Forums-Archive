---
title: "Can't hibernate when Vbox is running"
date: 2010-03-09
forum: General Help
---

### Post by nerdtron on 2010-03-09
I'm using Ubuntu 9.10 and recently installed Virtualbox PUEL edition that I downloaded from the Virtual box website. So I installed a virtual windows XP and it works fine. However, when the virtual XP is running, my computer can't go to hibernate when I click the hibernate button.
The screen just turns black for several seconds and then brings me back to the login screen. When I shut down the virtual xp, the computer can go to hibernate the normal way.
Why is it that running the virtual machine prevents my pc from hibernating?
Is there a setting to enable hibernation while the virtual machine is running?

---

### Post by dcstar on 2010-03-09
> **nerdtron said:**
> I'm using Ubuntu 9.10 and recently installed Virtualbox PUEL edition that I downloaded from the Virtual box website. So I installed a virtual windows XP and it works fine. However, when the virtual XP is running, my computer can't go to hibernate when I click the hibernate button.
The screen just turns black for several seconds and then brings me back to the login screen. When I shut down the virtual xp, the computer can go to hibernate the normal way.
Why is it that running the virtual machine prevents my pc from hibernating?
Is there a setting to enable hibernation while the virtual machine is running?

If the VM uses swap space, then there may not be enough left to hibernate.

---

### Post by nerdtron on 2010-03-09
I have 2gigs of RAM and about 4gigs of swap space. I allocated 800MB of my RAM for the virtual machine. and when I check the system monitor, the used swap is only about 1gig.

Do I need to adjust my swap space then?

---

### Post by Dayofswords on 2010-03-09
let me throw in this concept

hibernating a OS is ok, you tell it you want to it take a nap and get back to work later, fine

you tell it to hibernate  when another OS is running install I believe does not warn that OS, thus... you maybe come back to find errors on the virtual computer

instead:
take a snapshot of the virtual computer (in one of the menus on virtualbox, cant remember where) then hibernate 

safe and easy

---

### Post by nerdtron on 2010-03-09
> **Dayofswords said:**
> let me throw in this concept

hibernating a OS is ok, you tell it you want to it take a nap and get back to work later, fine

you tell it to hibernate  when another OS is running install I believe does not warn that OS, thus... you maybe come back to find errors on the virtual computer

instead:
take a snapshot of the virtual computer (in one of the menus on virtualbox, cant remember where) then hibernate 

safe and easy


Thanks for your reply.
Yes, I'm aware with that. I even consulted with my teacher using ubuntu. He said he can hibernate ubuntu while running the virtual XP. Then he said I should post in the forum to know if others are experiencing this problem and if there are some possible solutions.

---

