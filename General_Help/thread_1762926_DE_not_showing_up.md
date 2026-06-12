---
title: "DE not showing up"
date: 2011-05-19
forum: General Help
---

### Post by mirandansa on 2011-05-19
I've been running Ubuntu 10 and then 11 on a small Dell laptop for  several months without a problem until today. I logged in and waited for  the desktop environment to show up as usual. It didn't, except the  familiar background and the responsive mouse pointer. 4 messages popped  up consecutively:

[LIST]
[*]Could not update ICEauthority file /home/miranda/.ICEauthority
[*]There is a problem with the configuration server.
 (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
[*]It seems that you do not have the hardware required to run Unity. Please  choose Ubuntu Classic at the login screen and you will be using the  traditional environment.
[*]Nautilus could not create the following required folders: /home/miranda/Desktop,/home/miranda/.nautilus.
[/LIST]
 I looked for solutions regarding the first message. I found a few threads including this one:
[http://ubuntuforums.org/showthread.php?t=949750](http://ubuntuforums.org/showthread.php?t=949750)
As instructed, I got into recovery mode and then "drop to root shell prompt", and tried this code (both with and without sudo):

```
chown miranda:miranda /home/miranda/.ICEauthority
```I always get the following output:

```
chown: cannot access `/home/miranda/.ICEauthority': No such file or directory
```As for the other three messages, I don't know what to do.

I recall I previously tried to tweak things about my account so that, among other things,  I wouldn't be asked to type the password each time I log in. I suspect  that might have messed up my account, resulting in these error messages during log in.

Any suggestion? Thanks in advance.

---

### Post by Krytarik on 2011-05-20
I guess that the worse part of your issues arose because you have an encrypted home directory and enabled passwordless login. This way your home directory doesn't get decrypted upon login.

For a start, restore that functionality by disabling the passwordless login again:

1. Boot into "recovery mode -> root shell prompt".

2. Remove your username from the group "nopasswdlogin" in these files:
- "/etc/group"
- "/etc/gshadow"
```

nano /etc/group
nano /etc/gshadow
```[INDENT]- press Ctrl+O to save
- confirm with Return/Enter
- press Ctrl+X to quit
[/INDENT]Regarding the Unity issue, see these troubleshooting guides:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)
[http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

Greetings.

---

### Post by mirandansa on 2011-05-20
Problem solved. Thank you very much.

---

