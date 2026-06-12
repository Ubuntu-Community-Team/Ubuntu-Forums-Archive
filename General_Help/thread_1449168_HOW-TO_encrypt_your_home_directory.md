---
title: "HOW-TO encrypt your home directory"
date: 2010-04-07
forum: General Help
---

### Post by balckNwhite on 2010-04-07
I have tried getting my home directory encrypted, following these two articles:

[http://www.linux-mag.com/cache/7568/1.html](http://www.linux-mag.com/cache/7568/1.html)
[https://wiki.ubuntu.com/EncryptedHomeFolder](https://wiki.ubuntu.com/EncryptedHomeFolder)

None of them worked for me. I would end up with a .Private dir with all encrypted, but I could not make it mount on the home dir. I'm not a Linux expert by any means, but I have been using Ubuntu for a few years now, so I know my way around. Then I clued in that you can create a new user with an encrypted home directory from the very beginning (this works only from 9.10). So I thought that I could:

[LIST=1]
[*]Rename my user
[*]Create a new user with an encrypted home dir
[*]move everything from the old user to the new one
[*]delete the old one
[/LIST]

Well, it worked. I'm sure the 'oficial' ways are much better in a million ways, but if they did not work for you, try this:

- Logout from the graphic interface

- Login with Alt+Ctl+F1 to get a terminal with the minimum open files.

- Create a new admin user:
   sudo adduser --ingroup admin deleteme

- Exit, log back in with 'deleteme'

- Get the old home out of the way:
  sudo mv /home/user /home/olduser

- Rename the old user
  sudo usermod --home /home/olduser --login olduser user

- Create the new encrypted user
  sudo adduser --home /home/user --ingroup admin --encrypt-home user

- Exit, then login with the new user and copy all the files
 sudo rsync -a /home/olduser /home/user

- Make these files your own
  cd /home
  sudo chown -R user user

- Logout, then login with the user, make sure everything works. After a couple of days without a problems, clean up:

sudo deluser --remove-all-files deleteme
sudo deluser --remove-all-files olduser


I hope it helps

Emiliano Conde
Lead Developer
[jBilling.com]("http://www.jbilling.com") - Open Source Billing

---

### Post by abuster on 2010-10-07
This might be useful:

```
$ ecryptfs-migrate-home --help

Usage:

/usr/bin/ecryptfs-migrate-home -u USER

 -u,--user       Migrate USER's home directory to an encrypted home directory

WARNING: Make a complete backup copy of the non-encrypted data to
another system or external media. This script is dangerous and, in
case of an error, could result in data lost, or lock you out of your
system!

This program must be executed by root.

```


Haven't tried yet, though..[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by rockachu2 on 2010-10-25
> **abuster said:**
> This might be useful:

```
$ ecryptfs-migrate-home --help

Usage:

/usr/bin/ecryptfs-migrate-home -u USER

 -u,--user       Migrate USER's home directory to an encrypted home directory

WARNING: Make a complete backup copy of the non-encrypted data to
another system or external media. This script is dangerous and, in
case of an error, could result in data lost, or lock you out of your
system!

This program must be executed by root.

```


Haven't tried yet, though..[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

AWESOME. This solved most of the problems I had with an encrypted home directory AND with multiple administrators.
thx \\:D/ thx \\:D/ thx \\:D/ thx \\:D/

---

### Post by welshmike on 2010-11-29
If I encrypt my home directory (on my old netbook running 10.04) how do I decrypt it please?
(When I installed 10.04 on this new notebook I had the choice of having an encrypted home folder and supplying a password for that encryption so that /home gets decrypted when I initially Log in and enter that password).

---

### Post by vmp on 2010-12-30
Thank you for the post balckNwhite, it was very helpful.

However a big big warning for sudo deluser --remove-all-files olduser: **It will delete any of the files belonging to the old user anywhere on the filesystem. This includes external disks etc not only the home directory**.

It would be more appropriate to use deluser --remove-home, because these are the only files that have been backed up.

To locate and change all the files belonging to the original user use this command:

find / -user olduser -exec chown newuser:newuser {} \;

---

### Post by welshmike on 2010-12-30
Well in the end I realised that the only data in my home directory that I did not want anyone else to be able to see into was in a directory of files in a Truecrypt encrypted file. 
I had started using Truecrypt for my secret stuff years ago. 
So I saved my home directory and any other stuff I needed to copy back after a re-install of Ubuntu.
I then did a re-install without selecting the option to encrypt my home directory, copied back my saved home directory and other stuff.
I'm now happy that I can, if disaster strikes, restore everything to a different PC from my regular off-site backups.

---

### Post by hyapadi on 2010-12-31
How to check if the current /home directory already encrypted or not?

---

### Post by welshmike on 2010-12-31
When my home directory was encrypted and I booted from a live Ubuntu CD or USB flash drive I could not see the contents of my encrypted home directory.

---

### Post by carmelosantana on 2011-02-04
This was quite helpful, thanks guys!

Just wondering, I used ecryptfs-migrate-home to encrypt my home DIR.

```
/usr/bin/ecryptfs-migrate-home -u USER
```

I'm now left with a folder /home/USER.w3KuZxku is this just a backup of my user DIR? I'd like to remove if possible.

Edit: Looks like it's a duplicate. However files that **rsync: recv_generator: failed to stat** were left in the duplicate, and are not present in my main USER DIR.

---

### Post by iconoclast hero on 2012-04-23
Ok, I executed this in precise 

```

sudo /usr/bin/ecryptfs-migrate-home --help
sudo: /usr/bin/ecryptfs-migrate-home: command not found

```

to get the ecryptfs if not selected at time of installation
```
**sudo apt-get install ecryptfs-utils**
```

---

### Post by oldos2er on 2012-04-23
Old thread closed.

---

