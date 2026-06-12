---
title: "Can't boot into Windows 7"
date: 2011-11-26
forum: General Help
---

### Post by srb7215 on 2011-11-26
Alright so I decided I wanted to try Ubuntu and made the jump.  Installed just fine and loads just fine.  Restarted my computer to do some stuff in Windows 7 and I get to the screen where I can choose where to go.  I select Windows 7 and screen turns black and the first window loading animation starts up.  Then it restarts the computer and goes back to the screen where you can select where to start.

Any thoughts.  Very new at this.  I have little knowledge about linux.  I do mess around with a rooted Android device if that means anything here.

Tried to search but didn't come up with anything that I felt matched this same problem so sorry if this is a repeat post.

Appreciate all the help.

---

### Post by bluexrider on 2011-11-26
Dual boot Hummmmmm

about a million questions for the same answer.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

This should help you out.

---

### Post by drs305 on 2011-11-26
srb7215,

Welcome to the Ubuntu forums.

Selecting Windows from a Grub menu and having the system reboot back the Grub menu (Ubuntu bootloader) is often an indication you have installed Grub to the Windows partition.

There is an explanation and solution here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

If you don't think that applies or need help, the best thing to do is probably to click on the Boot Info Script link on that page and download/run the script. Post the contents of RESULTS.txt so we can see the status of your boot files.

---

### Post by Bucky Ball on 2011-11-26
Synaptic Package Manager. Install and run 'Boot-repair'. That will put the grub back where it's supposed to be and add your Windows 7 partition to the list. Reboot and you should be good to go. ;)

---

### Post by srb7215 on 2011-11-26
> **bluexrider said:**
> Dual boot Hummmmmm

about a million questions for the same answer.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

This should help you out.

This was a lot of help.  Rebooted with my windows 7 CD and had it repair the start up and now problems so far.  Thanks for the quick replies everyone.  I will spend some more time searching through the forums to learn more about all this.

---

### Post by drs305 on 2011-11-26
Glad things are working.

If you ever have boot problems, especially concerning Linux, the Boot Repair app can fix a lot of issues without the user having to learn a lot about the Grub bootloader. 

If you need or want to tweak the order, titles, etc of the Grub menu entries, Grub Customizer is an excellent tool.

Both have links in my signature line.

If you don't have any other questions about the current thread, you can mark it SOLVED via the 'Thread Tools' link at the top right of the first post.

Happy Ubuntu-ing

---

### Post by bluexrider on 2011-11-26
Glad to help out.

---

### Post by bluexrider on 2011-11-27
done

---

### Post by Bucky Ball on 2011-11-28
> **drs305 said:**
> Glad things are working.

If you ever have boot problems, especially concerning Linux, the Boot Repair app can fix a lot of issues without the user having to learn a lot about the Grub bootloader. 

If you need or want to tweak the order, titles, etc of the Grub menu entries, Grub Customizer is an excellent tool.



+1. Here here. And a pleasure; to help is why we frequent the forums ... and be helped, of course. Don't forget to ask for it if you have issues! ;)

Have fun ...

---

