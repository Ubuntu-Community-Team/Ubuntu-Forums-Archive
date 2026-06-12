---
title: "Accessing an encrypted folder"
date: 2010-09-07
forum: General Help
---

### Post by Fabriciodsb on 2010-09-07
So, here is what happened:

I was using Ubuntu 10.04 with this partition disposal:

sda1 - 10gb - OS exclusive - mount point /
sda2 - 110gb - personal files and so on - mount point /home
swap


When I first installed the Ubuntu, I made it encrypt my /home directory. After a few months I decided to install Fedora (Formatting the Ubuntu partition to do so), and I forgot that /home was still following the encryption rules from Ubuntu, therefore, I couldn't see my files without encryption on Fedora (Even with root access).

When I installed Fedora, I tried to create it with an user called "fabricio", but he said that there was already a /home/fabricio (Due to the Ubuntu instalation, this directory is where all my files are, and they're encrypted), but I created as "fabricio" anyway because it said that it was possible without losing my files.

But, the new user "fabricio" on Fedora, didn't have root rights, and a lot of applications and configs couldn't be loaded because it was inside /home/fabricio where this user couldn't access.

So I decided to try with Ubuntu again, but I didn't create with the same username "fabricio" but "fabricio1". I still can see (If logged as root user) the folders at /home/fabricio

[img]http://i55.tinypic.com/slk7b8.png[/img]
The actual files are under .Private

What should I do to get my files back without encryption?
Should I try to make a new user called "fabricio" and see if it can access the /home/fabricio without problems? (I'm kinda afraid now to do this because I don't know if I'll lose my files or what)

PS: I guess I have the encryption keys or something like that. It's under the /home/fabricio/.Encryptfs

---

### Post by Fabriciodsb on 2010-09-07
I tried to create a user with the name "fabricio" but it couldn't read the folder either, just as happened when using Fedora.

---

### Post by flick on 2010-09-07
The linked article suggests you can use an Ubuntu livecd to access your files IF you know the encryption passphrase you used when you made the original encrypted partition.

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

---

### Post by gauravj on 2010-09-08
Hi

You should have passphrase , then there is no problem.
Otherwise you are out of luck.
for ecryptfs you can always do
sudo mount -t ecryptfs /.enrypted_data_dir /where_you_want_mount
this will require your passphrase with which the data got encrypted.
defaults are fine for the the various questions, if you have not marked yes for
encrypt file names while encrypting in fedora.
If there was no passphrase you can remember you encountered, then it may be your root password, you used with fedora.

---

### Post by Fabriciodsb on 2010-09-08
I keep getting this message:

> mount: wrong fs type, bad option, bad superblock on /home/.ecryptfs/fabricio/.ecryptfs,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I'm using this command:

sudo mount -t ecryptfs /home/fabricio/.Private /home/fabricio

---

