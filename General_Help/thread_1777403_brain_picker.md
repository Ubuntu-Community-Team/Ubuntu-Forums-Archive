---
title: "brain picker"
date: 2011-06-07
forum: General Help
---

### Post by RatScoot on 2011-06-07
]Just downloaded Ubuntu 11.04, about 4 days ago. I am a first time user, and 11.04 is the first version i have used. I have several issues that i hope someone knows the answer too.

#1. Any command i put into terminal for any reason always ends with "***E: The   package lists or status file could not be parsed or opened.***"

#2. I cannot install Skype. (i have downloaded from the skype site for linux, and also gone through terminal to download and install, and again it ends with the error mentioned above)

#3. UbuntuOne will not load.

#4. Ubuntu Software Center will not load any category (hence the reason I've been doing my best to learn how terminal works)

 Your help with any, or all, of these issues would be much appreciated
thank you,
                      RS

---

### Post by Lash009 on 2011-06-07
My gut tells me that some type of error occurred during installation of Ubuntu. I would try to boot into recovery mode (at Grub of course). Once that has loaded up try to run the "dpkg Repair broken packages" option. I really messed up something when upgrading from 10.10 to 11.04, and this fixed it up nicely. Just make sure you have an internet connection when doing this.
I'm also pretty new to Ubuntu, so could someone with a bit more experience confirm my line of thought?

---

### Post by jramshu on 2011-06-07
Are you using sudo?

```
sudo apt-get install -f
```

---

### Post by jerrrys on 2011-06-07
maybe

[http://ubuntuforums.org/showthread.php?p=10913650#post10913650](http://ubuntuforums.org/showthread.php?p=10913650#post10913650)

---

### Post by jramshu on 2011-06-07
Have you tried update manager? Does it give errors?
What error do you get when you type this in a terminal? Copy and paste the results of this.
```
sudo apt-get update
```
It could be a different problem than the one that is fixed by deleting the /apt/lists files.

---

