---
title: "Multiple issues after installing from Mini ISO."
date: 2012-06-16
forum: General Help
---

### Post by Roger-H on 2012-06-16
I have a Dell Inspiron B130 that I just installed Lubuntu 12.04 on. I was unable to use the standard USB CD installation procedure, unfortunately the machine would lock up after I selected the installation option.

So I downloaded the Mini ISO, burned it on a CD, and installed it that way. I used the instructions here:

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

It worked well, the dual boot option works properly, etc., and I was able to resolve the issue with the missing Network Manager applet (see the "Unmanaged Wired Network" section on that page).

However, there are some lingering issues...

Issue #1: Apparently the system did not automatically detect the firmware for the wireless adapter so it says "Device not ready" when I click on the Network Manager applet on the taskbar. If someone can point me to the right wiki page to get this accomplished, I would appreciate it because my Google searches don't seem to be turning up the right results.

Issue #2: I want the system to boot straight to the user's account, no login screen. I edited /etc/lxdm/default.conf and changed the autologin parameter to the username. However, I still get the login screen.

Issue #3: After selecting an account, a dialog displays saying, "System program problem detected" and there are only two options to Cancel or Report problem. If I choose to report the problem, it prompts me for a password. When I enter the user's password (the only password I've ever defined on this machine), it doesn't accept it, says it's incorrect. At this point I can only cancel and there is no indicator as to what the system error actually was.

Any help would be greatly appreciated. Thanks!

---

### Post by marinara on 2012-06-16
google your laptop name and "ubuntu" to fix the NIC
Lubuntu does not use lxdm in 12.04

---

### Post by Roger-H on 2012-06-16
> **marinara said:**
> google your laptop name and "ubuntu" to fix the NICFound some better stuff, thanks. Will try these out.> Lubuntu does not use lxdm in 12.04That's interesting. I have another laptop with Lubuntu 12.04 and /etc/lxdm/default.conf has autologin defined and it works fine. If it isn't here, where do I define this parameter?

---

### Post by marinara on 2012-06-16
[http://ubuntuforums.org/showthread.php?t=1927563](http://ubuntuforums.org/showthread.php?t=1927563)

---

### Post by Roger-H on 2012-06-16
Okay, so far, so good. Issues #1 and #2 are solved, thank you very much. Issue #3 is still frustrating me. I even changed the password to see if it would accept a new one. No idea. I'm looking through /var/log for any clues but I'm not sure what to look for.

---

### Post by Roger-H on 2012-06-16
Ah-ha. Found this thread:

[http://ubuntuforums.org/showthread.php?t=1981696](http://ubuntuforums.org/showthread.php?t=1981696)

Did a "sudo rm /var/crash/*" and that fixed Issue #3. Thanks, everyone.

---

