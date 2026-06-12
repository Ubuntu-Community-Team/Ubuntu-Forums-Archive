---
title: "accidentally deleted fsck-at-reboot file"
date: 2012-05-15
forum: General Help
---

### Post by Butthead on 2012-05-15
Hi,

While farting around yesterday trying to get the upgrade notifier icon to display in my system tray, I carelessly deleted the "fsck-at-reboot" file that was in the /var/lib/upgrade-notifier folder.  I was just wondering if anyone else on the forum here can send me their fsck-at-reboot file (I don't think it's really that big of a file, if it even contains any text?), or post what was containd in theirs so I can create a new one.  I searched online for information about it, but came up not finding much about it.  I'm running a 64 bit Kubuntu 12.04 (Precise Pangolin) if that makes any difference?  Thanks for any help anyone can give me with this, I'd be most greatful! ):P

---

### Post by drmrgd on 2012-05-15
I just had a look at that file on my system, and it's empty.  I think it might just be something that acts as a flag when the system needs to run a fsck at the next reboot (or you want to ask the system to do it for you).  I'm guessing for now, you could just make an empty file if you really need it.

---

### Post by Butthead on 2012-05-15
Hi drmgd,

Okay, thanks very much!  I really do appreciate your help with this! :guitar:

---

### Post by Butthead on 2012-05-15
BTW - (if it helps anyone else?), here's the only revelant information I could find online (after hours spent searching :mrgreen: ) on how to regenerate a new fsck-on-reboot file:

(The patch he's referring to here never seemed to work for me when I tried to apply it. ](*,) )

After applying the above patch; either reboot, or regenerate /var/lib/update-notifier/fsck-at-boot as follows:

$ sudo -s
# run-parts --lsbsysinit /etc/update-motd.d > /var/run/motd

I imagine since the file itself appears to be empty (0 bytes), just creating a blank text file in your ASCII editor would probably work just fine too. :guitar:

---

