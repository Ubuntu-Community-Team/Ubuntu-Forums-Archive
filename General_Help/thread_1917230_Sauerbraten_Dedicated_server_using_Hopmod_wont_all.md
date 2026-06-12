---
title: "Sauerbraten Dedicated server using Hopmod wont allow logins from users in server.conf"
date: 2012-01-29
forum: General Help
---

### Post by morbidchimp on 2012-01-29
Hi all.

I'm running on 11.10 server 32bit. I've installed Sauerbraten Dedicated server and additionally installed hopmod module for admin of the server.

When I was compiling latest hopmod from hopmod svn I ran into problems where it was failing at 85% during make and some searching and twiddling yielded me a patch that allowed me to compile and install hopmod.

[http://ubuntuforums.org/showthread.php?p=11647918#post11647918]("http://ubuntuforums.org/showthread.php?p=11647918#post11647918")

One of the features of hopmod is that you can log in via a browser and configure/view settings etc. The username and password is defined by running the command

**source bin/env.sh; bin/utils/luapp bin/utils/web_admin.lua <username> <password>** 

and the result is displayed like

**someuser someencryptedpassword**

which in turn I have to add to hopmoddir/conf/server.conf in the section 

web_admins["user1 password" "user2 password"]

When I attempt to log in to hopmod through its web admin and I'm asked for the username and password, no matter what I do, the username and password that I enter does not allow me to log in. 

I am however, able to log in via localhost on the same server saur dedicated is running and bypass the login screen. So I'm doing so by tunneling the port atm. This isn't ideal but is livable if I have to, but there are other issues I think might be related.

I was wondering, am I doing something wrong when I'm creating the users for section web_admins[] in the server.conf file, or if the patch I had added to get me past the origional problem of not been able to compile hopmod with make, make install somehow through something out of whack. 

I'm thinking if that is the case, my use of

**source bin/env.sh; bin/utils/luapp bin/utils/web_admin.lua <username> <password>** is flawed or the encrypted string I'm returned via web_admin.lua is somehow flawed in that at the point of comparing the login password with its own encrypted version they are different. 

An example of the server.conf file, the section I'm concerned with is on lines 116-120.
[http://code.google.com/p/hopmod/source/browse/trunk/conf/server.conf?r=2036]("http://code.google.com/p/hopmod/source/browse/trunk/conf/server.conf?r=2036")

In my own server.conf file I've defined one user as follows

"admin 9e14d588b0c1e422ec0d2025ba4319e0ae716b19e021bb17 UDEF-PD)V9TC(-I"


On top of this issue, assuming I live with the need to log in via localhost over ssh tunnel or whatnot once I connect to the server from sauer client (ingame) I am unable to Claim Master for that server. Many of the commands don't work and other settings like "coop edit" are not respected from server.conf.

I've included a copy of my server.conf file.

So either something with the software is out of whack, or I'm doing something wrong with configuration. Any help would be greatly appreciated or if anyone knows of a better/alternative way to admin sauer would do either.

Best regards

---

