---
title: "Note able to change 'User Account' password!"
date: 2011-01-31
forum: General Help
---

### Post by s.a.patil on 2011-01-31
Respected Community Members, I searched on Google about this problem but in vain, so I'm posting this on forum. I'm using Ubuntu 10.4 version, and I keep my installation upto date. Recently I'm facing unique problem, when I go to System -> Administration -> Users and Groups to change my 'User Account' password I'm not able to do so. After opening 'Users and Groups' dialog box and entering "Current password" I opted for "Set password by hand" and entered new password and clicked "OK" but nothing happened the 'Time cursor' kept on rotating even after 10 minutes, after not able to do so with GUI I opened terminal and typed 'passwd' to change my user account password it showed me message "Changing password for sapatil" and asked me to enter "(current) UNIX password:" after entering valid current password it prompted me "Enter new UNIX password:" after entering one it asked for "Retype new UNIX password:" after doing so, I got this message "Bad: new password must be different than the old one" and again asked me to "Enter new UNIX password:" this kept on repeating, and my original password never changed. Another unique problem I'm facing is when I go to System -> Administration -> Users and Groups and try to change "Advanced Settings" it prompt for 'User Account' password, fine, when I enter the correct password it gives me following message "You are not allowed to modify the system configuration - An error occurred while checking for authorizations: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. You may report this as a bug." when I close this message and close the 'Users and Groups' dialog box and again re-open the same dialog box it opens without asking any password and error message. Earlier this task was breeze, but not any more. Please help.  Thanks a lot in advance.

---

### Post by s.a.patil on 2011-01-31
Respected Members, just few updates to my post.
The password entered in GUI and Terminal were same and different than my existing password so no mistake on my part.
I tried "sudo dpkg-reconfigure -plow libpam-runtime" and got following three options
[*] Unix authentication
[*] GNOME Keyring Daemon - Login keyring management
[*] ConsoleKit Session Management
I tweaked around by enabling and disabling but no use
My existing password is 34 character and contain valid permitted character my new password is 36 character containing valid permitted characters
Reducing characters did not help.
As always I really appreciate any help from kind members.

---

### Post by s.a.patil on 2011-01-31
I reinstalled 'sudo' and its additional package but of no use, please any one with any solution.

---

### Post by matt_symes on 2011-01-31
Hi

Have you tried dropping to a root shell at the grub menu and changing it from there ? From the root shell...

```
passwd Your_username
```

Kind regards

---

### Post by s.a.patil on 2011-01-31
Respected matt_symes, thanks a lot for the idea, will try it. Mean while I post this thread as an update.
Respected community members, at last I solved my problem (off-course by accidentally). Please note that this is really ridicules way of solving problem and hence is not recommended, but worked for me. Here is steps I took to solve my problem.
I have 2 account on my laptop one is Admin 'User Account' and another is Ordinary 'User Account' with no privilege except surfing net. When I tried to change the Ordinary 'User Account' password from Admin 'User Account' I ended up successful, so it immediately struck my mind why not the other way.
Step 1. I logged into Ordinary 'User Account' using it's password and user name.
Step 2. I went to System -> Administration -> Users and Groups and selected my Admin 'User Account'
Step 3. I clicked Password button, now my system asked me the Admin 'User Account' password which I typed.
Step 4. A dialog box appeared which prompted to enter new password, I did so and re-typed my new password.
Step 5. I logged out of Ordinary 'User Account' and logged in to Admin 'User Account' with new password, that's it.
But I request learned and experienced community members to enlighten newbies like me what went wrong and what fixed it. But please note that I'm still not able to do the same task in my Admin 'User Account'.
Also as end note I just wanted to know the maximum character limit Ubuntu accept as password, and does it varies with disto to distro. Thanks a lot in advance.

---

