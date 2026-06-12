---
title: "Hiding applications from users w/o rights"
date: 2011-09-02
forum: General Help
---

### Post by lukas93 on 2011-09-02
Hey ubuntu-community,

I'm a newbie to linux and understood today the user/group/rights system which is easier than thougt.
But I have a problem for which I did not have found a solution yet (maybe because I'm from Germany and I did not know any keyword to search for..)

Problem 1:

I like to set my rights via usergroups.
For example, I created a usergroup called "skype". Only users in this group can access skype.
I did it like this:

```

$ sudo cd /usr/bin
$ sudo addgroup skype
$ sudo chgrp skype skype
$ sudo chmod 750 skype
$ sudo adduser lukas skype
$ sudo ls -l skype
$ -rwxr-x--- 1 root skype 21362968 2011-06-08 12:26 skype

```Currently I can use skype but users which are not in the group are getting an error-message.
Here is my question:
Can I disable the skype-application in applications -> internet? (GNOME)
Other users e. g. the guest-user shall not be able to see applications which are not granted for them. How to hide them?


Problem 2:
I like to edit the guest-users desktop. For examle the guest users shall not be able to see the system -> preferences menu (in german: system -> einstellungen) in the main menu.
How to realize this?

I hope you can help me :)
Thanks a lot! :)

---

### Post by papibe on 2011-09-03
Right click on the Ubuntu logo (on the menu). Select 'Edit Menus'. It will open an application. There you can uncheck Skype on the Internet menu, and Preferences under System.

Hope it helps,
Regards.

---

### Post by lukas93 on 2011-09-03
Thank you for your reply.

This may work for normal accounts but I took focus to the guest-session.
Each setting you'll do while the guest-session will be lost after logout :(
And there is the problem, i do not know how to edit the account of guest-sesion.

Is it possible to change the group of "guest" temporarily to "lukas" (or anything else), do my settings and switch back to the guest-group?

Is this actually possible at all?

---

