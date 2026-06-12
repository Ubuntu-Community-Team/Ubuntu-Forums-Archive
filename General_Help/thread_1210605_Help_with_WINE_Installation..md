---
title: "Help with WINE Installation."
date: 2009-07-11
forum: General Help
---

### Post by Chase Young on 2009-07-11
I'm just having a small problem downloading WINE. For those of you who don't know, WINE is like a Windows emulator and allows you to run Windows binary (.exe's) in Linux. However, when I try to install it via the add/remove programs, it gives me this error:

[IMG]http://i305.photobucket.com/albums/nn210/chaseyoung19/WINEError.png[/IMG]

Any suggestions would be appreciated.

---

### Post by oldos2er on 2009-07-11
Looks like you're not in the /etc/sudoers file. [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Chase Young on 2009-07-11
If that were true, I wouldn't be able to run "sudo" at all, and I can.

---

### Post by Chase Young on 2009-07-11
Nevermind, apparently I'm not. I used to be, I'm the only account on my computer...Thanks.

---

### Post by oldos2er on 2009-07-12
You can try this: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by gobberpooper on 2009-07-12
Whenever I've installed WINE, just doing a "sudo apt-get install" or add/remove programs hasn't worked. Here's the guide I used.
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

As for your sudo problem, I think that has to be fixed through the GRUB menu.

---

