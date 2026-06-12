---
title: "AHCI &amp; SATA problems"
date: 2010-03-24
forum: General Help
---

### Post by John Wolf416 on 2010-03-24
Ubuntu 9.1 does not support SATA2 drives at full transfer rates (UDMA 3-133kbs only minor problem it's still fast)
Serious problem is Grub2beta4 is not compatable with AHCI (hot swapable SATA drives)this can lead to inability to boot at all. Grub2 is totally diffrent from Grub. Although I was able to obtain exelent advice from many on this forum of what needed to be done I was unabel to make corrections to all the files necessary to correct grub config problems. Some update packages were able to make out dated changes to VGA etc. which compounded the problem with false error messages. 
 
As I understand it Ubuntu 10.4 is imminate and is supposed to have nonbeta grub2.

---

### Post by pbrane on 2010-03-24
I'm not sure what you mean by "Serious problem is Grub2beta4 is not compatable with AHCI". My laptop is using AHCI version 3.0 and grub 1.97 beta4. Everything works fine. I'm running Karmic.

Lucid is due out in April. That may solve your issues. You can always try the beta.

---

### Post by John Wolf416 on 2010-03-25
To: Peabrain
Thank you for your response. What I suspect is that your AHCI-eSATA drives were ethier off or disconeccted when you booted/restarted. For some reason Grub 2 won't boot because there are other drive id's. Even though install partition for Ubuntu is unchanged it wont boot. That's also visa/versa if you have a drive on when you update grub you have to have it on and connected in order to boot. I knew 10.4 was due out this spring but April is very close and grub2 will be in its final stage. I'm sure then some people smarter than me will post scripting for correcting problems to grub2 because it's actually good.

---

### Post by pbrane on 2010-03-26
I see what you mean. My laptop BIOS set the hard drives to AHCI mode not SATA. There must be something else going on during boot for grub2 to work then. Because I only have that one drive.

I found this post:
[http://ubuntuforums.org/showthread.php?t=1307401]("http://ubuntuforums.org/showthread.php?t=1307401")

I'm looking forward to see how 10.04 will perform.

---

### Post by prodigy_ on 2010-03-26
First, Grub2 supports ACHI. Second, if you use hot-swapping and boot from different HDDs you might want to customize your Grub menu to reflect that. (Every partition has its own UUID so the most correct way is to add entries for all HDDs you boot from.)

Hope that helps.

---

