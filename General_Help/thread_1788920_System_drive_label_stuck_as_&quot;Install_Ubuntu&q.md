---
title: "System drive label stuck as &quot;Install Ubuntu&quot;"
date: 2011-06-23
forum: General Help
---

### Post by LFBarfe on 2011-06-23
Hi there. I've been running Windows XP and Ubuntu as a dual-boot on my desktop PC for some years now, and, when I bought a netbook recently, I thought I'd do the same. Having no DVD drive in the netbook, I had to create a bootable installer on a flash drive, using Unetbootin. So far, so good, but when I was creating the installer, using the desktop machine, I cocked up slightly and started to unload the installation files onto my C drive, not my flash drive. I stopped the process before it could do any damage to my XP installation, but I'm now stuck with my C drive labelled as 'Install Ubuntu'. I've renamed the drive label 'System' in Windows Explorer, but the displayed label is still 'Install Ubuntu'. Does anybody know a way, short of reinstalling XP, that I can get rid of the erroneous label? It's a minor annoyance and my XP installation still works fine, so I'm happy to leave it unless I can correct it without major surgery. Thanks in advance for any advice given.

---

### Post by dandnsmith on 2011-06-23
If you've a bootable Ubuntu, you can fix it with gparted.

---

### Post by LFBarfe on 2011-06-23
Thanks. I'll give that a go.

---

### Post by LFBarfe on 2011-06-24
No joy, unfortunately, but thanks for the suggestion.

---

### Post by LFBarfe on 2011-06-25
After much tearing out of hair, I located the answer. The boot disc creation process had put an autorun.inf on the C drive. I deleted this, rebooted, and I now have a C drive called 'System' once again, not 'Install Ubuntu'. Just thought I'd mention it in case anyone has the same trouble in future.

---

