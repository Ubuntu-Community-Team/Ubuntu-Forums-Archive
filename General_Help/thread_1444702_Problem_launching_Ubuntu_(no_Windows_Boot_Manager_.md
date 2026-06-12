---
title: "Problem launching Ubuntu (no Windows Boot Manager screen)"
date: 2010-04-01
forum: General Help
---

### Post by greenglaze on 2010-04-01
I am interested in open source software so I thought I'd try installing Ubuntu via the Wubi installer.  Windows XP is my current default operating system (which was pre-installed when I bought my computer).  I want to be able to run Windows XP and Ubuntu on the same computer.

I've followed these instructions (as described on the [Wubi FAQ page]("http://wubi-installer.org/faq.php")) but I get stuck at the section in bold: "*Run Wubi, insert a password for the new account, and click "install".  The installation process from this point is fully automatic. The  installation files (700MB) will be downloaded and checked, after which  you will be asked to reboot. **Do so and select Ubuntu at the boot screen.**  The installation will continue for another 10-15 minutes and the  machine will reboot again. This is it. Now you can select Ubuntu at the  boot screen and start using it*."

My problem is that when I rebooted my computer, the Windows Boot Manager screen didn't appear.  It just launched straight into Windows XP so I didn't even get a chance to select Ubuntu as the operating system to use.  I've rebooted my computer several times since the installation, but it always launches Windows XP straight away.

When I go to the Add & Remove Programs facility in the Windows Control Panel, I can see that Ubuntu has been installed as a separate program, but as the Windows Boot Manager screen doesn't appear when I switch on my computer, I have no way of launching it.

How do I fix this problem?  Is there a way of forcing the Windows Boot Manager screen to appear?  Thanks in advance for any advice.

---

### Post by Mark Phelps on 2010-04-02
Suggest you read through the linked Wiki page.  Look at the boot problems section and the section dealing with making Ubuntu the default boot selection:

[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu]("https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu")

---

### Post by greenglaze on 2010-04-03
Thanks for your reply.  I managed to fix this particular problem - it turned out that the "Time to display list of operating systems" box in Control Panel -> System -> Advanced -> Startup & Recovery wasn't checked.  Once I checked that box and re-booted my computer, the Windows Boot Manager screen appeared.

Unfortunately, that isn't the end of my problems.  I chose Ubuntu at the boot manager screen and it installed for about 10 minutes (while it was installing, it showed a slideshow of the main programs that are included in Ubuntu, such as web browser, text editor and so on).  The installation seemed to complete successfully, but then I was taken to a screen which had nothing but the Ubuntu logo on it and it remained frozen.  Nothing happened after that, and no menus appeared.  In the end I had to turn off my computer using the main switch, as there appeared to be no way for me to escape from that screen.

I believe my current OS is 32-bit, yet Wubi has downloaded and installed the 64-bit version of Ubuntu (the filename is ubuntu-9.10-desktop-amd64.iso).  Is this the source of my difficulty?

---

