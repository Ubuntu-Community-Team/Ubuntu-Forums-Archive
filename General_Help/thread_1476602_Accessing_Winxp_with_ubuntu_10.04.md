---
title: "Accessing Winxp with ubuntu 10.04"
date: 2010-05-08
forum: General Help
---

### Post by sandman3838 on 2010-05-08
Hello

I hope someone could take a look at this and see whats going on?

I had some issues with Ubuntu 9.10 and I decided to do a fresh install of Ubuntu 10.04.

First here is some background.

1.  I disconnected all my HDs except for my Windows HD.
2.  Using Winxp CD I did a fixboot and then fixmbr.
3.  I rebooted the system and I was able to access Winxp.
4.  Using the Win_7 Recovery CD I let it recover Win_7.
5.  After rebooting I was able to access both Winxp and Win_7 from the Windows 7 bootloader menu.  No issues!
6.  I unplugged the Windows HD and plugged in the Ubuntu HD and booted up to the Ubuntu 10.04 cd and did a clean install.
7.  From here I rebooted several times to make sure Ubuntu was up and running.
9.  I plugged back in the Windows HD and booted the system up.
8.  Next once I was in Ubuntu I ran terminal with: 

sudo update-grub

9.  I rebooted and the results were:

'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu
	Ubuntu access  - OK  No issues!


"Windows 7 (loader) (on /dev/sdb1)" 
	
	(This entry opens up to Windows 7 Bootloader)
	
Win_7 access - OK No issues!
	
Win_XP access - FAILS After a moment with a blinking cursor System reboots!


"Windows 7 (loader) (on /dev/sdb5)"
	NOTHING HAPPENS NOT EVEN THE WINDOWS 7 BOOTLARDER JUST A BLINKING CURSOR?


I wouldn't mind it if just one of those two Windows Bootloader options in grub worked and would actually give me access to both windows XP and 7, which ever one is easier to fix?  Please take a look at the attached Script file it should help.  It was from "boot_info_script055" that I downloaded and ran.


Thanks for all your time and help.

---

### Post by ankur1990 on 2010-05-08
> **sandman3838 said:**
> Hello

I hope someone could take a look at this and see whats going on?

I had some issues with Ubuntu 9.10 and I decided to do a fresh install of Ubuntu 10.04.

First here is some background.

1.  I disconnected all my HDs except for my Windows HD.
2.  Using Winxp CD I did a fixboot and then fixmbr.
3.  I rebooted the system and I was able to access Winxp.
4.  Using the Win_7 Recovery CD I let it recover Win_7.
5.  After rebooting I was able to access both Winxp and Win_7 from the Windows 7 bootloader menu.  No issues!
6.  I unplugged the Windows HD and plugged in the Ubuntu HD and booted up to the Ubuntu 10.04 cd and did a clean install.
7.  From here I rebooted several times to make sure Ubuntu was up and running.
9.  I plugged back in the Windows HD and booted the system up.
8.  Next once I was in Ubuntu I ran terminal with: 

sudo update-grub

9.  I rebooted and the results were:

'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu
    Ubuntu access  - OK  No issues!


"Windows 7 (loader) (on /dev/sdb1)" 
    
    (This entry opens up to Windows 7 Bootloader)
    
Win_7 access - OK No issues!
    
Win_XP access - FAILS After a moment with a blinking cursor System reboots!


"Windows 7 (loader) (on /dev/sdb5)"
    NOTHING HAPPENS NOT EVEN THE WINDOWS 7 BOOTLARDER JUST A BLINKING CURSOR?


I wouldn't mind it if just one of those two Windows Bootloader options in grub worked and would actually give me access to both windows XP and 7, which ever one is easier to fix?  Please take a look at the attached Script file it should help.  It was from "boot_info_script055" that I downloaded and ran.


Thanks for all your time and help.
this is a zero day grub bug of 10.04.......
just install the updates of the ubuntu 10.04 by enabling all the sources it will fix it and you will then get your window option shown in the grub :KS

---

