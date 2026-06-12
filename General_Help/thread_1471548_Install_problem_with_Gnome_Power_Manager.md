---
title: "Install problem with Gnome Power Manager"
date: 2010-05-03
forum: General Help
---

### Post by Seseli on 2010-05-03
On my login-screen, there is a message saying that the configuration defaults for Gnome Power Manager have not been installed correctly. I can still log in and work normally, but it seems to me that the system is pretty slow (which might or might not be because of this). It's been there for a while when I used version 9.10, but didn't disappear when I updated to 10.04. I searched for other threads with this problem, and found:

1) This one: [http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error](http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error) 
saying that it could be because the root drive was full, and said that I could run "sudo apt-get clean" to try to solve it. This didn't work, and it doesn't look like I'm low on space, anyway. Plus I can log in normally, so it doesn't look like the same problem. 

2) This one: [http://ubuntuforums.org/showthread.php?t=980711](http://ubuntuforums.org/showthread.php?t=980711)
advises me to run "sudo dpkg --configure -a", which seems to have worked for other people, but it didn't help me--when I restart, I still get the same error message. 

Anyone have other tips?

---

### Post by P4man on 2010-05-03
well, I googled on the error and found this must improbable post:

> This may be a candidate for the most misleading error message of all time!

You will get this message if gconf-sanity-check-2 tries to write a test file into /tmp and can't read it back. It can be caused if you erase the /tmp directory and allow the system to create a new one automatically. It does so with the permissions set to read and execute only, so the test file cannot be written.

Change the permissions of /tmp to 777 and it will fix it.


The command line is chmod 777 /tmp 

And yes, that is a reply to the same error message you are having (although on fedora:
[http://forums.fedoraforum.org/showthread.php?t=226569](http://forums.fedoraforum.org/showthread.php?t=226569) )

add sudo to that command and give it a try

```
sudo chmod 777 /tmp
```

---

