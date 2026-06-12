---
title: "Instant files sync between server and client."
date: 2011-06-05
forum: General Help
---

### Post by maegras on 2011-06-05
Hi everyone, i didn't know where to post my question, so, if I'm in the wrong section, please, move this post to the right place :)

Ok, so, my problem is as follows:

I have an home server 24/7 running ubuntu 11.04 desktop. I would like to keep in instant sync this server with my laptop through internet. If i change any file in my laptop this file has to be modified also in my server.

Is there a simple way to do that? (no dropbox, no ubuntu-one. I have to keep in sync ~100GB of data)

---

### Post by papibe on 2011-06-05
There's several steps you need to take. Here's a list of the top of my mind:

[LIST]
[*]Get a static IP from your ISP.
[*]or, better setup a dynamic DNS service like DynDNS.
[*]Install OpenSSH in your server.
[*]Open your router for an ssh conection.
[*]Forward that connection to your server.
[*]Optional: for extra security create public keys for more secure connections.
[/LIST]
Now that you can access your server from almost anywhere, there are several alternatives depending of what you have running on your laptop. Is it Windows, Mac or Ubuntu?

Regards.

---

### Post by maegras on 2011-06-06
> **papibe said:**
> 

[LIST]
[*]Get a static IP from your ISP.
[*]or, better setup a dynamic DNS service like DynDNS.
[*]Install OpenSSH in your server.
[*]Open your router for an ssh conection.
[*]Forward that connection to your server.
[*]Optional: for extra security create public keys for more secure connections.
[/LIST]


All done...


My laptop is running Natty as well.

---

### Post by papibe on 2011-06-06
OK.

I would recommend using rsync over ssh. The first synchronization should be in your LAN, because 100GB is enough data to make it very difficult to transfer over the Internet (actually time consuming).

Later syncs won't have that problem because rsync only transfer changes. Here's an example:

```
$ rsync -aP -e ssh data/ yourserver.dyndns.org:data/
```
-a will go recursively into data/
-P is very important in my opinion. It implies --progress, which is a nice way of see what is going on, but most importantly it also implies --partial, which means it preserves incomplete data transfered. If by any reason the command is interrupted in the middle of its execution, next time you run it, it will resume much faster.

Hope it helps.

EDIT: I would recommend try this manually first a couple of times, and then design a way to automate the process.

---

### Post by maegras on 2011-06-06
> **papibe said:**
> 
```
$ rsync -aP -e ssh data/ yourserver.dyndns.org:data/
```-a will go recursively into data/
-P is very important in my opinion. It implies --progress, which is a nice way of see what is going on, but most importantly it also implies --partial, which means it preserves incomplete data transfered. If by any reason the command is interrupted in the middle of its execution, next time you run it, it will resume much faster.


Thanks for your help but i think this is not what I was searching for.

I know rsync, and I know also that it works only unidirectionally, isn't it?
Moreover I have to launch that command every time i want to sync my data.

What I was searching for was a program/command, (maybe a daemon?) that sync bidirectionally and that works in background, like a system service...

---

### Post by papibe on 2011-06-06
Well, yes. But you can automate your rsync scripts using crontab.

There's a tool called Unison (is on the Software Center). Maybe it could better fit your needs. This is a sort of [tutorial]("http://www.youtube.com/watch?v=fOxTh6um1p0") on youtube. It is for a Mac client, and a FreeNAS server, but it is essentially the same (it starts very basic so be patient).

Hope it helps.

---

### Post by erind on 2011-06-06
> **maegras said:**
> Thanks for your help but i think this is not what I was searching for.

I know rsync, and I know also that it works only unidirectionally, isn't it?
Moreover I have to launch that command every time i want to sync my data.

What I was searching for was a program/command, (maybe a daemon?) that sync bidirectionally and that works in background, like a system service...
Also take a look at** inotifywait** from **inotify-tools** package, combine it with* rsync* in a small script, and run it during the startup, (Preferences -> Startup Applications). Check also this:

[http://ubuntuforums.org/showthread.php?t=1753839](http://ubuntuforums.org/showthread.php?t=1753839)

---

### Post by maegras on 2011-06-08
Thanks to all of you for help... I'm going to try your various suggestions

Let you know :)

---

