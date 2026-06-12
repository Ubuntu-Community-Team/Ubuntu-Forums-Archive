---
title: "Sudoers Problem"
date: 2012-01-17
forum: General Help
---

### Post by OldManRiver on 2012-01-17
All,

Been posting on thread:

[http://ubuntuforums.org/showthread.php?p=11619443#post11619443](http://ubuntuforums.org/showthread.php?p=11619443#post11619443)

and noticed it is set to "closed" but still taking input, so reposting a new thread, so the "SOLVED" status will not get me ignored.

My problem is:

I have a 10.04 server and having problems with obtaining root from "sudo".

I hold down the "Shift" key, get the menu and enter 'e' to edit the options. I've entered the rw init=/bin/bash, but does nothing for me.

My problem is I have no sudoers users, so can not get to any root functions and everything I tried from the HOWTO at:

[http://burnz.wordpress.com/2008/09/0.../#comment-4385](http://burnz.wordpress.com/2008/09/0.../#comment-4385)

Does not allow me to get to and edit the /etc/sudoers file to add users with admin rights.

I finally got into my /etc/sudoers file using the HOWTO at:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

but find that I have defined the 3 users of:

user1 ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS
user2 ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS
user3 ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS

but when logging in as one of these users, and then issuing the "sudo su" command, still get the error:

"No sudoers users found"

Can someone explain what is up with this? Is this a group settings issue?

Thanks!

OMR

---

### Post by OldManRiver on 2012-01-17
All,

Figured it out!  Since I got root through the grub menu process, I edited the /etc/passwd file and changed the value of user2 from 1001:1001 to 0:0 and now I get root logging in as that user.

Sorry to bother you all.

Thanks for being a sounding board while I figured it out!

OMR

---

