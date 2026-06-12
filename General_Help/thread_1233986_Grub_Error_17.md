---
title: "Grub Error 17"
date: 2009-08-07
forum: General Help
---

### Post by skormaze on 2009-08-07
Hi there.

On my Ubuntu Server 8.04.3 Grub has the "Grub Error 17". This happened after I set the system with "sudo echo mem > /sys/power/state" into standby.

The server runs with a raid controller (3ware Escalade 9650SE-4LPML) and three 500GB hdds in raid 5.

After doing some research on the internet, I found out that grub hast some problems with raid 5. However the system worked just fine before I entered the standby command! I shut down and rebooted the server several times. Everytime Grub worked and booted Ubuntu properly.

Why do I get the error now?
What can I do to get the server running again, without loosing all my data?

Would it be possible to install another disk (directly to the motherboard) and use this disk for a fresh ubuntu installation + beeing able to mout the raid system so I can access the files?

please help! I am a bit frustrated..
                          [FONT=Times New Roman, serif][SIZE=3]
[/SIZE][/FONT]

---

### Post by note32 on 2009-08-07
have you tried hot swapping?

---

### Post by skormaze on 2009-08-07
> **note32 said:**
> have you tried hot swapping?
thanks for your answer! Why should I do that? Can hot swapping repair my Grub?

---

