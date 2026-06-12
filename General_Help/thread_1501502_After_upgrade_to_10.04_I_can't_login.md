---
title: "After upgrade to 10.04 I can't login"
date: 2010-06-04
forum: General Help
---

### Post by lol768 on 2010-06-04
I have recently upgraded to ubuntu 10.04 on a machine which I installed the kubuntu-desktop package onto. After the installation I tried to login to a KDE session and my password is accepted. The login screen disappears before the loading splash screen for KDE appears, however this only stays on the screen for a few seconds before the login screen appears again and the drumbeat sound is played (as if you had just turned it on).
Note that GRUB works fine.

[B]UPD (17:48:10 4/06/2010) I have re-installed plasma-desktop, kubuntu-desktop and kdemain packages and this has only caused a longer delay before the login screen is displayed again.
[/B] 
Please could somebody send me in the right direction to get this fixed. I have attached kdm.log.1 as a txt file as this may help diagnose some errors.
Thanks

---

### Post by DagMan on 2010-06-04
See if you're able to hit CTRL-ALT-F1 and login at the command line.  If not, then its possible that your password was lost in the upgrade.  It happened to me recently, where I had my user but no working password, or at least resetting the password fixed the problem.
To reset the password, you'de want to select recovery mode at the grub menu and then at some point it will ask you what action you want to take.  Select dropping to a root shell, or becoming root, or whatever, then type
passwd <username>
and set the new password.  If it asks you for your old password, and that fails, try doing it again and just hitting enter (what worked in my case).

Hopefully that works for you as well.

---

### Post by lol768 on 2010-06-05
Thanks for your quick reply, however I do not think this is a password issue because **I can go to tty1 (Ctrl + Alt + F1) and login there**, and **I** **_can_ login to GNOME**. Also if I try to login to kde with the wrong password it alerts me and when I enter the correct password it logs me in, but after about 5 seconds I am logged out again.

Also is it normal for the login screen to be at Ctrl + Alt + F8? I thought it should be F7.

Is there such a thing as a fail-safe KDE session, because I have noticed that there is a gnome option but none for KDE? 

I have googled this issue a bit and have also found that this is caused by /tmp having the wrong permissions set on it, so I used chmod to set it to 777, however this only seems to delay when I get logged out a little.

I have attached dmesg and /var/log/messages output after trying to log into kde.

Right now the only thing I can think of doing is formatting my partition and installing kubuntu.

Thanks

---

### Post by lol768 on 2010-06-05
OK, this may sound a bit drastic but I finally gave up trying to reinstall KDM and everything else so I decided to format my partition and install Kubuntu 10.04 and everything is working fine now.

DagMan, thank you for your help - it is appreciated.

I am installing Firefox now and setting up my new installation - however this has not really solved the problem so I shall leave the thread unsolved in case anyone wants to add any information.

I think that I will do a re-install when the next version of kubuntu/ubuntu is released to stop any potential problems.

---

### Post by gcpitts on 2010-06-05
I suspect that this issue is probably related to the issue I posted at [http://orice.ubuntuforums.org/showthread.php?t=1473233](http://orice.ubuntuforums.org/showthread.php?t=1473233), as I've also been able to enter my password, but the login screen reappears as if I hadn't logged in at all.

---

### Post by lol768 on 2010-06-05
Did you ever find a fix? I think I have seen this in the kde bug tracker (or kubuntu bug tracker) so I think people know about it. Still haven't got a clue as to what caused it.

Looked at your thread and although I had the problem where I couldn't login it seems like you had much worse problem with the screen cut off - something which I never experienced.

---

### Post by save2 on 2011-08-16
I found that in my case it wasn't authentication problem.
also someone suggested some "AIGLX" on xorg.conf which did nothing.

what solved my logins was:
reboot to root console
goto the relevant user home dir
see if there is .xsession-errors file. 
open it and see if you can fix the errors there.

---

