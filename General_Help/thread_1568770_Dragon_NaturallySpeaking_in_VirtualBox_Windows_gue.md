---
title: "Dragon NaturallySpeaking in VirtualBox Windows guest"
date: 2010-09-05
forum: General Help
---

### Post by zzantozz on 2010-09-05
I'm trying to run Dragon NaturallySpeaking 10 on a Windows guest under VirtualBox on Ubuntu 10.04. The installation goes fine, but upon launching Dragon, it just shows the splash screen and sits there forever at 100% CPU usage. Any help?

Note: I know this problem is only loosely related to Ubuntu, but in searching for a resolution, I've found that many Dragon users have switched or tried to switch to Ubuntu, and this is generally a very large and helpful community, so I'm hoping to find someone with experience here.

Details:
Host: Ubuntu 10.04 desktop amd64, fully up to date
VirtualBox 3.1.8 r61349
Guest: Windows XP Home 32-bit, fully updated
Guest: Windows 7 Enterprise 64-bit, fully updated
(tried both Windows guests with same result)

---

### Post by zzantozz on 2010-09-18
Problem solved. I believe it was caused by a hard disk problem. At the very least, my partition tables were in a bad state. I wiped my partitions, recreated, and reinstalled everything, and it works fine.

---

### Post by mrodent on 2010-09-23
Hi Zzantozz,

Question: can you confirm you are successfully using DNS in an XP guest?

I have a good USB mike, DNS 8 pref, XP 32-bit guest on an Ubuntu 64-bit 10.10 (beta) host.

All my attempts (including Win 7 host) at using DNS in the XP guest have failed because the sound, although present is horribly scratchy in the guest - not good enough for dictation.

Do you have any tips???

---

### Post by zzantozz on 2010-09-23
Hey, mrodent. Yes I got it working in XP, but I'm at the same place that you are with sound input. I'm using a regular old 3.5mm mike, and recorded sound in the guest is very noisy and scratchy. I get around an 8 on the signal-to-noise test in Dragon, though I can record crystal-clearly in the Ubuntu host. In the past, I've read about similar problems with audio quality in Windows guests, but I was focused on overcoming my other problems, so I didn't pay much attention to those. I did read in the VirtualBox issue tracker that older versions of VBox had this same issue, and their response was that sound input was a rarely-used feature, so they weren't devoting a lot of attention to it. I'm not sure if this is still their attitude about it. When I get around to messing with it again, I plan to search the VBox forums and bugs a bit more and maybe post a message over there to see about getting this cleared up. Do you have any active threads running on this? I'd like to subscribe to them if you do.

---

