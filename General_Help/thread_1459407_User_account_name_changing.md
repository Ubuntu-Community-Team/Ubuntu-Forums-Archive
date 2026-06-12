---
title: "User account name changing"
date: 2010-04-21
forum: General Help
---

### Post by Mike32772 on 2010-04-21
I am fairly new to Ubuntu and while trying to configure samba I think that I screwed up my primary user account.  I had been on 9.10 and just upgraded to 10.4 a couple nights ago.  

I had been having problems where when I'm on the initial login screen my primary user would never show...it would show the two other accounts I had.  After upgrading I tried adding another user and noticed that on the left of the manage user screen, the primary user name (listed first) changed to be the same as what the new user was.  Unfortunately the primary user is the one that I use most often as the other users were built for my kids.  

Does anyone have any ideas how to get my user account working as the others (not changing names when a new user is added)?  When doing the SAMBA setup I had done several things within terminal, unfortunately I don't have the instructions anymore.  Would I be better off creating a new "main" administrator acocunt, delete the problem account and then re-add the account and copy the files to the new account?  Any tips or suggestions are appreciated.  Thanks in advance.

---

### Post by _0R10N on 2010-04-21
It looks like while configuring Samba you've changed dramatically your user's permissions and, possibly disallowed the privilege to login in the system. You can verify/rectify that configuration on the users/groups management windows, on the privileges tab. Notice that you must be logged in with a sudoer account.

Kind regards!

_0R10N >>

---

### Post by philinux on 2010-04-21
> **Mike32772 said:**
> I am fairly new to Ubuntu and while trying to configure samba I think that I screwed up my primary user account.  I had been on 9.10 and just upgraded to 10.4 a couple nights ago.  

I had been having problems where when I'm on the initial login screen my primary user would never show...it would show the two other accounts I had.  After upgrading I tried adding another user and noticed that on the left of the manage user screen, the primary user name (listed first) changed to be the same as what the new user was.  Unfortunately the primary user is the one that I use most often as the other users were built for my kids.  

Does anyone have any ideas how to get my user account working as the others (not changing names when a new user is added)?  When doing the SAMBA setup I had done several things within terminal, unfortunately I don't have the instructions anymore.  Would I be better off creating a new "main" administrator acocunt, delete the problem account and then re-add the account and copy the files to the new account?  Any tips or suggestions are appreciated.  Thanks in advance.

It would be easier to see exactly what you did. Terminal command history is stored in this file in your Home Folder.
~/.bash_history

Use gedit ~/.bash_history and paste back here with what you did.

Remember to put code tags around the text.

---

