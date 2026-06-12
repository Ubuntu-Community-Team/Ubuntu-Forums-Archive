---
title: "ubuntu conencts to internet but not XP"
date: 2009-08-19
forum: General Help
---

### Post by masoud23 on 2009-08-19
Hello

I have ubuntu 9.04 and XP on diferent partitions on my harddrive. When i start my pc by ubuntu there is no problem conecting to internet but when i start with XP I can't conenct to internet what ever i do?

---

### Post by fr34k_0/\/_4_1345l-l on 2009-08-19
> **masoud23 said:**
> Hello

I have ubuntu 9.04 and XP on diferent partitions on my harddrive. When i start my pc by ubuntu there is no problem conecting to internet but when i start with XP I can't conenct to internet what ever i do?

are ya trying to connect on wifi or a cable?

---

### Post by DeMus on 2009-08-19
> **masoud23 said:**
> Hello

I have ubuntu 9.04 and XP on diferent partitions on my harddrive. When i start my pc by ubuntu there is no problem conecting to internet but when i start with XP I can't conenct to internet what ever i do?

Has XP connected to the internet before you installed Ubuntu, or did it never do that?
When it's the last, it could be a driver. I have here a pcmcia network card which is automatically detected and installed by Ubuntu, but for XP I need to get me a separate driver because XP has never heard of the card.
What make and model is your card, or are you, as "fr34k_0/\/_4_1345l-l" also mentioned, connecting through WiFi? Even then, what is the make and model of this card? Don't forget XP is 8 years old. Hardware which is newer could be a problem for this old software.

---

### Post by fr34k_0/\/_4_1345l-l on 2009-08-19
> **DeMus said:**
> Has XP connected to the internet before you installed Ubuntu, or did it never do that?
When it's the last, it could be a driver. I have here a pcmcia network card which is automatically detected and installed by Ubuntu, but for XP I need to get me a separate driver because XP has never heard of the card.
What make and model is your card, or are you, as "fr34k_0/\/_4_1345l-l" also mentioned, connecting through WiFi? Even then, what is the make and model of this card? Don't forget XP is 8 years old. Hardware which is newer could be a problem for this old software.

yea, i was gonna get to the driver when i figured out what they used to connect ;P

---

### Post by Maheriano on 2009-08-19
I installed XP on a new computer yesterday and quickly realized it won't even connect wired until you install the motherboard's LAN driver. Reminded me why I installed Ubuntu on my other 4 computers.

---

### Post by masoud23 on 2009-08-19
I had XP on this PC before and den it was no problem conecting to internet. problems apierad when I installed ubuntu sid by side with xp.

---

### Post by fr34k_0/\/_4_1345l-l on 2009-08-19
> **masoud23 said:**
> I had XP on this PC before and den it was no problem conecting to internet. problems apierad when I installed ubuntu sid by side with xp.

that sucks. wtf? that should not happen. did you try uninstalling the windows driver and reinstalling it again?

---

### Post by credobyte on 2009-08-19
Ubuntu have nothing to do with your XP drivers ( motherboard ).

---

### Post by Commander_Keen on 2009-08-19
If I was you I would double check the settings.
then I would do the following
Go to start
Run
type " command"
type " IPconfig"
there should an IP address
if the Ip addres = 192.168.X.X ; then the problem could be the gateway.
If the Ip adrress = 169.x.x.x.  = the pc is not getting an ip address  
                    from the router
Step 2
 Ping 127.0.0.1  If its not pingable then you need to re-install the IP/tcp and or the drivers.
 If its pingable then its the gateway..

The gateway should be pointing to your router. ( IP address of router)

---

### Post by mike555 on 2009-08-19
When you switch from Ubuntu to XP it probably confuses your modem , if you shut down for a couple of minutes in between it should be ok ..........

---

### Post by DeMus on 2009-08-19
> **mike555 said:**
> When you switch from Ubuntu to XP it probably confuses your modem , if you shut down for a couple of minutes in between it should be ok ..........

Right, maybe even switch off the router since it is possible that the pc gets a completely different IP number from the router.

---

