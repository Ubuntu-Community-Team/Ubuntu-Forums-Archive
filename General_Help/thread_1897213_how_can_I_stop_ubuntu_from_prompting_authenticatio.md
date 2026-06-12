---
title: "how can I stop ubuntu from prompting authentication?"
date: 2011-12-18
forum: General Help
---

### Post by v0rtexer on 2011-12-18
Hello I want to remove my password from ubuntu but whenever I removed my password it would prompt me for authentication and it wouldn't allow me to enter nothing as a password so I had to change my password back to what it was and then enter it back in when I was prompted for authentication. I want to remove the feature of being prompted for authentication and then remove my password after changing that feature.
How would I remove the feature of being prompted? I have went through all of my system setting and I am stumped. I dont know much about the terminal so any ideas?

---

### Post by wildmanne39 on 2011-12-18
Hi, this question is not supported in the forums because it makes your system unsecure.
Thanks

---

### Post by Cheesehead on 2011-12-18
The description is very vague.

Perhaps the user has enabled auto-login? If so, gnome-keyring does still prompt for a password if the keyring is needed -for example- to enable network access.

The keyring has nothing to do with login or sudo access - it simply stores keys (like WEP keys) so you don't need to enter them manually every time. The keyring *requires* a password to unlock, so somebody else cannot use your keys to gain trusted access to networks. That cannot be disabled or bypassed. The only alternative is to not use keyring...which means entering your WEP key and other keys manually every time.

So if you need the keyring for network access (not everybody does), then auto-login is not a useful option for you.

---

### Post by MechaMechanism on 2011-12-18
See here on how to remove the need for a password.
[http://www.psychocats.net/ubuntucat/creating-a-passwordless-account-in-ubuntu/](http://www.psychocats.net/ubuntucat/creating-a-passwordless-account-in-ubuntu/)

In Applications/Accessories/Passwords And Encryption Keys Right click Passwords:login select change password.  Enter your current password and leave the new password lines blank.  Select use unsafe storage.

You should now have a password free system.  Contrary to popular belief you will probably experience no security issues as long as you do not install any server packages such as DNS or web server apache.  How ever you must take care not to accidentally delete system files.  Your fine in other words, ignore the sky is falling idiots.

How ever if there is a security issue with the flash plugin as an example and a dialog box pops up saying install me and you click yes then with out the password it will compromise your system.  But this scenario is very unlikely as there is no evil software for Linux out there, well there are some but they target servers.

Don't worry.

---

### Post by tears of the river on 2011-12-18
I asked the same thing when i was new to ubuntu and here is the link although i ended up not actually doing it coz it is alot better for security

[http://ubuntuforums.org/showthread.php?t=1888666&highlight=turn+password]("http://ubuntuforums.org/showthread.php?t=1888666&highlight=turn+password")

---

