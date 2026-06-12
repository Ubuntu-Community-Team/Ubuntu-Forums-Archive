---
title: "SVN: Problem doing checkout - connection"
date: 2010-03-04
forum: General Help
---

### Post by kabeza on 2010-03-04
Hi guys
I'm having trouble with SVN
I'm trying to do the first checkout to my project and I'm getting

Couldn't stablish a connection with the server. You can see the address and screenshot here

[IMG]http://i.imgur.com/6Y9T6.png[/IMG]

I'm behind a proxy, and I've configured the file
/home/me/.subversion/server
with this

```
http-proxy-host = 10.2.0.1
http-proxy-port = 6588

```

and then restarted PC, but problem still persists... Can any1 point me to some things I could try to solve this?

Thanks,

---

### Post by zine92 on 2010-03-04
Did you use a terminal instead. Try the terminal first.

type:
```
svn checkout http://[your-links-here.whatever]
```
this will create for you and automatically download from the svn. you may add the folder name after the svn
```
svn checkout http://[your-links-here.whatever][Intent file name]
```. Check your home folder for the downloaded files.
Hope that helps.

---

### Post by kabeza on 2010-03-05
Hi
I've got this output when doing checkout through terminal

> svn: /home/kike/.subversion/servers:6: Section header expected

EDIT: researching found that I had to put the config variables, under [global] section and not at file's head

---

