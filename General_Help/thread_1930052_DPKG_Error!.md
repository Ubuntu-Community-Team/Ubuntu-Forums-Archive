---
title: "DPKG Error!"
date: 2012-02-23
forum: General Help
---

### Post by AnotherCupOfCoffee on 2012-02-23
Hello everyone! I'm new to this forum and first off I'd like to apologize for making my first post a plee for help but I'm really stuck. Thanks in advance to anyone that'll try and help me!!!

Ever since my last update, I've never been able to update/install anything again.
Whenever I try to, I get this error message: 
-----------------------------------------------------------------------------------------
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd) : files list for package 'oxygen-icon-theme' : Input/
output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover.
------------------------------------------------------------------------------------------

What I've heard from [http://ubuntuforums.org/showthread.php?t=1232143](http://ubuntuforums.org/showthread.php?t=1232143) is that you can fix this by navigating to /var/lib/dpkg and delete the offending  part of the status file out. 

This person says you can just edit the status file, but for me "status" shows up as "Owner: Root , Access: Read & Write". I'm unable to edit this because I don't know how to change my permissions.

Can someone please tell me how to fix this error, or at least tell me the terminal commands that'll allow me to edit the file?

THANK-YOU SO MUCH!!!


p.s. I'm using 10.04 Lucid

---

### Post by Script Warlock on 2012-02-23
is this similat to yours? [http://ubuntuforums.org/showthread.php?t=1232143](http://ubuntuforums.org/showthread.php?t=1232143)

---

### Post by raja.genupula on 2012-02-23
> **AnotherCupOfCoffee said:**
> Hello everyone! I'm new to this forum and first off I'd like to apologize for making my first post a plee for help but I'm really stuck. Thanks in advance to anyone that'll try and help me!!!

Ever since my last update, I've never been able to update/install anything again.
Whenever I try to, I get this error message: 
-----------------------------------------------------------------------------------------
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd) : files list for package 'oxygen-icon-theme' : Input/
output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover.
------------------------------------------------------------------------------------------

What I've heard from [http://ubuntuforums.org/showthread.php?t=1232143](http://ubuntuforums.org/showthread.php?t=1232143) is that you can fix this by navigating to /var/lib/dpkg and delete the offending  part of the status file out. 

This person says you can just edit the status file, but for me "status" shows up as "Owner: Root , Access: Read & Write". I'm unable to edit this because I don't know how to change my permissions.

Can someone please tell me how to fix this error, or at least tell me the terminal commands that'll allow me to edit the file?

THANK-YOU SO MUCH!!!


p.s. I'm using 10.04 Lucid

```
sudo gedit <place path to your file here >
```

---

### Post by AnotherCupOfCoffee on 2012-02-23
Thanks for the reply, I'll try it out - and to the first guy, thanks for the suggestion but I already mentioned that thread in my post :P

---

### Post by AnotherCupOfCoffee on 2012-02-23
> **raja.genupula said:**
> ```
sudo gedit <place path to your file here >
```

Just did that, it let me edit and save. Following this guide: 
[http://ubuntuforums.org/showthread.php?t=1232143](http://ubuntuforums.org/showthread.php?t=1232143)

I'm supposed to do this next: Run: "sudo dpkg dpkg --configure -a"

When I entered that exact thing in terminal, I got this message:

------------------------------------------------------------
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
------------------------------------------------------------

---

### Post by AnotherCupOfCoffee on 2012-02-23
UPDATE: NEVERMIND! There was a typo: 

This is what you're supposed to type: dpkg --configure -a

It installed fine!!!

---

### Post by raja.genupula on 2012-02-23
Hi thats good news . So now what about your original issue ?  is it solved ? if so please mark the thread as solved from thread tools . :)

---

