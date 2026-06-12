---
title: "Will I be able to use encrypted /home partition if I upgrade"
date: 2012-03-05
forum: General Help
---

### Post by x1a4 on 2012-03-05
Hi,

On a Xubuntu 11.10 box with an encrypted /home partition.  Will it be possible to access and use the files in /home after upgrading to 12.04?  I opted to encrypt when installing Oneiric but don't remember if I set a password or not.  I don't see one in my password notebook.  I'm thinking of upgrading by doing a clean install.  

Thank you.

---

### Post by clegends on 2012-03-27
In a similar boat myself. In the past I've just backed everything up, wiped, and reinstalled, then restored it. Long process. Basically, your user password (which should also be your root password) is your encryption password. From memory, you should be able to use it to remount your 'home partition after reinstall, just make sure you don't wipe that partition in the reinstall, and BACK IT UP...

You'll have to do some more research, because my facts are sketchy, but look up Ecryptfs (which is used for encryption), and see how to mount encrypted partitions. The latest version (I believe) makes this very easy. You would then choose the /home partition to install your home directory on in the install (not formatting it!), and remount your old ecryptfs folder (whatever it is) after reinstall, copying your data across. Good luck!

*edit: Actually, it seems really easy. In recent versions of Ubuntu (from 11.10 I think), ecryptfs, which is used for encryption, has a nifty little tool called ecryptfs-recover-private. When you run that command, you'll actually be asked which .Private folder you wish to decrypt, which is then mounted in /tmp. That folder, by the way, is where all your data is stored, encrypted. So in effect, it's not actually the entire partition, just a folder within it. You will either need your unwrapped passphrase, or simply your login password to decrypt it. Good luck!

---

### Post by x1a4 on 2012-03-28
Thank you for your reply.  It definitely helped.

---

