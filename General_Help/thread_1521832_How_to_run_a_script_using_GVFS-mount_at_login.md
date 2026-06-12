---
title: "How to run a script using GVFS-mount at login?"
date: 2010-07-01
forum: General Help
---

### Post by risbac on 2010-07-01
The situation:
-Lucid Lynx
-Likewise-open to connect to an AD

The idea:
-add all network shares to the nautilus favourite places

The problem:
-our script is working fine if you are running the script manually from an opened session
-it's not working when placed in /etc/profile.d

What the script is doing:
-reading the .bat script name from the AD using the user login
-mounting the netlogon share
-reading the content of the netlogon script
-finding the network share names and adding them to the nautilus favourite places

What is failing:
it does not mount the netlogon share using gvfs-mount
Maybe because it's run too early in the process? 

if you have any idea, that would be great

Please note that a new user may log in any time, and we want this to be entirely automatic. So we cannot put the script in /home/login/*, as the home is not created yet at first login. 

Thanks in advance !

---

### Post by gzarkadas on 2010-07-01
gvfs cannot be called in your situation (ie from /etc/profile.d). Those scripts are executed too early, befaure the login screen, so gvfs is not yet loaded (use `cat /etc/gdm/Xsession | less' to verify; and read below). If you want to go that way, you need to know how gdm is loading. See [this thread]("http://ubuntuforums.org/showthread.php?t=1517628") and the docs pointed by the two links at the bottom of [this post]("http://ubuntuforums.org/showpost.php?p=9522065&postcount=13"). 

I believe -at first sight; not searched it in depth- that what you want to accomplish can be done if you put the appropriate commands in `/etc/gdm/PreSession/Default'.

---

### Post by risbac on 2010-07-02
Thanks a lot for your feedback.
I just quickly tested it, but it does not seem to work. I don't know exactly what is failing yet though, I will need to spend more time on it and look at the links you provided.

---

### Post by artooro on 2010-09-08
> **risbac said:**
> Thanks a lot for your feedback.
I just quickly tested it, but it does not seem to work. I don't know exactly what is failing yet though, I will need to spend more time on it and look at the links you provided.

Did you have any luck with this risbac?

---

### Post by artooro on 2010-09-08
I found the best solution using this thread:

[http://ubuntuforums.org/showthread.php?t=1194530](http://ubuntuforums.org/showthread.php?t=1194530)

Basically create the .desktop file for each user under /home/user/.config/autostart/ which runs the gvfs-mount commands inside a shell script.

---

### Post by risbac on 2010-09-27
SOrry, just noticed your answers.

Yes I found a solution. I have added the script in the list of programs to run after login in the /etc/skel folder and this way, it adds it automatically to any new account.

So now anybody connecting on of the computers will have automatically its network shares in the favorites of Nautilus. Quite cool ! ;)

---

### Post by gzarkadas on 2010-09-27
> **risbac said:**
> SOrry, just noticed your answers.

Yes I found a solution. I have added the script in the list of programs to run after login in the /etc/skel folder and this way, it adds it automatically to any new account.

So now anybody connecting on of the computers will have automatically its network shares in the favorites of Nautilus. Quite cool ! ;)

Well done :cool:! When you say "in the list of programs to run after login" you mean inside `.bashrc' ?

---

