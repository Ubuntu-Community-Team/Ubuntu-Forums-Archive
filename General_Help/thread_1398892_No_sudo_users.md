---
title: "No sudo users"
date: 2010-02-05
forum: General Help
---

### Post by Xi0N on 2010-02-05
I think i screwed up big time:

I was messing around with encrypted home directory for my user "a"
Then, i decided that the encrypted directory was giving me some headache, so, instead of going through the process of decrypting the home directory (if it ever exists), i preferred to create user "b", login as user "b", delete then user "a" and create it again.

the point is that, after doing so, i deleted user b from the admin group, and i seem to not added user a correctly to the group:

In a nutchell: I have no sudo users, i canot do sudo.......

How can i fix this issue?

thanks!

---

### Post by lotharmat on 2010-02-05
methinks you may need to use a live CD and add yourself to the group from the command line.

I'm not sure what commands will achieve this but someone here will!

---

### Post by Xi0N on 2010-02-05
Im currently only able to log in via ssh........ is there any other way? (instead of having to go again to where i have my server: This days im in another city)

thanks for your help anyway!!!!! :D

---

### Post by lotharmat on 2010-02-05
If you know the root password - you should be able to do it. But I know that default installations do not have a root password as such..

---

### Post by Xi0N on 2010-02-05
I dont know why, but webmin let me do some changes in the groups, and now i seem to have all ok again..... :popcorn:

---

### Post by lotharmat on 2010-02-05
+1 for webmin! :D

---

### Post by Xi0N on 2010-02-05
Webmin FTW! :KS:KS

---

