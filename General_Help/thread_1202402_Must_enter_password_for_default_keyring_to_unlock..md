---
title: "Must enter password for default keyring to unlock...."
date: 2009-07-02
forum: General Help
---

### Post by ozark_hillbilly on 2009-07-02
Howdy,

After signing on I receive a prompt to "Enter password for default keyring to unlock."  I believe this is in conjunction with the Evolution mail program wanting to update my email files.

Where do I set a flag or preference to avoid having to do this?

Is this where I want to go:

 Howto: Get Network Manager to stop asking you for your keyring password (pam_keyring) ......      dated 2006 originally.....


Appreciate Ya,

Ed DeLauter

---

### Post by lovinglinux on 2009-07-02
Follow this:

> **mcduck said:**
> 
Changing/removing the keyring password is quite easy to do (no need to remove the current keyring or mess with user accounts):

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

[keyring password](http://www.google.com/search?q=keyring password+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) [ubuntuforums.org]  

> [color=#CC0000]**Note:**[/color] when you see [ubuntuforums.org] after a link on my posts it means that I am using Google site search feature. This feature allow us to get search results only from a specific site, in this case Ubuntu Forums, by adding the string *site:ubuntuforums.org* after the keywords. This method is much better than the forum search feature, since it gives you more precise results. I usually add this to my posts when a subject is very common and already answered several times.

---

### Post by ozark_hillbilly on 2009-07-04
Thank you.

Ed

---

