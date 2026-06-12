---
title: "LDAP and Keyring Authentication With Root Password"
date: 2012-06-14
forum: General Help
---

### Post by davzie on 2012-06-14
Hi Guys,

I have an Ubuntu image that we use here in our office. It's 12.04 and works lovely with LDAP authentication for all clients.

I installed the fresh image on a new machine, got a user to login using LDAP. The home directory was created from /etc/skel as it didn't already exist. Now whenever the user tries to save or retrieve passwords from the keychain it won't let the user access it with their password.

It does however work if I use the root password.

Why is this and can I make it user specific rather than having to use a root password? I'm saying root password, it could also be the password for the only local administrative account on the machine, I'm not sure which one, they use the same password at the moment whilst I'm testing things.

Hope you can help,

Dave.

---

### Post by Gluhm on 2012-08-26
I have exactly the same problem (Ubuntu 12.04 with an LDAP/NFS Server where the users can not save passwords (e.g. in Chromium) because they would need the admin-password to unlock the gnome-keyring.

I don't want to use a "blank" keyring-password for security reasons. gnome-keyring includes a pam module (mentioned in the softwarecenter) but the ldap users are not using a "private" keyring.

Is there any solution or workaround that solved the problem for you?

---

