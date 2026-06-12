---
title: "So let me get this straight"
date: 2010-10-11
forum: General Help
---

### Post by petrasflorin on 2010-10-11
If I disable the input password on login (login without password) then I have to type the password anyway after login for the damn keyring which I have no idea what is used for.

---

### Post by renkinjutsu on 2010-10-11
The keyring is used for many things.. ssh, Wifi ap encryption keys.. and Google-chrome uses keyrings to store your passwords for different webpages.

No idea what you have to type in if you have no password. :confused:

---

### Post by ean5533 on 2010-10-11
I've experienced what he's talking about. He does have a password; every login has a password. He just has it set so that his password isn't required to log in (you can set that in the login settings somewhere). However, the second that Ubuntu finishes logging in, update manager and a handful of other programs call keyring for access, which subsequently requests a password from the user over and over again. It's quite frustrating.

Unfortunately, I don't know of a solution to this problem. It's a fundamentally hard problem when trying to keep security in mind, and I don't know if it's been answered.

---

### Post by empty_spaces on 2010-10-11
You are most likely being asked for the keyring to unlock Network Manager.
If that is the case, right click on the network manager applet in the panel, then go to Edit Connections => Wireless Tab => Select your network => Edit.
Enter user password if asked.
Check the boxes for "Connect Automatically" and "Available to all users"

This should stop network manager asking for a keyring password upon login.

---

### Post by bshosey on 2010-10-11
OK. On Auto log on I usually have to do the following.

Click on System/Preferences/Passwords and Encryption Keys

In that new window right click on Passwords then left click on Change Password. Set it to a blank password.

That will never prompt you for password.

---

### Post by petrasflorin on 2010-10-11
> **empty_spaces said:**
> You are most likely being asked for the keyring to unlock Network Manager.
If that is the case, right click on the network manager applet in the panel, then go to Edit Connections => Wireless Tab => Select your network => Edit.
Enter user password if asked.
Check the boxes for "Connect Automatically" and "Available to all users"

This should stop network manager asking for a keyring password upon login.

No wireless. I'm hooked up via a 100Mbps ethernet cable.

---

### Post by petrasflorin on 2010-10-11
> **bshosey said:**
> OK. On Auto log on I usually have to do the following.

Click on System/Preferences/Passwords and Encryption Keys

In that new window right click on Passwords then left click on Change Password. Set it to a blank password.

That will never prompt you for password.

That did the trick. SOLVED.

---

### Post by Spice Weasel on 2010-10-11
Er... Security?

---

### Post by bshosey on 2010-10-11
> **Spice Weasel said:**
> Er... Security?

You are correct. This does lower security quite a bit but. So does Auto log on. And I am sure he has evaluated the risks.

---

### Post by ean5533 on 2010-10-11
> **Spice Weasel said:**
> Er... Security?

It's a security/ease-of-use tradeoff that (I assume) he has willingly acknowledged and accepted.

---

### Post by petrasflorin on 2010-10-11
I don't have any important stuff on my computer anything other than... my e-mail which isn't important either... so...
Anyway I'm behind a router, and a firewall (an actual physical one) so that should be ok even if something important comes up.

---

### Post by Dyegov on 2010-10-11
> **empty_spaces said:**
> You are most likely being asked for the keyring to unlock Network Manager.
If that is the case, right click on the network manager applet in the panel, then go to Edit Connections => Wireless Tab => Select your network => Edit.
Enter user password if asked.
Check the boxes for "Connect Automatically" and "Available to all users"

This should stop network manager asking for a keyring password upon login.
This did it for me!!! Thanks!!!

---

