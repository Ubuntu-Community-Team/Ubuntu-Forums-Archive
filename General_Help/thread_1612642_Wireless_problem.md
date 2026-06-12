---
title: "Wireless problem"
date: 2010-11-03
forum: General Help
---

### Post by r1kkie on 2010-11-03
Hi!
I geting realy pissed of on my wireless now. Recently I upgraded to ubuntu 10.10 and my wireless didnt work. After som atempts to fix it I gave up. Just installed ubuntu 10.04 again and to my surprise my wirelss dosnt work proparly. 
My wireless cant find any networks when I start ubuntu 10.04. But if I connect my cable and after 30 second, the wireless finds network and are able to connect and works until  I shutdown my computer. 
What is the problem?! I am sitting on a Hp dv6501eo. Some kind of broadcome card in it. I have installed the driver.

Any1 have any suggestion?

---

### Post by 3Miro on 2010-11-03
Broadcom recently released a new sta driver. This may be a bug related to the new release (since the problem persists in 10.04 and 10.10). I had some trouble with the new one on other distros, however, I have not experiences what you describe. Can you go to the hardware center and check which version of the sta driver you have installed.

Broadcom driver is closed source and hence nobody from Canonical can do anything about it.

---

### Post by TBABill on 2010-11-03
r1kkie you should just need to get a hard wired connection then go to system>>>administration>>>hardware and allow the system to detect if drivers are available. Depending on which Broadcom card you have you may face a choice of a couple different ones. My BCM4312 uses the STA driver. To find out which model you have just type "LSPCI" in a terminal in lower case letters. That way when you see the choices you'll know your hardware.
 
Edit: Once you activate the driver a reboot is required to use it.

---

