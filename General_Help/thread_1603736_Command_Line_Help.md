---
title: "Command Line Help"
date: 2010-10-23
forum: General Help
---

### Post by Alan James on 2010-10-23
I need some command line help. I am trying to write a script to copy a website from a Samba server to a web server.

I am currently using yafc to copy it, but I keep running in to errors when it reaches a directory with a space in the name. Adding “\” before the space usually solves the problem, but it is not this time.

Here is what I have so far.

```
yafc <<FTP
open ftp://USERNAME:PASSWORD@ftp.9ironproductions.com/domains/concept.9ironproductions.com/html/
put -r -n /mnt/server/9\ Iron\'s\ Server/9\ Iron/Web\ Marketing/9IronProductions.com/2011\ \(Concept\)/Code/*
FTP
```

What am I doing wrong?

---

### Post by gmargo on 2010-10-23
I'm not familiar with that tool but can't you just change to the source directory first, then do the ftp from the now-current directory?

---

### Post by Alan James on 2010-10-23
That works. It's a different approach than what I was thinking and it was a very good idea. Thanks for the help.

---

