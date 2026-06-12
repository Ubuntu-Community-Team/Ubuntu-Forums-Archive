---
title: "weird upgrade msg when login via ssh"
date: 2010-04-18
forum: General Help
---

### Post by michael_j_w on 2010-04-18
So any one know why when i log in via ssh i get two versions of whether or not i need to update any files? here's the text i get:
```
Linux server 2.6.32-16-generic #25-Ubuntu SMP Tue Mar 9 16:33:52 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 (lucid)
Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
*** System restart required ***
Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
234 packages can be updated.
0 updates are security updates.
Checking for a new ubuntu release
No new release found
No mail.
Last login:
```
 
Note that no updates are indicated in the first iteration but that 234 are in the second. this has been like this for two weeks or so. the first one changes every time i run apt to upgrade the packages but the 234 stays the same. so how can i fix this? thanks!

---

### Post by gmargo on 2010-04-18
I believe this is caused by a bug in the server installation. However, it looks like you need a reboot, so you should reboot first to see if that restart message goes away.

Two different ways to fix the weird double motd display (assuming it is still present after reboot):

1. Remove or rename the **/etc/motd.tail** file.  Check the content of that file - I think you'll find it's the first (incorrect) part of the motd display. (That's strange - on my system, the incorrect part is first, on your's it seems to be last.)

2. Disable the motd display entirely.  Edit **/etc/pam.d/login** (and **/etc/pam.d/sshd**) and comment out the line with "pam_motd.so" mentioned.  Now the login will be speedy, as it should be.  This is my preferred "fix".

---

### Post by michael_j_w on 2010-04-18
Well done! renaming the **/etc/motd.tail** file did the trick! I didn't even have to do part two. This has been bugging me for weeks! Every time i login, i get that annoying reminder that something is wrong, but no more. Thank you very much for your help.
 
Michael

---

