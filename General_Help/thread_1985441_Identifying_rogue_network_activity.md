---
title: "Identifying rogue network activity"
date: 2012-05-23
forum: General Help
---

### Post by GuiGuy on 2012-05-23
I have just rebuilt my mythbuntu box. On my network is a 4G NAS device used for backup storage. 

Almost as soon as the rebuilt mythbuntu box was up and running it started a non stop discourse between itself and the NSA device. There is no conceivable reason I can think of why it should be doiing this.

Can anyone here give me some tips on identifying & isolating programs that might be doing this?

TIA

---

### Post by ~!geek!~ on 2012-05-23
> **GuiGuy said:**
> I have just rebuilt my mythbuntu box. On my network is a 4G NAS device used for backup storage. 

Almost as soon as the rebuilt mythbuntu box was up and running it started a non stop discourse between itself and the NSA device. There is no conceivable reason I can think of why it should be doiing this.

Can anyone here give me some tips on identifying & isolating programs that might be doing this?

TIA

Check out Nethogs tool.

after installing the nethogs, execute 

> sudo nethogs <interfacename>
 
The interface name will be something like eth0, ppp0, eth1 and stuff which you can find out by looking at the output of ifconfig command.

---

### Post by GuiGuy on 2012-05-23
> **~!geek!~ said:**
> Check out Nethogs tool.

after installing the nethogs, execute 

 


Cool. Thanks for the tip. The problem was actually a media server running on the NAS box. 

Cheers

---

