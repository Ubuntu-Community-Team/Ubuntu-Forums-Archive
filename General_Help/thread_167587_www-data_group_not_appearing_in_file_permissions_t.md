---
title: "www-data group not appearing in file permissions tab"
date: 2006-04-28
forum: General Help
---

### Post by nick1 on 2006-04-28
Greetings,

I'm hoping you can help me with this issue I'm experiencing in Ubuntu 5.10:

in /var/www/testdir I have a file named test.txt.  When I right-click that file, goto Permissions, and select the File group drop-down menu, I do not see the group named www-data listed.

However, when I goto System > Administration > Users and Groups and check Show all users and groups, I can see that the www-data group does indeed exist.

My question is:  why isn't the www-data group listed in the filename > permissions > File group drop-down menu?  And how do I go about making it appear there?

Thank you for your time,

*Nick*

---

### Post by Mr. Picklesworth on 2007-10-20
Old thread, but I have had the same problem in Gutsy. If anyone knows why this is, that would be great :)

This thread seems to have a high ranking on Google, so it would be good to solve the issue!


Okay, The Clunky Guide to a solution:

For now, this is solvable with the terminal. Open the terminal...

First, you need the gid for the www-data group. One way to do this is to read through /etc/group (cat /etc/group). www-data should be listed somewhere. The format is Name:Password:ID:Users. Take note of the ID, you will need it later. (For me, it is 33).

In my case, every web site has its own unprivileged user account. Apparently this is odd, but I find it tidy, since *good* remote file transfer services (ssh) can instantly make use of that with no extra setup.

There are a few things you can do. You can add a user to the www-data group (sudo adduser user www-data). This way, files created by the www server can be accessed by that user.

In my case, since I wanted PHP to stop giving me problems when *it* accessed the site's data, I made www-data the main group for the site's user. This is done with "sudo usermod -g 33 theuser". That way, the user can safely say whether to allow group access with www-data.

---

