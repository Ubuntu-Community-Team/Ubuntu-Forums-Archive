---
title: "Help with setting up proftpd and chroot"
date: 2011-11-16
forum: General Help
---

### Post by Siwon on 2011-11-16
Alright, I'm new here so hello to everyone.

I have installed Ubuntu Server 10.04 on vmware and right now I have installed:

php5
apache2
proftpd

I want to create multiple user accounts and let them access the www folder but not sure the best way to go about, however, I have tried:

Editing proftpd.conf to make sure the accounts are jailed to their home directory.
User1 Home: /home/user1
User1 www: /var/www right now but I'd like something for multiple users

Focusing on User1, I'm have successfully logged into the FTP and I can't move up to the root directory (good), but, when I did:

cd /home/user1
sudo ln -s /var/www www
chown -R user1 /var/www

I can see and access the www folder from command line, however, when I FTP to it, it says www directory doesn't exist.

Any help would be great!

---

