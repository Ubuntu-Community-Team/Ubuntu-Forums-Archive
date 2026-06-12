---
title: "Torrent client with cli"
date: 2010-08-22
forum: General Help
---

### Post by Kungen7 on 2010-08-22
Ive looked a bit around but i still cant get the picture.

What clients support cli?

Is it possible using transmissioncli locally on a ubuntu system, not a server? In that case, how?


Thanks,
Kungen

---

### Post by dagdeniz on 2010-08-22
Using the client locally? I couldn't get it well. Anyway, may this help you?
[http://linux.die.net/man/1/transmissioncli](http://linux.die.net/man/1/transmissioncli)

By the way afaik all of the torrent applications in linux have a cli.

---

### Post by Kungen7 on 2010-08-22
Hm i see.
When i say locally i mean not remotely on a server for example, but on my computer.

And with cli i mean like rtorrent or this screenshot [http://github.com/fagga/transmission-remote-cli](http://github.com/fagga/transmission-remote-cli).

I have tried rtorrent, but would like to get the transmission cli to work.

---

### Post by WorMzy on 2010-08-22
Deluge has a decent CLI. Start the daemon with
```
deluged
```

Then start the CLI client with

```
deluge -u console
```

Type "help" to get a list of commands, and "help <command>" to get info about a specific command.

```
connect
```

Should automatically connect you to the deluge daemon.

---

### Post by Kungen7 on 2010-08-28
Thanks Wormzy, works very well.

I came over this [http://github.com/fagga/transmission-remote-cli](http://github.com/fagga/transmission-remote-cli).
Faggas transmission-remote-cli curses interface. Looks fantastic!

Can anyone help me install this?

**EDIT: **Sorry for being so slow answering, but im the army so they tend to keep my busy in the weekdays.

---

### Post by WorMzy on 2010-08-28
There's no need to install it, just download the python script ([Transmission Remote CLI]("http://github.com/fagga/transmission-remote-cli/tarball/master")), extract it from the tarball, and run it from a terminal with
```
python /path/to/transmission-remote-cli.py
```

---

### Post by Kungen7 on 2010-08-28
I thought i had tried this, but when i do now i get

```
401: Unauthorized
Unauthorized User
```

Does the same with sudo and i have made it executable.

---

### Post by Lars Noodén on 2010-08-28
btpd is another option, if you know your way around shell.

---

### Post by WorMzy on 2010-08-28
Have you read the connection info on the link you posted?

> Authentication and host/port can be set via command line with one of these patterns:
$ transmission-remote-cli.py -c homeserver
$ transmission-remote-cli.py -c homeserver:1234
$ transmission-remote-cli.py -c johndoe:secretbirthday@homeserver
$ transmission-remote-cli.py -c johndoe:secretbirthday@homeserver:1234

You can write this (and other) stuff into a configuration file:
$ transmission-remote-cli.py -c johndoe:secretbirthday@homeserver:1234 --create-config

I've never used Transmission, so I have no idea how it works, but are you sure you've set it up correctly?

That stuff I quoted suggests that you don't need to call the script with python, but I get a permission error if I call it like the examples. :confused:

---

### Post by Kungen7 on 2010-09-04
Thanks WorMzy you got me on the right track, but im still stuck though.

The past problems are gone, now its the connection part i dont get. I try to connect to localhost:9091, but get connection refused. Same with running it as root.

Looks to me like a simple problem. Any one care to give me a lesson?


Again, sorry for slow answering.

---

### Post by Kungen7 on 2010-09-04
Jepp, very simple.

Just ran the transmission-daemon first.

Thanks for the help guys ;)

---

### Post by WorMzy on 2010-09-04
Ah, that makes sense. Without the daemon running, you'd have nothing to connect to.

Well, glad you got it sorted out. :)

---

