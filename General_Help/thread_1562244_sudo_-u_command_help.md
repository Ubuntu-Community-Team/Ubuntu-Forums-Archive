---
title: "sudo -u command help"
date: 2010-08-27
forum: General Help
---

### Post by blindenvy on 2010-08-27
I have a general question regarding the use of sudo. If I ran the following command as user1:

sudo -u user2 script.sh

What environment setup scripts will be run upon that command being issued? Does it use the current environment variables for user1? Does it run any of the env setup files that may be in the home directory of user2? Does it reload what may be in /etc/profile.d/?

I hope what I am trying to gather is clear. Thanks in advance.

---

### Post by blindenvy on 2010-09-08
Any help would be most appreciated.

---

### Post by Achilles124 on 2010-09-08
Why don't you go into root and run from there?

---

### Post by gauravj on 2010-09-08
Hi

I guess this will depend on permissions of user2.
If for the script all permissions are satisfied then it will execute successfully.
Otherwise the famous one Permission denied. :-)

---

### Post by blindenvy on 2010-09-22
The problem is not with permissions but environment variables. 

<some background>
This server hosts a few "sites" each site has a directory and "messages" are stored in different folder in sub directories of the site directory. Each site manipulates these messages differently. In order to do this we keep track of what site we are working on via environment variables. So we run a script that sets the site. then we run the script that I am having trouble with to start/stop processing messages. These sites and messages are all owned by the same owner, we will call that owner "company"

<instance of problem>
User A sets his site. He then wants to start processing messages so he runs the script called process.sh which takes start or stop argument.

sudo -u company process.sh start

The problem occurs here because when this process.sh is run as user company. The env variables of user A are not used.

So my question still stands, what .rc or scripts get run to load env variables or aliases when you do a sudo -u ?

---

