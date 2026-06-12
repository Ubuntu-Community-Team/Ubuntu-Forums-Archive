---
title: "No operating system found"
date: 2010-09-02
forum: General Help
---

### Post by robhol111 on 2010-09-02
I got a new laptop today and the first thing I did was to install Ubuntu as a dual boot with Windows 7. Everything seemed to work the first time I loaded Ubuntu after installation, and Windows also seemed to work. Then, Windows Maintenance said there was possible disk corruption, so I restarted the computer and now I get this error when trying to load. After reading around about similar problems I think it might be a problem with the grub bootloader, but I have no idea how to fix it. Can anyone help? It is 64-bit if that makes a difference.

---

### Post by splater on 2010-09-02
well I think you will have your answer there:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

hope this help
Splater

---

### Post by robhol111 on 2010-09-02
Thank you, after following that guide I have now managed to get Windows to load and the problem appears to be solved.

---

### Post by robhol111 on 2010-09-02
Spoke too soon; that worked the first time but now I have the same problem. I think Windows is removing the bootloader automatically for some reason.    EDIT: Also, I can no longer boot from the Ubuntu Live CD; I just get the same error as when I try to boot normally. EDIT2: The reason I was unable to boot from the Live CD is that, after checking it in another computer, it appears to have spontaneously transmogrified into a blank CD. I will burn another Live CD and try again. The main problem still remains, though.

---

### Post by SycloneMedia on 2010-09-02
Does your laptop happen to be a Dell? If so, the problem starts with the Local Backup software that Dell preinstalls on their systems. After you bring grub back (there's many documented threads regarding the issue here), uninstall that local backup software, or just don't launch it, or ever update it. If you decide to uninstall it, you will have to reinstall grub one more time because anytime changes are made to that crap backup software, it destroys grub since that software operates off its own partition on the dell computer.

---

### Post by robhol111 on 2010-09-02
It is indeed a Dell; thank you, I shall try this removing the backup software and see what happens.

---

