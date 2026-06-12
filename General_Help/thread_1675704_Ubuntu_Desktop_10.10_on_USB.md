---
title: "Ubuntu Desktop 10.10 on USB"
date: 2011-01-26
forum: General Help
---

### Post by Jaiv on 2011-01-26
Hey everyone. After my 10.10 Live CD arriving in the mail, I thought it was finally time to leave Windows. I am very experienced in Windows. I really haven't had a chance to check out all Ubuntu has  to offer, however I am extremely satisfied with this OS already. It is sleek, fast, functional, and loaded. My main HDD is fully partitioned to Windows and I did not want to change that, at the time the only USB storage I had was a 32GB USB Flash Drive. So wanting a portable OS I loaded Ubuntu onto that, I left 15.5GB for files and 16.5GB for Ubuntu. My problem is that I have others who use the PC I installed Ubuntu from. When my Flash Drive is inserted it boots into the menu which lets me select Windows or Ubuntu. However when the flash drive is unplugged (most times, since it is always with me), It will not load Windows. The people who use the computer need to boot Windows as they are not good with computers.

Too long, didn't read? How do I boot Windows without having my Ubuntu Drive plugged in?

---

### Post by Rody on 2011-01-26
this may help
sudo dpkg-reconfigure grub-pc

the program that pops up will ask you where you want to install grub make sure to add it to the drive that windows is on. Also you may have to go into your bios and tell it what drive to boot off if this does not work. 

there are also guides out there on how to fix your windows boot sector but they are defferent depending on what version of windows you are running and weather or not you have the windows install disk.

---

### Post by Jaiv on 2011-01-26
That is a terminal command, correct? It gives me a command not found error. FYI I do not know much about Terminal.

---

### Post by Rody on 2011-01-26
sorry about that I added an extra k in the command

sudo dpkg-reconfigure grub-pc

---

### Post by Jaiv on 2011-01-26
Okay, after everything I ended up putting Ubuntu on my main drive. Thanks for all your help.

---

