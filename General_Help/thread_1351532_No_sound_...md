---
title: "No sound .."
date: 2009-12-10
forum: General Help
---

### Post by user1001 on 2009-12-10
Hi

I just installed Ubuntu 10.9 and updated everything.. 
but i do not have any sound at all.
I have looked everywhere on google and this forum to find a solution but still couldn't get it to work.

Btw. my sound was working with Ubuntu 7.10 when I installed it long time ago.. where I formatted it and installed xp and used it for a long time till now.


edit::: I have creative soundblaster audigy 2

Thanks

---

### Post by user1001 on 2009-12-10
I've actually got Creative Sound Blaster Audigy 2 ZS 
but my alsa pastebin says I have
```
# Soundcards recognised by ALSA
# -----------------------------
#  
# 0 [Audigy         ]: Audigy - Audigy 1 [Unknown]
#                      Audigy 1 [Unknown] (rev.5, serial:0x20051102) at 0xe480, irq 16
#  
#  
# PCI Soundcards installed in the system
# --------------------------------------
#  
# 03:03.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
# 03:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 05)
```

---

### Post by user1001 on 2009-12-11
> **user1001 said:**
> I've actually got Creative Sound Blaster Audigy 2 ZS 
but my alsa pastebin says I have
```
# Soundcards recognised by ALSA
# -----------------------------
#  
# 0 [Audigy         ]: Audigy - Audigy 1 [Unknown]
#                      Audigy 1 [Unknown] (rev.5, serial:0x20051102) at 0xe480, irq 16
#  
#  
# PCI Soundcards installed in the system
# --------------------------------------
#  
# 03:03.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
# 03:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 05)
```

Bump.. No help? =(

---

### Post by NoaHall on 2009-12-11
Try clicking on the sound icon, and make sure it isn't muted.

Do the same by typing ```
alsamixer
``` into the terminal.

---

### Post by user1001 on 2009-12-11
> **NoaHall said:**
> Try clicking on the sound icon, and make sure it isn't muted.

Do the same by typing ```
alsamixer
``` into the terminal.

Thanks for your reply =)

No... it's not muted, however I've discevered two soundcards or systems in my pc one which is the one on the motherboard and one is the creative audigy 2 zs


when I plug into the one on the motherboard it works fine, but I want it to work with the creative sound card.. I think it's better quality.

and i think audigy 1 is the one on the motherboard.. maybe since that's what it says on the paste-bin info from alsa.

thanks again..

---

### Post by joes7 on 2009-12-11
Driver configuration is your friend.
Applications->System->Hardware / Drivers

---

### Post by iamgeniusrnti on 2009-12-11
> **joes7 said:**
> Driver configuration is your friend.
Applications->System->Hardware / Drivers

That never works... I cant believe you posted that.  All that ever says is no proprietary hardware... LOL!  j/k about your post though:)

---

### Post by joes7 on 2009-12-11
You can always look for your speakers' drive online.

---

### Post by joes7 on 2009-12-11
Fixed! I remember now. I had the same problem a couple of months ago (when I installed Ubuntu. Now I am running Xubuntu). If you are multi booting with Windows, uninstall the driver from Windows. Look for the driver online and make sure that it is for Linux. Finding drivers is not that hard , depending on your speaker brand.

---

