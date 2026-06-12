---
title: "HP PSC 1410 on Windows Share"
date: 2006-01-28
forum: General Help
---

### Post by matthewv on 2006-01-28
We recently got a new printer: a HP PSC 1410. However, it is connected up to and shared out from a Windows XP box. Other windows machines can print to it fine. When connected directly to my computer (Breezy) I can print to it fine. However, when using exactly the same settings, but changing the connection to the windows share, the document appears to be sent from my machine, the printer light starts flashing busy, the print head moves about a bit, and then... nothing! The printer remains "busy", according to its status light, but nothing happens. The windows computer shows a "Remote Downlevel Document" is being printed, but it never advances past 64.0KB.

Any ideas????

---

### Post by matthewv on 2006-01-29
So it sounds like I'll just have to keep trying..???
Or see if i can get the printer shared from my comp??

---

### Post by kseise on 2006-02-12
Same problem here, so I will bump this one up again.

---

### Post by roadrawts on 2006-02-18
Can you tell me how you set up your Ubuntu config to print to the HP on the windows share?

Thanks.

---

### Post by ORF1000 on 2006-07-22
Identical problem here, but with an HP OfficeJet 4200 series.  I hope someone comes up with an answer.

Incidentally, the printer connected to a Debian Sarge box (my server) shares just fine with all the Ubuntu boxes, but I can't get any of the Windows machines to connect to it.  They want new drivers, but won't install any.  So I'm stuck trying to share it off a Windows machine.

Dave

---

### Post by ORF1000 on 2006-07-22
Well, here's a workaround.  On the Windows box, uncheck bi-directional support in the Ports dialog.  But I think you'll lose functionality on features like ink cartridge levels.

---

### Post by nick944 on 2006-07-23
> **matthewv said:**
> We recently got a new printer: a HP PSC 1410. However, it is connected up to and shared out from a Windows XP box. Other windows machines can print to it fine. When connected directly to my computer (Breezy) I can print to it fine. However, when using exactly the same settings, but changing the connection to the windows share, the document appears to be sent from my machine, the printer light starts flashing busy, the print head moves about a bit, and then... nothing! The printer remains "busy", according to its status light, but nothing happens. The windows computer shows a "Remote Downlevel Document" is being printed, but it never advances past 64.0KB.

Any ideas????
same problem exept with a PSC 1610 I just connect it right to the computer when i want to print on that printer

---

### Post by useResa on 2006-08-25
Since I have exactly the same problem with the same printer (PSC 1410) and - to my knowledge - no solution has been given (yet), I'll bring this one under the forum's attention once more.

Is there any other solution than the indicated work-around?

BTW: I use Ubuntu 6.06 LTS - The *Dapper Drake*

---

### Post by samkline on 2007-02-10
BUMP

same problem :( anyone find a solution?

---

### Post by useResa on 2007-02-10
> **samkline said:**
> BUMP
same problem :( anyone find a solution?

The solution that is given in [post #6](http://www.ubuntuforums.org/showpost.php?p=1288183&postcount=6) resulted in the fact that at least I can print.

The setback is that you loose some functionalities on the Windows side, like checking the level of your ink cartridges.

Another solution I have not been able to find or get.

---

### Post by mrjerryk on 2008-07-04
bump I am having the same problem.  Anyone find a resolution yet?

---

### Post by useResa on 2008-07-04
> **mrjerryk said:**
> bump I am having the same problem. Anyone find a resolution yet?I have used the work-around that is provided in post #6:
> **ORF1000 said:**
> Well, here's a workaround. On the Windows box, uncheck bi-directional support in the Ports dialog. But I think you'll lose functionality on features like ink cartridge levels.
This works fine for me and for some reason -- don't know why -- I still get alerted on low ink cartridge levels.

---

