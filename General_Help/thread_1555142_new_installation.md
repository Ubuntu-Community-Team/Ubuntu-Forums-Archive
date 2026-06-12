---
title: "new installation"
date: 2010-08-17
forum: General Help
---

### Post by enhu on 2010-08-17
i've just installed xubuntu but how can i run as a root to edit text files?

---

### Post by [Shawn] on 2010-08-17
Welcome to Ubuntu Forums enhu.
What I know is that root is disabled as a default for ubuntu.
What you need to do is open terminal;
Applications>Accessories>Terminal
And type the following..
```
sudo passwd root
```
Then enter your password (Won't show up for security reasons)
Then it will ask you for a new password. Type the password you 
Want to use to login as root. And then once your done type;
```
su
``` And then enter the password and you should have root access!
Hope this works!

---

### Post by Vaphell on 2010-08-17
[http://linux.about.com/od/xubuntu_doc/a/xubudg05t07.htm](http://linux.about.com/od/xubuntu_doc/a/xubudg05t07.htm)

i think mousepad is the default text editor
open the terminal window (whatever it's called in xubuntu) and run
```
gksudo mousepad
```

---

