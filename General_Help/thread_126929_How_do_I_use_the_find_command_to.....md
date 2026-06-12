---
title: "How do I use the find command to...."
date: 2006-02-07
forum: General Help
---

### Post by KevRus on 2006-02-07
work for files within folders within a folder?  It just looks for files in the one folder I enter and not within the folders in that folder....Can I change this?

---

### Post by Kadin2048 on 2006-02-07
[QUOTE=KevRus]work for files within folders within a folder?  It just looks for files in the one folder I enter and not within the folders in that folder....Can I change this?[/QUOTE]

Are you sure you're using find correctly?

It's not exactly straightforward (well, at least I think it isn't). If you want to find a file with a specific name, that's in a subdirectory of the working directory, you need to type:
$ find . -name "FileYouWantToFind"

Look at this site for examples of how to use it:
[http://www.athabascau.ca/html/depts/compserv/webunit/HOWTO/find.htm](http://www.athabascau.ca/html/depts/compserv/webunit/HOWTO/find.htm)

I just tried it, and it definitely seems to be searching down the directory hierarchies for me.

Frankly I don't use it much as a tool for finding files, though. I much prefer locate, as the syntax is simpler:
$ locate FileYouWantToFind

In order for locate to work, its database has to be kept up to date, but Ubuntu seems to do that automatically (so unless you've messed with the maintenance scripts you should be OK).

---

### Post by Snoopy2052 on 2006-02-08
I believe the updatedb command (that updates the locate database) is scheduled to run at 2am each morning. My computer is not often on at that time, and so I find it best to just run updatedb whenever I remember to do so.

---

### Post by taurus on 2006-02-08
[QUOTE=Snoopy2052]I believe the updatedb command (that updates the locate database) is scheduled to run at 2am each morning. My computer is not often on at that time, and so I find it best to just run updatedb whenever I remember to do so.[/QUOTE]
Then change it to a differenct time in /etc/crontab!!!

---

### Post by lamego on 2006-02-08
"man find" is what you need, anyway just to make your read shorter:
```
  find folder -maxdepth 1 -name "file"
```

---

### Post by dcstar on 2006-02-08
[QUOTE=taurus]Then change it to a differenct time in /etc/crontab!!![/QUOTE]
Actually, installing anacron is a far better way to do things for systems that are not up 24/7.

Anacron will run all "past" cron jobs on boot-up so things don't get missed.

---

