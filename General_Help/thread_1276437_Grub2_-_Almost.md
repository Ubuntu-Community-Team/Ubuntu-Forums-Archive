---
title: "Grub2 - Almost"
date: 2009-09-27
forum: General Help
---

### Post by Quarkrad on 2009-09-27
I get the impression Grub2 is reasonably stable and having failed before tried again yesterday.  This site gave me confidence and away I went - backing up my old 9.04 sda1 partition and following the instructions:

[https://wiki.ubuntu.com/Kernel/Team/Grub2Testing](https://wiki.ubuntu.com/Kernel/Team/Grub2Testing)

The first part went OK

[B]How to Install grub2

sudo apt-get install grub-pc

At the first prompt, select OK. Next, at the "Chainload from menu.lst" prompt answer "Yes". And at the "Linux command line:" prompt just press the Enter key.

......................

............ If you experience this problem, at the "Chainload into Grub 2" menu item, press 'e' to edit the configuration. Press 'e' a second time to edit the top boot line and change[/B]


I rebooted and my Grub screen was definately different - I now had a Chainloader into Grub2 option at the top.  Great - I thought I was there.

Unfortunately pressing Grub2 gave me  **Error 11: Unrecognized device string.  Press any key to continue**

So I continued with the wiki page and as I have 9.04 (Jaunty) I was not too worried.  I followed the instructions and changed my

 root   xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
to
uuid   xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

Rebooted and I still get **Error 11: Unrecognized device string.  Press any key to continue** whether I choose Chainloader into Grub2 or my old Grub 1.5 option lower down the Grub screen.  Interesting I can still boot into my winxp partitions via the grub screen - I just cannot boot into my sda1 Ubuntu partition.

Any help appreciated - I would love to have Grub2.

---

### Post by Quarkrad on 2009-09-29
Edit the menu.lst file in the Grub folder so that uuid replaces root

---

