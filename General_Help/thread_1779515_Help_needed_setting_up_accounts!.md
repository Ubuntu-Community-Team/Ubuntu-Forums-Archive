---
title: "Help needed setting up accounts!"
date: 2011-06-10
forum: General Help
---

### Post by ItsAsh on 2011-06-10
Hi Community.

I have recently got a new Ubuntu 11.04 Dedicated server, and I'm new to administration, I know the basic commands, and the manuals etc.

However I have created a new user called ash.

1. I want ash to have root privileges (via sudo).
2. I then wish to disable the root user.

However, I did the following:

```
$ useradd -m ash
$ passwd ash
$ usermod -G admin ash
$ groups ash
```

Then i log into ash using ssh, and use sudo, enter the password for ash when prompted. I don't have ANY privileges what so ever.

Please could someone advise me through this process?

Thanks!

---

### Post by TeoBigusGeekus on 2011-06-10
You also need to add the user to the sudoers file with visudo.
From a user account that has root priviledges
```
sudo visudo
```
If you're not comfortable with vi, then use nano
```
sudo EDITOR=nano visudo
```
Then add this line at the end of the file
```
ash ALL=(ALL) ALL
```

---

### Post by ruffEdgz on 2011-06-10
> **TeoBigusGeekus said:**
> You also need to add the user to the sudoers file with visudo.
From a user account that has root priviledges
```
sudo visudo
```
If you're not comfortable with vi, then use nano
```
sudo EDITOR=nano visudo
```
Then add this line at the end of the file
```
ash ALL=(ALL) ALL
```
This works or if you do the 'sudo visudo' command and find the following line
```

%sudo ALL=(ALL) ALL

```
make sure its uncommented so you can control who has sudo through the /etc/group file. You should see the group 'sudo' when you do the following command:
```
grep sudo /etc/group
```

Cheers!

---

### Post by ItsAsh on 2011-06-10
Thank you both for your responses, much appreciated..

and are you seriously telling me that % is a bloody comment?

excuse me while i punch the wall.

---

### Post by ItsAsh on 2011-06-10
Hi Guys,

I have uncommented the %admin and %sudo within visudo.

However, I still need to add the user to the sudouser list?

I was hoping i could add a group called "sudoallow" and everyone in that group gets access to sudo?

---

