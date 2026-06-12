---
title: "Help, ubuntu logs me out immediately after i logged in"
date: 2011-03-15
forum: General Help
---

### Post by duckyq on 2011-03-15
hi all, i have encountered a rather strange error, i'm able to log in using the ubuntu account, in this account i created a user using
 
ubuntu@ubuntu:~$ sudo useradd -m duckyq -g root -d /home/duckyq 
-s /home/duckyq
 
After which i set the password 
 
ubuntu@ubuntu:~$ sudo passwd duckyq
 
after this i logged out and try logging in to this newly created account(duckyq) but immediately after entering the correct password and displaying the ubuntu's system info i was logged out.
 
i'm running this ubuntu as a vm in vmware workstation
 
i've attached a screen shot
 
any help will be greatly appreciated
 
**SOLVED: followed Krytarik's suggestion **

---

### Post by duckyq on 2011-03-15
up for help

---

### Post by Old *ix Geek on 2011-03-15
From your screenshot it looks like your home directory is trying to be executed as...something. In other words, you must have a command in a file that gets executed as/after you're logging in that's trying to execute your directory, and since that fails, you're getting logged out. Look at the line that says:

```
/home/duckyq: /home/duckyq: is a directory
```

So, with your other account, either create another new user and try logging in with that, or poke around in /home/duckyq and look at config files; I'd start with .bashrc and see if there's some reference in there to /home/duckyq as something to be executed, and then fix it.

---

### Post by duckyq on 2011-03-15
ok thx i'll look into it

---

### Post by Krytarik on 2011-03-15
You have set "/home/duckyq" as shell with the "-s" option.
> **duckyq said:**
> 
ubuntu@ubuntu:~$ sudo useradd -m duckyq -g root -d /home/duckyq  
**-s /home/duckyq**
 
[http://manpages.ubuntu.com/manpages/maverick/en/man8/useradd.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/useradd.8.html)

To set it to the default, this command should work:
```
sudo usermod duckyq -s
```
[http://manpages.ubuntu.com/manpages/maverick/en/man8/usermod.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/usermod.8.html)

---

