---
title: "The system is running in low graphics"
date: 2012-06-02
forum: General Help
---

### Post by ShannonMcC on 2012-06-02
"Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself."
 
I have updated my my laptop ( Lenovo Ideapad Z560) from Windows 7 to Ubuntu 12.04. I am using both Windows 7 and Ubuntu 12.04 on my laptop now. 
My laptop uses: **Intel HD Graphics in processor,external analog monitor support via VGA DB-15 connector and digital monitor supportvia HDMI, HDCP-compliant**
 
I am unable to use any of the 4 options following the prompt given above. 
 
Options:
1. Run in low-graphics mode for just one session.
2. Reconfigure graphics.
3. Troubleshoot the error.
4. Exit to console login.
Results:
1. Gives no change and loops back.
2. No options able to be changed.
3. Troubleshooting gives no new solutions in any manner so far.
4. Sends me back to login.
 
Using Ctrl+Alt+F1, I used
sudo apt-get update (upgrade)
sudo apt-get install -f
sudo apt-get --configure -a
 
Had 40 Updates and 288 Upgrades but not solutions for my error.
 
I am willing to put hours of work into my laptop to get it moving again but I need the support that I know I can get from here. Thanks!
 
-ShannonMcC

---

### Post by wilee-nilee on 2012-06-02
Have you looked in the additional drivers app?

Post the actual card.
  	 	 	 	 	 	   ```
lspci | grep VGA 
```

---

### Post by ShannonMcC on 2012-06-02
I fixed the issue by simply reinstalling Ubuntu to my hard-drive not syncing it with Windows 7 and using Ubuntu 12.04 solely. I will be searching for coding sources though as well for further users.

---

### Post by traditionalist on 2012-06-02
> **ShannonMcC said:**
> "Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself."
 
I have updated my my laptop ( Lenovo Ideapad Z560) from Windows 7 to Ubuntu 12.04. I am using both Windows 7 and Ubuntu 12.04 on my laptop now. 
My laptop uses: **Intel HD Graphics in processor,external analog monitor support via VGA DB-15 connector and digital monitor supportvia HDMI, HDCP-compliant**
 
I am unable to use any of the 4 options following the prompt given above. 
 
Options:
1. Run in low-graphics mode for just one session.
2. Reconfigure graphics.
3. Troubleshoot the error.
4. Exit to console login.
Results:
1. Gives no change and loops back.
2. No options able to be changed.
3. Troubleshooting gives no new solutions in any manner so far.
4. Sends me back to login.
 
Using Ctrl+Alt+F1, I used
sudo apt-get update (upgrade)
sudo apt-get install -f
sudo apt-get --configure -a
 
Had 40 Updates and 288 Upgrades but not solutions for my error.
 
I am willing to put hours of work into my laptop to get it moving again but I need the support that I know I can get from here. Thanks!
 
-ShannonMcC

I don't think there is a solution yet, I couldn't find one.  This may  be of interest to you;

[http://blogs.operationaldynamics.com/paul/opensource/not-unified-removing-unity-from-ubuntu-12-04-lts](http://blogs.operationaldynamics.com/paul/opensource/not-unified-removing-unity-from-ubuntu-12-04-lts)

After removing unity as described there ( Scroll down), my graphics worked.  So now I use "GNOME Classic".

I have no idea whether this will help you, but it can't hurt to try.

---

### Post by fymox on 2012-09-24
I am running Ubuntu 12.04 (alongside WinXP). I installed version 8 a few years back, and have been upgrading ever since. 2 days back, 12.04 was running fine. Then it told me to please reboot so updates could be applied. On reboot, I get the message "your screen, graphics card, and input device settings could not be detected correctly. You will need to configure them yourself." At this point, the Keyboard and Mouse are not functional, so I cannot click anything or configure anything. PLEASE HELP! 

During Boot, when Grub comes up, the keyboard works just fine, letting choose which Kernel version I want or to boot Windows. Can I boot to a Linux CD and run some kind of Uninstall script on the last set of Updates?

My system has an Intel Quad Core Duo prog, 4 gigs of DDR2 and a Geforce 8400 vid card, if that matters.

please help. [email]fymox@yahoo.com[/email]

---

### Post by prohank on 2013-02-04
Getting the same problem as fymox mentioned
No one of enough knowledge here to solve this?
Please help!

---

### Post by Yellow Pasque on 2013-02-04
> **prohank said:**
> Getting the same problem as fymox mentioned
No one of enough knowledge here to solve this?
Please help!
Unless you have the same hardware, please make a new thread instead of bumping this old one. Also, I would suggest giving more info in the new thread, such as your Xorg log (/var/log/Xorg.0.log).

---

### Post by prohank on 2013-02-05
I am a newbie as you can see.
And my problem is exactly what the OP describes.
Still making a new thread hoping we will reach to the solution.

---

