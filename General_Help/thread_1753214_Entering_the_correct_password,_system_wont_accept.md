---
title: "Entering the correct password, system wont accept"
date: 2011-05-08
forum: General Help
---

### Post by jasonab1 on 2011-05-08
HI (it a long one)

I have been using Ubuntu for two years now. I have had my ups and downs but until today never a problem that made me think of going back to windows. I am currently using Ubuntu LTS 10.4.

It started about February. Whenever I tried to install a package the system would not accept my password. I checked cap locks, typed it in gedit just to make sure all the keys were working and they were. After typing in the password about 30 times every time the same it would authenticate properly. The problem was not only limited to Ubuntu Software Center. The same thing happens in the console when I sudo and when i try to login in a terminal. The problem was infrequent.

Over the last few months the problem got worse and no amount of attempts worked. I tried some solutions on the net. One was to remove pam-bind. I did this and rebooted. The problem seemed to be solved. I installed some updates without any issues. The very next day it happened again.

I tried another solution if found which involved changing permissions on a policy-kit file I cant remember which. I struggled and couldn't. I went into a root shell via recovery mode and set the permissions there. Rebooted and it seemed fine. A week passed and I didn't need to authenticate anything. Then on Saturday I needed to install a package and the exact same problem occurs.

I have disconnected my KVM switch, switched keyboards, changed my password in root shell recovery mode. I just cannot authenticate. I formatted all the partitions of my pc except /home. After installation I tested and dammit still its not accepting my password. Thinking it could be a config file in the home directory. I installed linux from scratch, repartitioning and formating. From the start it does not accept my password.

I can install packages from rootshell in recovery mode and do anything admin wise there but its annoying me. Anyone know what it could be? My password is Yellow1. I am beginning to think its hardware related.

Part of the auth.log
> May  8 23:22:14 jason-desktop polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session1 (system bus name :1.18 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_ZA.UTF-8)
May  8 23:23:24 jason-desktop sudo: pam_unix(sudo:auth): authentication failure; logname=jason uid=0 euid=0 tty=/dev/pts/0 ruser= rhost=  user=jason
May  8 23:23:37 jason-desktop sudo:    jason : 3 incorrect password attempts ; TTY=pts/0 ; PWD=/home/jason ; USER=root ; COMMAND=/usr/bin/apt-get update
May  8 23:46:57 jason-desktop sudo: pam_unix(sudo:auth): authentication failure; logname=jason uid=0 euid=0 tty=/dev/pts/2 ruser= rhost=  user=jason
May  8 23:46:58 jason-desktop sudo: pam_unix(sudo:auth): conversation failed
May  8 23:46:58 jason-desktop sudo: pam_unix(sudo:auth): auth could not identify password for [jason]
May  8 23:46:58 jason-desktop sudo: pam_unix(sudo:auth): conversation failed
May  8 23:46:58 jason-desktop sudo: pam_unix(sudo:auth): auth could not identify password for [jason]
May  8 23:46:58 jason-desktop sudo:    jason : 3 incorrect password attempts ; TTY=pts/2 ; PWD=/home/jason ; USER=root ; COMMAND=jason


---

### Post by relay_man on 2011-05-09
I've had a similar problem at times with 10.04 on two desktop units,and also with earlier installations of 8.10 on the same two desktops and one laptop.
This happened not only during initial login, but also when attempting to authenticate so I could get to the synaptic package manager.

I've found through experimentation that I sometimes must enter my password very slowly.  That is to say I must enter each character of my password with a 2-3 second pause between each keystroke.

It seems odd to me that anyone could enter characters from the keyboard with such speed that the computer could not keep track of what was being typed, but the fact remains that when my password gets rejected with more than two consecutive attempts, I now just slow down and use 1 finger to enter my password.  So far, it has worked every time.

Hope this helps.

---

### Post by jasonab1 on 2011-05-09
Thank you relay-man. I really appreciate the assistance.

Sadly, that did not work. I' going to try again tomorrow. I am also in the process of downloading 11.04. If I have the same problem I am going to buy a new computer. This PC is about 6 years old now and I've been looking for a reason to replace it.

---

### Post by jasonab1 on 2011-05-10
I installed Ubunty 11.04 and used the same password. After setup was done I had the exact same problem. I rebooted into recovery mode and reset the password and exited. I got a console requesting me to login. The username and new password worked no problems. I rebooted the pc. When I got in I tried to install packages and again the same issue. This was however different, after the 4th try it accepted it. I rebooted the PC and oddly enough I was greeted by a login screen (I use auto login) and no matter how hard I tried nothing worked.

I am reinstalling 10.04 and doing one thing different than the previous time. If that doesn't work then I give up.

---

### Post by jasonab1 on 2011-05-11
I installed 10.04, but this time I changed two things. I disconnected my backup hard drive which is an SATA so there was only my IDE drive left. During installation I partitioned it so that that there was a small piece of the drive that wasn't being used. This piece of the drive is where my /tmp folder was mounted. I think there may be an issue there as the system twice complained that it couldn't mount /tmp while it was booting up.

It seems to be working fine with no issues and it just has to hold until I get my new computer in a couple of days.

---

