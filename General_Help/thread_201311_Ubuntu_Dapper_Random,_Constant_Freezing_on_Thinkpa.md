---
title: "Ubuntu Dapper Random, Constant Freezing on Thinkpad X24"
date: 2006-06-21
forum: General Help
---

### Post by behn1220 on 2006-06-21
I'm having a major problem with Dapper on 2 IBM ThinkPad X24 laptops.  Both laptops freeze within 15 - 30 mins of booting Dapper.  Sometimes even sooner.  I notice it most in Firefox because they are primarliy used for web browsing but I have also had this happen in OpenOffice apps and while in the Gnome Terminal.  I had been successfully running Hoary, Breezy, and even some early flights of Dapper on these laptops without incident...I even had Breezy go 89 days without a reboot on one of them.  Since the later flights of Dapper and the official release I have been plaugued with these constant freezes.  These laptops are unusable at the moment because of this and I would REALLY like to use Ubuntu on them but if I can't get this figured out I am going to have to switch to a different distro.  Here is what I have tried so far with no success...

1.) Fully updated Dapper
2.) Added "noacpi acpi=off" to Grub's menu.lst per a suggestion for a similar ThinkPad freezing problem posted elsewhere
3.) Reinstalled Dapper from scratch
4.) Updated the BIOS to the latest from IBM

Any thoughts?  Anyone else seeing this?

Behn

---

### Post by Paerez on 2006-06-21
I think I may be getting the same thing, except mine is predictable. Specifically, there is a text file on my desktop and whenever I open it with gedit or eclipse my comp freezes. Complete hard-lock. I am clueless.

---

### Post by behn1220 on 2006-06-24
Well, I think I have narrowed it down to my PCMCIA Cisco Aironet A/B/G wireless adapter.  Whenever I activate it through Network Manager the laptop starts randomly crashing/freezing.  If I'm using wired ethernet and my Cisco card is de-activated the laptop never freezes.  I've tried avoiding Network Manager by following this thread's advice ... [http://ubuntuforums.org/showthread.php?t=191085&highlight=wireless+freezing+dapper](http://ubuntuforums.org/showthread.php?t=191085&highlight=wireless+freezing+dapper) ...but I can't get wireless to automatically start at boot time using this method.  I'm still digging into it and hope to have this resolved soon...

---

### Post by jivetolkein on 2007-02-23
I'm afraid I get this on an X24 too - ubuntu, xubuntu :-( - pretty sure Windows doesn't but it's been a while since it was on there. On Edgy now, but it's happened on earlier incarnations, and I'm sure it didn't on SuSE.

MEMcheck runs quite happily ( I suspected an extra SoDimm I'd added) and I've had it apart to re thermal grease the processor. Still no luck.

Tried various kernal switches on boot with no effect.

I'm using the Intel 802.11a card, so I don't think it's related to your MiniPCI card (plz prove me wrong!) - works well with Kismet and the like so I'd prefer not use another machine and NDIS wrapper.

Anymore ideas out there? It's not critical if this gets trashed for the furtherment of the community :-)

---

