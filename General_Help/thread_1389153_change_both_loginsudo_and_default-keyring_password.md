---
title: "change both login/sudo and default-keyring passwords with one operation?"
date: 2010-01-24
forum: General Help
---

### Post by tlroche on 2010-01-24
How to change both the login/sudo and default-keyring passwords with one operation? If I recall correctly, to change one's

[LIST]
[*]login and sudo password, one must use `passwd` or System>Preferences>About Me>Change Password
[*]default-keyring password, one must goto Accessories>Passwords and Encryption Keys>Passwords, rclick on keyring>Change Password
[/LIST]

Is there a way to do both with one operation? preferably from commandline? preferably in karmic?

---

### Post by dcstar on 2010-01-24
> **tlroche said:**
> How to change both the login/sudo and default-keyring passwords with one operation? If I recall correctly, to change one's

[LIST]
[*]login and sudo password, one must use `passwd` or System>Preferences>About Me>Change Password
[*]default-keyring password, one must goto Accessories>Passwords and Encryption Keys>Passwords, rclick on keyring>Change Password
[/LIST]

Is there a way to do both with one operation? preferably from commandline? preferably in karmic?

They are two different, unrelated things. The Keyring password is for GUI apps and has nothing to do with your account login password (which is used by sudo).

---

### Post by krispiebrown on 2010-06-09
Since Ubuntu 10.04 defaults to setting the keyring password to the same password as your user password (sudo) it become important to keep them aligned. I am very cautious and I have set up password policies as to ensure I change my password regularly BUT every time I do so I have to manually change the password of the keyring manually in the graphical interface.

If I knew how to do this by the command-line I could develop a script.

---

