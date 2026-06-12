---
title: "proftpd server help"
date: 2009-11-28
forum: General Help
---

### Post by jimfuture12345 on 2009-11-28
hi, 
sorry i need little push to do this part ,i am setting up proftpd server l don't know where is etc/shell (folder or file ) in second secure step .
 
2- Add this line in /etc/shells file (sudo gedit /etc/shells to open the file) :
Code:
/bin/false
 

will you explain me more ? 
ftp-shared folder ok done
and stop
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by cariboo on 2009-11-28
There is no such thing as /etc/shell, are you trying to setup the configuration file? Look in /etc/proftpd, that is where the configuration file is located.

---

### Post by bodhi.zazen on 2009-11-29
The file in question is /etc/shells

This is a list of shells (bash, csh, sh, zsh, etc) available on your system and if the shell you wish to use is listed in that file you can assign it with the various command line tools, such as adduser.

I assume the tutorial you are following is asking you to create a user with a shell /bin/false ;)

You can directly edit /etc/passwd if you prefer.

At any rate , to edit system files, use sudo or with graphical applications gksu

```
gksu gedt /etc/shells
```

---

