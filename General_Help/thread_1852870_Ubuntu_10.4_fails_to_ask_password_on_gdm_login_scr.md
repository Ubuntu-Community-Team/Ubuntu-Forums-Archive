---
title: "Ubuntu 10.4 fails to ask password on gdm login screen"
date: 2011-10-01
forum: General Help
---

### Post by mteppo on 2011-10-01
Hi

I have been tinkering with my 10.4 LTS 64bit installation that I use for all-purpose whole family machine. I did the installation from scratch few days ago and initially there was no issue with the login.
I have set up user accounts for all members of my family + some guest accounts.

**Now that I did some maintenance on one of the guest accounts I managed somehow to disable the login-password query completely.**
I can use GDM2Setup to enable or disable the userlist.
Still when I either select a useraccount from the list _or_ type in user name I see no password prompt but gnome session is started immediately without any password being required.

Here is the GDM2Setup Screenshot.
[IMG]http://ubuntuone.com/46HOeKNn2otxmFqTqXYyCq[/IMG]

I tried to ask Google and search this forum but found only plenty of posts on how to _disable_ the password-asking.

Here is the screenshot on user settings for my user account - I take that password - ask on login should actually mean that this account is password - protected.

[IMG]http://ubuntuone.com/7jWjIa6I50wk9CAnBtngE4[/IMG]

So my question is what other things I need to check to resolve this issue?

Any links or tips would be very much appreciated. Also if there would be a better place for this post please do advice.

---

### Post by mteppo on 2011-10-01
Ok - replying to my earlier question.

The thing which I had done was to merge (manually) /etc/passwd and **/etc/group** files from earlier installation.
In this merge I happened to mess with some group id:s.
Namely **nopasswdlogin** group had same id as there was with another group (mythtv) to which all the users did belong to :oops:.

This caused all users to "belong" to nopasswdlogin - group and thus no questions asked on login.

So issue resolved.

---

