---
title: "sudo Could not connect to database"
date: 2010-01-16
forum: General Help
---

### Post by jgenussr on 2010-01-16
I have a strange thing happening when I use the sudo command.  I'm getting "Could not connect to database"  every time I use the sudo command.  I don't have the slightest clue.  The sudo command works but it gives this phrase.
Can someone enlighten me?

---

### Post by n0dix on 2010-01-16
What database you want to connect?? What is the command line you use to connect.

---

### Post by nullmind on 2010-01-16
This does sound odd. Just out of curiousity, `which sudo` does give you `/usr/bin/sudo`, right?

@n0dix
I don't think he's trying to connect to a database, but getting that when he issues any sudo command.

---

### Post by jgenussr on 2010-01-16
Actually, I only have one database on the machine, MySQL and I'm not attempting to connect to a database.  This occurs each and every time I use the /usr/bin/sudo command.  This command is the only time I see the phrase

---

### Post by jamesisin on 2010-01-16
What happens if you try sudo --help or sudo -V (note: that's a capital V)?

---

### Post by jgenussr on 2010-01-16
Actually not much,
$ sudo -V
Sudo version 1.6.9p10
jgenus@bull:~>
$ sudo --help
sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

---

### Post by jamesisin on 2010-01-16
It may not seem like much but those are responses from sudo itself.  So we know that it's working on some level.

Sometimes solving a problem is eliminating what is not at issue.

---

### Post by jgenussr on 2010-01-16
The sudo command appears to be working but I have no idea why it would be attempting to connect to a database unless it is calling the sudoers fill a database or some shadow file associated with it where it can't access those files.

---

### Post by jamesisin on 2010-01-16
So if you run sudo mycommand, mycommand runs through sudo as expected (only you also get that db error)?

Annoying.

---

### Post by jgenussr on 2010-01-16
Yes, very

---

### Post by nullmind on 2010-01-25
Does the original poster have any update?

---

