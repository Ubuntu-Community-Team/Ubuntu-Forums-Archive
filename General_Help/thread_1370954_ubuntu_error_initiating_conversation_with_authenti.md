---
title: "ubuntu error initiating conversation with authentication system"
date: 2010-01-02
forum: General Help
---

### Post by Gionani7 on 2010-01-02
I got this ERROR shortly after trying to eliminate the need to enter my keyring for the network applet. This ("error initiating conversation with authentication system") at the login screen. I want to note some things.
-Im running 64 bit 9.10 Ubuntu
-I used (@include common-pamkeyring)
-I disabled the autologin option prior to restarting my desktop
-I could not log back in through graphical interface.
So at this point what I did was this.
Restart
Held "Esc"
Entered the root shell
And entered this command: sudo nano /etc/pam.d/gdm

I deleted the line(@include common-pamkeyring)

Hit "F3" to save

Hit "F2" to exit 

Ran command: sudo reboot

Now I was able to login regularly through the graphical interface.

HOPE THIS HELPS THOSE WHO FIND THEMSELVES AT THESE ODDS.

My Question is, Is there any way I can stop having to enter my keyring without going through this again with 9.10 Ubuntu??? HELP PLZ

---

### Post by toomanyplugs on 2010-01-08
I had this same error with the same conditions: pam, network manager keyring access, using Karmic Netbook Remix.

Thanks for posting a solution!

Regarding the Network Manager asking for keyring on autologin: I bypassed the issue of needing the keyring this way (for a wireless connection):

Open Network Connections
Select which connection you are using (wired/wireless, etc.)
at the bottom of the first tab is a checkbox to make the connection "Available to all Users".

This made network manager stop asking for access to the keyring on login (auto or manual).

Nik

---

### Post by heino74 on 2010-02-18
Thx... you've saved me a lot of time reinstalling.

---

### Post by NeverSage on 2010-05-01
Thanks Gionani7 and toomanyplugs!  I thought I was really stuck there

---

### Post by windfix on 2010-05-06
You are my hero this morning.  Ran updates at home (Lucid 10.4), booted at work and was locked out of my system.  As an Ubuntu evangelist, it's really bad if I have to cry for help and this was a major problem.  Solved in seconds, THANK YOU!

---

### Post by aircaptbigmac on 2010-05-07
Thank you guys so much. HUGE help!

---

### Post by TripleEye on 2010-05-19
Yes, thank you! It worked for me too!

---

### Post by specopus on 2010-08-22
I have this same error message coming up, but I never used the @include common-pamkeyring command in the /etc/pam.d/gdm file. Wondering if anyone knows of something else that can cause this error to come up. If it is of any help, I am currently running ubuntu 10.04 dual booting with win7.

---

### Post by willis575 on 2010-08-24
I am having the same problem, except holding the ESC key does nothing for me. How can I get into a command prompt before the login screen?

---

### Post by gesquive on 2010-09-02
Pressing ctrl+alt+F1 should get you to the command prompt. To get back to the GUI press ctrl+alt+F7. You can actually use F1-F6 to get to a different prompt.

---

### Post by giannosfor on 2011-05-18
Thanks that works great!!!

---

### Post by Krzysztow on 2011-05-25
Worked for me as well, thanks!

---

### Post by sagirfahmid3 on 2011-10-16
YOU ARE AWESOME! I wanted to take my time to thank you by signing up over here and commenting!  If there was a rep system like VBulletin, I would have gave you +10000! EXCELLENT!

---

