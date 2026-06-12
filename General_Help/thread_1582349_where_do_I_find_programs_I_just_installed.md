---
title: "where do I find programs I just installed?"
date: 2010-09-26
forum: General Help
---

### Post by warakawa on 2010-09-26
I downloaded a program called imwheel using Ubuntu software centre, after I downloaded them, where is the program located?

---

### Post by sendblink23 on 2010-09-26
did you test rebooting.. just incase maybe it would appear afterwards somewhere in applications or system > preferences or admin

---

### Post by 0N3 on 2010-09-26
What section or category was it under when you found it on Ubuntu Software center should be in that section of your applications list eg. Internet based applications in Ubuntu Software Centre comply under the Internet section of your applications menu...

---

### Post by Frogs Hair on 2010-09-26
File system >  Usr >  share file. Some of my applications don't show up on my installed software list because the are not officially supported and I find them in the share folder.

---

### Post by mick222 on 2010-09-26
Try alt+f2 and type imwheel

---

### Post by WorMzy on 2010-09-26
/etc/X11/Xsession.d/60imwheel_start-imwheel
/etc/X11/imwheel/imwheelrc
/etc/X11/imwheel/startup.conf
/usr/bin/imwheel
/usr/lib/imwheel/getmdt
/usr/lib/imwheel/mdetect
/usr/lib/imwheel/mdump
/usr/lib/imwheel/mice/a4tech
/usr/lib/imwheel/mice/default
/usr/lib/imwheel/mice/intellimouse
/usr/lib/imwheel/mice/mouseman+
/usr/lib/imwheel/mice/netmouse
/usr/lib/imwheel/see
/usr/lib/imwheel/setimps2
/usr/lib/imwheel/setmmplus
/usr/share/doc/imwheel/EMACS
/usr/share/doc/imwheel/NEWS.Debian.gz
/usr/share/doc/imwheel/README.Debian.gz
/usr/share/doc/imwheel/changelog.Debian.gz
/usr/share/doc/imwheel/changelog.gz
/usr/share/doc/imwheel/copyright
/usr/share/doc/imwheel/examples/61imwheel_load-xmodmap
/usr/share/man/man1/imwheel.1.gz


You run the application by either opening a terminal, or pressing Alt+F2, then running ```
imwheel
```

Find out more about how to use it by opening a terminal and running
```
man imwheel
```

---

### Post by jokes_finder on 2010-09-26
I think u can try typing in the terminal:
$ which [the program name]
i.e. Type the name of the program after the word 'which'
For example: I have downloaded the program mountmanager using software center and I don't know where it is, so:
$ which mountmanager
/usr/bin/mountmanager ( this is the output )
Tell me if it works..

---

### Post by 0N3 on 2010-09-26
try open a terminal and type imwheel --help or imwheel --config

---

### Post by warakawa on 2010-09-26
I typed in imwheel in terminal, I just get the following code in terminal

xiao@ubuntu:~$ imwheel
xiao@ubuntu:~$ INFO: imwheel started (pid=2529)

what am I doing wrong?


ps: how can I put the terminal writing in a code box in posts?

---

### Post by 0N3 on 2010-09-26
imwheel --config

or

imwheel --help for other commands

---

### Post by Lateralis on 2010-09-26
[imwheel man page]("http://pwet.fr/man/linux/commandes/imwheel").

It is a package to support non-standard buttons on new mice (so says aptitude).  As such, it probably won't have an Applications menu launcher.  It might have something under System -> Preferences but I wouldn't bet in it.  So as ON3 and the link above suggests, type the following into the command line

```

imwheel --config

```

Report back what you find.

---

### Post by warakawa on 2010-09-26
I got this. 

Is this the right program?

---

