---
title: "Authentication Failure."
date: 2010-05-18
forum: General Help
---

### Post by Ash-Lee on 2010-05-18
This problem is still here.

The only version of Ubuntu i have been able to use without this issue is 8.04LTS anything above wont accept my password.

Just installed 10.04LTS in the hope it has been sorted but it hasn't.

Surely there is a known problem here? There are several other posts with people having the same problem.

My password and username is correct, and changing the password at the prompt makes no difference, trust me i have tryed several times over the years.

Anything that requires my password, updates etc just doesn't work.

---

### Post by Ash-Lee on 2010-05-18
This is in my auth.log


> May 18 23:38:51 ash-desktop polkit-agent-helper-1[1670]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=ash rhost=  user=ash
May 18 23:38:56 ash-desktop polkit-agent-helper-1[1673]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=ash rhost=  user=ash
May 18 23:39:00 ash-desktop polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session1 FAILED to authenticate to gain authorization for action org.freedesktop.systemtoolsbackends.set for system-bus-name::1.52 [users-admin] (owned by unix-user:ash)

---

### Post by Ash-Lee on 2010-05-19
Anyone?

---

### Post by JohnVLang on 2010-05-21
Hi,

I can't offer any help - but i can say you are not alone! Same here, 8.04 worked great, upgraded to 10.04 now i can't log in. I've even tried a complete re-install of 10.04 from CD but still no log in "authentication failure"!

If i find a fix/work around i'll post back here...

J

---

### Post by ChronoSphere on 2010-06-15
This problem still has me baffled. All Ubuntu releases install and work fine on one PC, but not on my newer one. There has to be a fix.

---

### Post by Janith on 2010-06-15
Waa i don't know what to say:lolflag: :confused::confused::confused::confused::confused::confused::confused:

---

### Post by SisterNotes on 2010-07-18
When you did a fresh install of 10.04, did you selection the new option to secure your computer (I think it's step 7)? Then after login, get the screen that asks you to proceed with viewing the security code? (sorry I can't remember the actual wording). I selected this option and realized that I am not able to use the auto login option - terrible, bad, horrible things happen (I can't access the home directory). That's the situation on computer no. 1. On computer no. 2 - I also did a fresh install (and upon re-install) opted NOT to go for the super-high security option. I set up autologin (it's my son's laptop, not mine) and life was good...until I tried to login to his laptop using the account name and password that I had setup on the laptop - Authentication failure! Next, tried to log in using his id and password - same problem! Since he's out of town, I have no idea how long this has been a problem...unless he needed to do something that required re-entering his password (such as an update), he would not have had an problems.

Sorry, for rambling. Any additional input on why the auth failure is occuring would be appreciated.

---

### Post by lkjoel on 2010-07-18
Are you in the admin group?
You must be in it to use sudo.

---

### Post by SisterNotes on 2010-07-19
I solved my authentication failure issue by resetting my password as suggested in a similar post thread (1487187) [http://ubuntuforums.org/showthread.php?t=1523745&highlight=authentication+failure]("http://ubuntuforums.org/showthread.php?t=1523745&highlight=authentication+failure")

The instructions for resetting the password are here:
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

I'm not sure if this will solve your problem. But I think my authentication failure issues may have started as a result of a recent power outage. Apparently, because I do not have a battery in my laptop, if I do not properly shutdown before cutting the power, the login/password system gets corrupted.

---

