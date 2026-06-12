---
title: "how to enable jre in firefox-3.6 beta"
date: 2009-12-23
forum: General Help
---

### Post by shaon3343 on 2009-12-23
[SIZE=2]**hi I'm using ubuntu 9.10 and i've installed firefox-3.6beta. i also uninstalled the previous firefox-3.5.3. now when i run some java applet my firefox-3.6 says "missing plugins" but sun-java6-jre is installed in my ubuntu. Those java applet runs finely with opera browser.So what should i do to enable jre in firefox-3.6? please help me.**[/SIZE]

---

### Post by scottuss on 2009-12-23
Presumably then, you have sun-java6-plugin installed too?

---

### Post by shaon3343 on 2009-12-23
[SIZE=2][B]> **scottuss said:**
> Presumably then, you have sun-java6-plugin installed too?

:lolflag:  sorry , it was not installed!! I'm now installing it. thanks for reply.[/B][/SIZE]

---

### Post by scottuss on 2009-12-23
No problem. Post back here to let us know if that fixed it :D

---

### Post by shaon3343 on 2009-12-23
[SIZE=2][B]> **scottuss said:**
> No problem. Post back here to let us know if that fixed it :D
oops :confused::confused:! its not fixed yet!! I've installed "sun-java6-plugin" but still now when i run any java applet it shows: 
"additional plugins required " !!! please help. java applets are not working on chromium browser too. But in opera they are working fine.[/B][/SIZE]

---

### Post by shaon3343 on 2009-12-23
**that applets are working on newly installed firefox-3.5.8. But those are not working on firefox-3.6beta and on chromium browser!!  any idea??**

---

### Post by timchesonis on 2010-01-12
> **shaon3343 said:**
> **that applets are working on newly installed firefox-3.5.8. But those are not working on firefox-3.6beta and on chromium browser!!  any idea??**

I too, am having the exact same problem.  I'm using Firefox 3.6pre (nightly builds), and the issue is that the java plugin is NOT installed on 3.6, but it IS installed on 3.5.8.  How do we get the java plugin to be recognized in 3.6?

---

### Post by scouser73 on 2010-01-12
This is what I've found [http://forums.mozillazine.org/viewtopic.php?f=23&t=1576825](http://forums.mozillazine.org/viewtopic.php?f=23&t=1576825)

---

### Post by timchesonis on 2010-01-12
> **scouser73 said:**
> This is what I've found [http://forums.mozillazine.org/viewtopic.php?f=23&t=1576825](http://forums.mozillazine.org/viewtopic.php?f=23&t=1576825)

Yes, I have read this thread, but found it a bit confusing.  I'm running Ubuntu 9.10 using AMD64.

My libnpjp2.so file is located here:

/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libnpjp2.so

What should the command line be that I need to use to make it happen?

---

### Post by forubu on 2010-01-12
The first thing to check is whether apparmor is in enforce-mode for firefox 3.6.

Run: **sudo aa-status** 

If Firefox 3.6 is listed as an enforced profile you could set it to complain mode.

Run: **sudo aa-complain /etc/apparmor.d/usr.bin.firefox-3.6**

---

### Post by timchesonis on 2010-01-12
> **forubu said:**
> The first thing to check is whether apparmor is in enforce-mode for firefox 3.6.

Run: **sudo aa-status** 

If Firefox 3.6 is listed as an enforced profile you could set it to complain mode.

Run: **sudo aa-complain /etc/apparmor.d/usr.bin.firefox-3.6**

Here are my findings:

apparmor module is loaded.
10 profiles are loaded.
10 profiles are in enforce mode.
   /usr/lib/connman/scripts/dhclient-script
   /usr/share/gdm/guest-session/Xsession
   /usr/bin/evince-previewer
   /usr/sbin/tcpdump
   /usr/lib/cups/backend/cups-pdf
   /usr/bin/evince-thumbnailer
   /sbin/dhclient3
   /usr/bin/evince
   /usr/sbin/cupsd
   /usr/lib/NetworkManager/nm-dhcp-client.action
0 profiles are in complain mode.
2 processes have profiles defined.
2 processes are in enforce mode :
   /sbin/dhclient3 (12680) 
   /usr/sbin/cupsd (1620) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

Any ideas?

---

### Post by SirBismuth on 2010-01-13
> **timchesonis said:**
> Yes, I have read this thread, but found it a bit confusing.  I'm running Ubuntu 9.10 using AMD64.

My libnpjp2.so file is located here:

/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libnpjp2.so

What should the command line be that I need to use to make it happen?

Have you tried creating a symlink to that file, and in placing it in Firefox's (3.6) plugins folder?.  I had to do that when I installed 3.5.7 side-by-side with 3.5.6, as I wanted 3.5.7 before it appeared in the repos.  I would guess it's much the same with 3.6.

B

---

### Post by timchesonis on 2010-01-13
> **SirBismuth said:**
> Have you tried creating a symlink to that file, and in placing it in Firefox's (3.6) plugins folder?.  I had to do that when I installed 3.5.7 side-by-side with 3.5.6, as I wanted 3.5.7 before it appeared in the repos.  I would guess it's much the same with 3.6.

B

My problem is that I don't know what the command line is to create the symlink for this file.  Would you mind providing the exact command line?

---

### Post by forubu on 2010-01-13
> **timchesonis said:**
> My problem is that I don't know what the command line is to create the symlink for this file.  Would you mind providing the exact command line?

Try these two commands:
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins/libnpjp2.so
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libnpjp2.so /usr/lib/xulrunner-addons/libnpjp2.so

Then restart Firefox and check if the java plugin is registered.
If it is registered check if it is correctly recognized at [java check site]("http://java.com/en/download/installed.jsp").
Sometimes Firefox will freeze up during checking which indicates the java plugin is not correctly installed.

---

### Post by timchesonis on 2010-01-13
> **forubu said:**
> Try these two commands:
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins/libnpjp2.so
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libnpjp2.so /usr/lib/xulrunner-addons/libnpjp2.so

Then restart Firefox and check if the java plugin is registered.
If it is registered check if it is correctly recognized at [java check site]("http://java.com/en/download/installed.jsp").
Sometimes Firefox will freeze up during checking which indicates the java plugin is not correctly installed.


You nailed it!  This worked perfectly.  Thank you!

---

