---
title: "Change password"
date: 2009-12-21
forum: General Help
---

### Post by J V on 2009-12-21
I can't change my password! I'm going to describe this step by step...

[LIST]
[*]Open up users and groups
[*]hit authenticate
[*]insert pass1
[*]choose my account
[*]hit properties
[*]hit change password
[*]type in pass1
[*]authenticate
[*]change to pass2 (Testing wheather ecryptfs would automatically change, it does, isn't that a security risk if someone logs in recovery mode?)
[*]log out
[*]log in with pass2
[*]promted for keyring password
[*]pass 1 didn't work
[*]pass 2 did
[*]Re-removed password on keychain (ecryptfs ftw)
[*]Tried to change password back (here's the tricky part)
[*]Open users and groups
[*]Hit authenticate
[*]Insert pass 2
[*]Go to properties
[*]Change password
[*]insert pass2
[*]authenticate
[*]change to pass1
[*]attempt to change again to check weather password has changed: **no, password hasn't changed**
[/LIST]
Anyone know what I'm doing wrong? Changing passwords was hard jaunty too, whats wrong? :/

---

### Post by fm1234 on 2009-12-21
if you are logged in as your_userid, open a terminal and try

passwd your_userid

---

### Post by J V on 2009-12-21
The reason I didn't just do that in the first place, is because:

a: That would screw with my encrypted home directory (Or did they incorporate it into the CLI as well?)
b: I would like to fix my GUI, it would help for people to be able to change their passwords more than once :)

Edit: Preferences > about me > change password works as intended... Is there a bug report on this?

---

