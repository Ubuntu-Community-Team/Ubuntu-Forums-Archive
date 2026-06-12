---
title: "Unlock Keyring Problem"
date: 2009-10-16
forum: General Help
---

### Post by RSASKA on 2009-10-16
Hi,

I recently purchased Dell 1545 Inspiron with Ubuntu 9.04 distribution. 

1. Ever since I connected my machine to wireless router, every time I boot up the computer, it asks me for password to unlock keyring. This is the password I created when opened the laptop witih Ubuntu for the first time and I created password with upper-case and lower-case. Now, even a bigger problem, with this laptop, I am unable to see whether the cap-locks are on, so I have to type in my password twice, sometimes three or four times because I cannot tell when cap-locks are on or not.

2. I was told that the prompting for password to unlock keyring at bootup is a bug in Ubuntu 9.04. That is understandable. However, I have made several attempts to change this password to all numbers by going to System -> Administration -> Users and Groups, but the changes don't take effect and I am still prompted to type in the original password with uppercase and lowercase letters.

Please help me!

---

### Post by Anton32828 on 2009-10-16
I have the same problem with my HP Mini 110. I think the problem began when I used the "update" feature to downoad the latest updates in Ubuntu Netbook Remix 9.04.

---

### Post by Sven6210 on 2009-10-17
Well, I can not solve your problem concerning the upper- and lower case letters. But I can help you delete the password for the key ring.

1. Right mouse click on the wifi symbol in the panel
2. Choose 'Edit connections...'
3. Choose the tab 'Wireless'
4. Identify the name of the wireless network for which you want to reset the password and click it
5. Press the 'Delete' button
6. When being asked to allow the transaction I recommend only to 'Allow once'
7. Restart the computer an restart the deleted wireless connection

I hope that helps you

Sven

---

### Post by RSASKA on 2009-10-19
Tried it, still no luck :-(

Any other ideas?

---

### Post by mcduck on 2009-10-19
> **RSASKA said:**
> Hi,
2. I was told that the prompting for password to unlock keyring at bootup is a bug in Ubuntu 9.04. That is understandable. However, I have made several attempts to change this password to all numbers by going to System -> Administration -> Users and Groups, but the changes don't take effect and I am still prompted to type in the original password with uppercase and lowercase letters.

Please help me!
No, it's not a bug.

The keyring password and your login password are two different things.

The keyring will be unlocked automatically if both passwords are exactly the same, and you use login with password (instead of automatic/timed login).

If you change your login password you need to also change the keyring password, which is done in Applications/Accessories/Passwords and Encryption Keys.

Alternatively, when changing the keyring password you can leave the fields for new password empty to remove the keyring password completely. This means that all your passwords and encryption keys are stored as plain text instead of encrypted, but you won't have to worry about the keyring password any more.

---

