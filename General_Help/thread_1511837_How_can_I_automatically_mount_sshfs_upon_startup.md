---
title: "How can I automatically mount sshfs upon startup"
date: 2010-06-17
forum: General Help
---

### Post by Isamtron on 2010-06-17
Hello,

I use this command to mount sshfs:

sshfs -o idmap=user user@ip:/home/user/public_html ~/Folder

Then I enter my password. I do this every time I start my computer!

How can I automate this process?

Please help. Thanks.

---

### Post by Tim Sharitt on 2010-06-17
You can add an entry to /etc/fstab to mount the sshfs on start up.

First you'll need to use a ssh-key for authentication instead of a password (which is just a good idea for ssh anyway). See [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) to get you going with that.

Open fstab for editing:
```
gksu gedit /etc/fstab
```

Then add a line for the sshfs mount:
```
sshfs#user@ip:/home/user/public_html mountpoint fuse options 0 0
```

Take a look at [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) for more info on fstab.

---

### Post by Isamtron on 2010-06-17
Thanks but does that mean I can not have a Key Password for my SSH keys in order to be able to automate the login?

---

### Post by Isamtron on 2010-06-17
There's another HUGE problem. How the drive will be mounted before the Internet connection is established?

Please help.

---

