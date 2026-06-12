---
title: "What's wrong with my update manager?"
date: 2010-10-17
forum: General Help
---

### Post by ivarn on 2010-10-17
Hey. For some weird reason my update manager can't download files from the getdeb.net server. [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps) and [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games).
Why is that? Is t here a bug in my system or are the server down or something?
Because it can download everything else perfectly.
Please help. thanx :)

---

### Post by Frogs Hair on 2010-10-17
I tried both links and they time out before connection , so I don't think it is the update manager. What packages are you trying to update ? Do you have these software sources enabled ?

---

### Post by holiday on 2010-10-17
Not even the root pings. 

$ ping [http://archive.getdeb.net/](http://archive.getdeb.net/)

$ ping: unknown host [http://archive.getdeb.net/](http://archive.getdeb.net/)

So either there's something wrong with that hostname or there's a DNS problem somewhere along the line. 

If the server was down, ping would come back with the IP address from the DNS and then report the failed connection. 

Are you sure of that hostname?

---

### Post by ivarn on 2010-10-17
> **Frogs Hair said:**
> I tried both links and they time out before connection , so I'm don't think it is the update manager.
You tried them in the web browser? no they won't work there.
These are the urls you are downloading apps and games from with update manager.

But i mean, if this is a server problem there would have been 100 threads about it now with people asking what the hell t his problem is. So I m afraid the problem is on my end.
I wish I knew how to fix this.

> **holiday said:**
> Not even the root pings. 
Are you sure of that hostname?

When I run sudo apt-get update, it says it can't download from those two getdeb addresses.
So what it basically means is, I can't update anything and if I run the update manager installation, I will lose important packages.

---

### Post by holiday on 2010-10-17
> **ivarn said:**
> You tried them in the web browser? no they won't work there.
These are the urls you are downloading apps and games from with update manager.

But i mean, if this is a server problem there would have been 100 threads about it now with people asking what the hell t his problem is. So I m afraid the problem is on my end.
I wish I knew how to fix this.



When I run sudo apt-get update, it says it can't download from those two getdeb addresses.
So what it basically means is, I can't update anything and if I run the update manager installation, I will lose important packages.

So check that hostname. My repositories are wide open and I don't have anything like yours in my sources.list. And they are not in my DNS chain. Are they in yours? 

Ping the URL. I'm betting it's a no-show. 

Try this

$ cd /etc/apt
$ cp sources.list sources.list-bak
$ sudo gedit sources.list

and remove the offending lines, save the file ... 

And then
$ sudo apt-get update

---

### Post by ivarn on 2010-10-17
If I do that I won't be able to update anything.
The actual url in the source.list is [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) (lucid getdeb apps and lucid getdeb games). It's the same source code that came with the installation of my apps and games on getdeb. The website is down so I guess it's just a server issue.

---

