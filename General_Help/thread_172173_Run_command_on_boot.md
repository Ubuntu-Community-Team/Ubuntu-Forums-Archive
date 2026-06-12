---
title: "Run command on boot"
date: 2006-05-08
forum: General Help
---

### Post by jonnymccullagh on 2006-05-08
I need to automatically run the following command when my machine boots:
sudo route add default gw 192.168.1.1

This is due to a bug in kubuntu not holding on to the gateway address.

Should I enter this command into a text editor and save it as a file in the folder /etc/rc5.d 
I don't want to risk messing something up so some reassurance would be helpful,
thanks,
jonny

---

### Post by Eversmann on 2006-05-08
I think you can add a command like that in /etc/network/interfaces, but the easier way for me is add the command in a file and then go to preferences->sessions, then go to startup programs (i have it in spanish, i think that's what i says in english) and add an entry pointing to that file.

It should load at start.

---

### Post by cyracks on 2006-05-09
insert into file /etc/rc.local (before line "exit 0"):
route add default gw 192.168.1.1

if the file doesn't exists create "/etc/init.d/rc.local" and insert
####
#! /bin/sh

case "$1" in
    start)
        route add default gw 192.168.1.1
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
####

enter in terminal:
$sudo update-rc.d rc.local defaults 99 10

---

### Post by MJN on 2006-05-09
Technically speaking the use of rc.local is deprecated in Debian-based distros (which is why you likely needed to create it first) hence if you're really going to play by the rules you would be better of putting your script in /etc/init.d/ and calling it via a symlink (usind update-rc.d) from /etc/rcS.d. Everything in the latter is then parsed upon boot.

(Some background info in [http://www.debian.org/doc/FAQ/ch-customizing.en.html]("http://www.debian.org/doc/FAQ/ch-customizing.en.html") if it's of any to interest to anyone)

Mathew

---

### Post by cyracks on 2006-05-09
I don't know about breezy, but in dapper there is file /etc/rc.local which is automatically executed at the end of each multiuser runlevel.

---

### Post by MJN on 2006-05-09
It's quite possibly for backwards-compatibility reasons. As always there's many ways to skin a cat, some official, some not, some old, some new - you pays your money you takes your choice. However, it's always worthwhile going with the flow and falling in line with the official line as then you're less likely to come a cropper in the future (akin to side-stepping the modularised Apache approach taken by Debian - sure it's possible but you may regret it further down the line when something depends on, and blindly assumes, that very approach).

Mathew (cliche man ;))

---

