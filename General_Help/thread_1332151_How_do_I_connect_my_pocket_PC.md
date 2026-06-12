---
title: "How do I connect my pocket PC?"
date: 2009-11-20
forum: General Help
---

### Post by mirchichamu on 2009-11-20
I want to know how can I connect my PPC with ubuntu. I saw palm device on my system but nothing happens when I connect my PPC to system.
Your help will be highly appreciated.

---

### Post by earthpigg on 2009-11-20
can you provide more detail?

what version of ubuntu, what pocket pc?

---

### Post by mirchichamu on 2009-11-20
> **earthpigg said:**
> can you provide more detail?

what version of ubuntu, what pocket pc?

Thanks earthpigg for your reply.
I am using latest version of Ubuntu which I downloaded 2 days back and installed through wubi. I am having Htc opal, which is also called htc touch viva, with windows mobile 6.1.

---

### Post by P4man on 2009-11-20
This may or may not work:
[http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice](http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice)

Keep in mind the synchronization protocol is not disclosed by MS, and synce was built by trying to reverse engineer it, so there are no guarantees it will work, but its worth a shot.

edit: your ubuntu version, assuming its 9.10 is "karmic"
So replace interpid or jaunty in those instructions with karmic

---

### Post by mirchichamu on 2009-11-20
> **P4man said:**
> This may or may not work:
[http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice](http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice)

Keep in mind the synchronization protocol is not disclosed by MS, and synce was built by trying to reverse engineer it, so there are no guarantees it will work, but its worth a shot.

edit: your ubuntu version, assuming its 9.10 is "karmic"
So replace interpid or jaunty in those instructions with karmic

Thanks a lot p4man for your great support.
I did everything what is asked on the page. Ultimately I got my pDA connected but there is some problem still remaining. When I right click the syce tray icon>>explore device>>>I get a reply>>Nautilus cannot handle synce location.
When I press on DCCM, I get reply that vdccm cannot start which is necessary to communicate with device. Otherwise I can see my device programs. I just want if I could explore my device, no other syncing I need.

---

### Post by P4man on 2009-11-20
In that case, try installing wm5torage on your mobile. It makes it behave like a USB storage device and so should be transparent to ubuntu who will see it as a thumb drive.

---

### Post by mirchichamu on 2009-11-20
> **P4man said:**
> In that case, try installing wm5torage on your mobile. It makes it behave like a USB storage device and so should be transparent to ubuntu who will see it as a thumb drive.

Thanks once again for being with me.
I installed win5torage but few folders are opened on my SD card only. The others are not opened at all. I don't know why.
If I could access through Nautilus that would have been better.

---

