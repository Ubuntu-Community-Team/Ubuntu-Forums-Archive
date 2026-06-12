---
title: "ubuntu server 9.04"
date: 2010-02-06
forum: General Help
---

### Post by ashvindora on 2010-02-06
i'm new in ubuntu server..just installed it and i was prompted to enter my username and password..but theni got this prompt:

administrator@ubuntuserver:~$

please let me know what to type, dont know what to do..

thanks
ashvin

---

### Post by julianb on 2010-02-06
sounds like your username is "administrator" and you gave your machine the name, "ubuntuserver".

If you want to switch to a graphical system instead of a "command line only" system you may do this

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

(enter your password when asked. installing the desktop will take a while.)

A lot of server-related tasks are easier with the command line, but install the ubuntu desktop if that's what you really want.

---

### Post by ashvindora on 2010-02-06
Still not working.
after typing my username and password, i type 
sudo apt-get update but i got this error:
failed to fetch...some file (a lot)

and i still not understand why u mentioned ubuntu desktop when i'm using ubuntu server!!!

---

### Post by rnerwein on 2010-02-06
hi
because a server is just a "server" and no play ground. why haven't you install a desktop version. you can use this version ( using apt-get some packets if you need them) as a server too.
ciao

---

### Post by Iowan on 2010-02-06
What file did it "fail to fetch"? Most folks start with a desktop version, but most (Ubuntu) servers don't come with one.  You're certainly not obligated to install/use one - in fact, you may discover the CLI (command line interface) is more efficient. There are some help threads/posts available if you need them.

---

### Post by gmargo on 2010-02-07
> **ashvindora said:**
> 
administrator@ubuntuserver:~$

please let me know what to type, dont know what to do.


[LIST]
[*] type "man man" (without quotes) and learn about the documentation system.
[*] type "ls" to see what's in your directory.
[*] type "ls -a" to see what's in your directory, including hidden files.
[*] type "ls -l /" to see the root directory, long format.
[*] type "man ls" to see other options that the "ls" command supports.
[*] type "ls /bin" to see a whole bunch of installed programs.
[*] type "ls /usr/bin" to see even more.
[/LIST]
 explore and learn and have fun.

[http://www.google.com/search?q=unix+beginners+tutorials](http://www.google.com/search?q=unix+beginners+tutorials)

Kind of funny that you need a desktop environment installed to view the command-line tutorials.

---

