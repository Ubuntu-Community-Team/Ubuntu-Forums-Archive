---
title: "write to system file on startup"
date: 2006-02-17
forum: General Help
---

### Post by tr333 on 2006-02-17
i need to run the following command at login, but i dont want to type the password every time the computer starts up.

```
sudo echo "-10" > /sys/devices/temperatures/limit_adjust
```

is it possible to run the command and not have to type the password?

---

### Post by healychan on 2006-02-17
It is not possible because the function of command "sudo" is prompt for your password.

What you can do is use a flag(check the man page) to change the "sudo" to accept the password from stdin. Then you can use "echo" to send your password to "sudo".

But I don't suggest you to do this unless no other solution because storing your password as plain text is not secure.

---

### Post by Mustard on 2006-02-17
How would you make it so that the line was run as root, thus avoiding the need for sudo?

---

### Post by dcstar on 2006-02-17
[QUOTE=tr333]i need to run the following command at login, but i dont want to type the password every time the computer starts up.

```
sudo echo "-10" > /sys/devices/temperatures/limit_adjust
```

is it possible to run the command and not have to type the password?[/QUOTE]
Why do you need to do this?

---

### Post by romdos on 2006-02-17
if you only need to do this at startup, I would call it from rc2.d 

first I would make it into a little shell script
we should put it in /usr/local/sbin because it is a script
to be run by root (sbin) and we created it ourselves for 
our system (local)

```

 romdos@freekbox:~$ sudo gedit /usr/local/sbin/littlescript

```

in gedit, type:

```

#!/bin/sh
sudo echo "-10" > /sys/devices/temperatures/limit_adjust

```

save it and make it executable by root:

```

romdos@freekbox:~$ sudo chmod 744 /usr/local/sbin/littlescript

```

then make a startup symlink in /etc/rc2.d to your new script

```

romdos@freekbox:~$ sudo ln -s /usr/local/sbin/littlescript /etc/rc2.d/S99littlescript]

```

it will be run as root everytime you boot up with no need for a password

---

### Post by tr333 on 2006-02-17
[QUOTE=dcstar]Why do you need to do this?[/QUOTE]
i need to lower the temperature-limit for the internal fan to start working.  otherwise, the powerbook gets too hot to use for more than 5-10 minutes at a time.

---

### Post by tr333 on 2006-02-17
[QUOTE=romdos]if you only need to do this at startup, I would call it from rc2.d 

first I would make it into a little shell script
we should put it in /usr/local/sbin because it is a script
to be run by root (sbin) and we created it ourselves for 
our system (local)

```

 romdos@freekbox:~$ sudo gedit /usr/local/sbin/littlescript

```

in gedit, type:

```

#!/bin/sh
sudo echo "-10" > /sys/devices/temperatures/limit_adjust

```

save it and make it executable by root:

```

romdos@freekbox:~$ sudo chmod 744 /usr/local/sbin/littlescript

```

then make a startup symlink in /etc/rc2.d to your new script

```

romdos@freekbox:~$ sudo ln -s /usr/local/sbin/littlescript /etc/rc2.d/S99littlescript]

```

it will be run as root everytime you boot up with no need for a password[/QUOTE]

i will try this as soon as i can get onto my powerbook.

---

### Post by tr333 on 2006-02-17
thanks!!  works perfectly.  \\:D/ 

just out of interest, what is rc2.d?

---

### Post by romdos on 2006-02-18
rc2.d is one of the directories that holds scripts (or links to them) that are run on every boot. 
the default runlevel in ubuntu is rc2, this can be changed in /etc/inittab
all files that start with an S are started in the order of the number that comes after
if the file starts with a K it will be killed in the order of the number following

for more info:
```

romdos@freekbox:~$ man init

```

---

### Post by tr333 on 2006-02-18
great!  thanks for your help on this issue.

---

