---
title: "Installing Programs"
date: 2011-06-15
forum: General Help
---

### Post by carmenat250 on 2011-06-15
On my Ubuntu installation, I have an administrator and user account.  I generally use the user account.

When I need to install a program under the user account, I am prompted to enter in the admin password to continue.  However, it seems that I can never install a program under the user account.

The most recent example of this was today when I trying to install a plugin for Google and I got the below message.  Are we not able to install apps under a user account?

Failed to run gdebi-gtk '--non-interactive' '/home/user/downloads/google-talkplugin_current_i386.deb' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program.  Contact the system administrator

---

### Post by ChipOManiac on 2011-06-15
From what I can see... you don't sem to have sudo permission... in order to be able to use sudo it has to be enabled by the administrator on your user account... check the permissions for the user in your user accounts program...

---

### Post by papibe on 2011-06-15
Usually works like this:

Your regular user is a normal user, but it belongs to the Administrators group. In order to do admin work like install programs, the system will prompt for your password (the same that you use to login), and then you'll increase your privileges (you'll became root).

What you describe (having 2 users), it's not a common situation. If your normal user is not part of the Administrator group, you won't be able to do upgrades or install software with it.

I would advice you for a simpler set up. Just add your normal user to the Administrator group, and every time you need an execute an admin task it would just require to get the same password.


Hope that helps.

---

### Post by carmenat250 on 2011-06-15
I see how to do this, but if I add the user account to the admin group, would that not make it an admin user and defeat the unwritten rule of never using a computer with the admin account?

---

### Post by papibe on 2011-06-15
The admin account is called root. You won't be running as root. You'll be 'you', and when you need to execute an admin task, your password will be required and that task will be executed as root. Just that task, the other windows and processes will stay as you.

I hope it's not getting too complicated.

Regards.

---

### Post by dFlyer on 2011-06-15
With ubuntu it's safe to have your original account as both user and admin, as sudo give you admin privilege. Once you close an admin program it also closes admin rights and make you a regular user. Second, third or more users that may use the machine don't need admin privileges unless you want to get them that right. Ubuntu keeps it simple, yet safe.

---

### Post by carmenat250 on 2011-06-15
Thanks.  I guess I took one to many steps of setting up an additional user account for a computer that is only used by me.

---

