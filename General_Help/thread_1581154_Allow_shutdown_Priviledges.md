---
title: "Allow shutdown Priviledges"
date: 2010-09-24
forum: General Help
---

### Post by Strategist01 on 2010-09-24
Hey guys.

Running Ubuntu 10.04.1 here and I need some help with very specific users privileges, namely one.

Basically, when I installed Ubuntu I created my account as the admin and two other accounts that are non admin. Now, one non-admin is my mom who sometimes needs to boot into XP to do her work (proprietary software that takes 6 hours to install and only runs on Windows  - now alternative) and she needs to shut the PC down.

However I am usually logged in and she can't do so as she is non-admin. I want her to be able to do so if I'm not there.

Now, I gave her admin rights - in order to shut the PC down, however I fear she doesn't know enough about Linux to have an admin's account and might do accidental damage.

How would I give her rights just to be able to shutdown the PC?

Thanks guys.

---

### Post by andrewthomas on 2010-09-24
[http://how-to.wikia.com/wiki/How_to_allow_non-super_users_to_shutdown_computer_in_Linux](http://how-to.wikia.com/wiki/How_to_allow_non-super_users_to_shutdown_computer_in_Linux)

---

### Post by searchfgold6789 on 2010-09-24
When you go in to set the user privileges, just uncheck what you *don't* want her to be able to do.
Or, you could log in as an administrator and set it so that the system shuts down after a while anyway.

---

### Post by Strategist01 on 2010-09-24
Thanks guys, managed to do that using the first article. Had to look up a few things (like how to add users to groups!) but got through.

---

### Post by andrewthomas on 2010-09-24
Glad to be of help.

---

### Post by Strategist01 on 2010-09-24
Hi, tried doing what the article says, but it didn't work. Am I doing something wrong, or could you simplify it for me a bit please? Thanks.

EDIT: Previous post: I thought it worked - however it didn't, now I am stuck :/

---

### Post by Strategist01 on 2010-09-24
Ok, just added her to the admin group graphically and restricted some privileges. Semmed easier. It's not the best solution I would have hoped for, but it is the only one that seems to work.

---

### Post by andrewthomas on 2010-09-24
What part did you have trouble with ?

1:   make shutdown group and add user to group

2: edit /etc/sudoers file using 'visudo'

adding
```
%shutdown ALL=NOPASSWD: /sbin/shutdown
```then
Then right click on the top panel and select add to panel and select custom application launcher and fill in command 

to reboot 'sudo /sbin/shutdown -r now' 
to power down 'sudo /sbin/shutdown -h now'

---

