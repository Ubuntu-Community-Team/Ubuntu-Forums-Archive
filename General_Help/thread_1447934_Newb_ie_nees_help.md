---
title: "Newb ie nees help"
date: 2010-04-06
forum: General Help
---

### Post by jdashbaugh on 2010-04-06
I am new to Linux and installed the sperating system without problem. I also downloaded and installed several of the software packages. Ni I get this message, "Check if you are using third party repositories. If so disable them, since they are a common source of problems. Furthermore run the following command in a Terminal: apt-get install -f"

When I run the command i get this:

john@john-desktop:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I know I've been up for nearly 24 hours and I'll be able think clearer after a little sleep ,,,,, but ............  i NEED HELP.... not yelling,,,,, it just hard for thos old dog to learn these new tricks.   

John

---

### Post by lisati on 2010-04-06
apt-get often requires "root privileges". Try prepending "sudo" to the apt-get command, e.g. ```
sudo apt-get -f
```

It will ask for your password, which won't show as you type - just type your normal password as usual.

For more information on sudo, look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

