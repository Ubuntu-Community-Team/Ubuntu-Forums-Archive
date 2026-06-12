---
title: "fresh install no users installed what do I do?"
date: 2006-03-08
forum: General Help
---

### Post by brickbat on 2006-03-08
Hi, I installed a fresh system and it didn't ask me for a new user so now it has installed it without one.  Also (this may be related), my home directories are on their own partition which I kept from a previous install.

What do I do to;

1. Be able to log in
2. Use my previous home directory.

I need a step by step because my cli knowledge is poor. Please.

---

### Post by glug101 on 2006-03-08
Hmmm, there are no userids setup at all?  Well, Ubuntu doesn't have a root user by default.  So, if there are no general purpose users setup on the computer, then I am the bearer of bad news.

There is no way to setup a user without an existing user account.  You will need to reinstall Ubuntu and take care to remember username and passwd when you create a regular user. :(

Wish I had better news.

---

### Post by taurus on 2006-03-08
You can boot into single user mode (from GRUB menu) and add a user to your new system.  Make sure to include that user to group "adm" so you can run "sudo" later...

---

### Post by brickbat on 2006-03-09
ok.  I have added the user.  Now my problem is that even though I added hi mto the adm group, sudo doesnt work.  I think its because I have not specified a root password for use by sudo gksudo etc.  Can someone please tell me how to do that?

---

### Post by taurus on 2006-03-09
You don't need to specify root's password if you want to run sudo!!!  Just use your own password when it asks you for one.  Did you log out and back in again after you added that user to group adm in /etc/group?  If it still doesn't let you run "sudo apt-get update", then paste the contents of your /etc/group & /etc/sudoers here...

---

### Post by brickbat on 2006-03-10
It was too hard.  I just reinstalled and everything was fine.  Thanks anyway.

---

