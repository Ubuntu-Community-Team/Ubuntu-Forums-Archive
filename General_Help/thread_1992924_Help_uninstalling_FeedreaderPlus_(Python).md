---
title: "Help uninstalling FeedreaderPlus (Python)"
date: 2012-06-01
forum: General Help
---

### Post by henrikgormsen on 2012-06-01
I wanted a RSS-reader for my desktop, so I took a suggestion from [Upubuntu]("http://www.upubuntu.com/2012/02/list-of-best-5-rss-feed-readers-for.html") about installing FeedReaderPlus. Now I desperately need help uninstalling it, since my CPU runs at 90-100 % as there are two new processes named python running.

I installed like this:

sudo add-apt-repository ppa:screenlets-dev/ppa
sudo apt-get update
sudo apt-get install feedreaderplus-screenlet
 
And then things are crap. Then i go 

sudo apt-get remove feedreaderplus-screenlet

The terminal does it's thing. The screenreader is still on my desktop, unafflicted. Even after reboot. The Terminal said that following was installed automatically and is no longer needed:

python-gnome2 libgnomeui-common libgfortran3 libart-2.0-2
  linux-headers-3.0.0-19-generic linux-headers-3.0.0-19 libbonoboui2-common
  libbonoboui2-0 python-pyorbit python-utidylib python-beautifulsoup
  libtidy-0.99-0 python-numpy python-tz libgnomecanvas2-0 libgnomeui-0
  python-feedparser libglade2-0 python-rsvg libgnomecanvas2-common libblas3gf
  screenlets liblapack3gf python-evolution screenlets-pack-basic

I go apt-get autoremove to remove it. I am then told two errors:
It could not open the lockfile (translation from danish, hope it makes sense) /var/lib/dpkg/lock - open (13: Access denied). And that it could not lock the administration folder (/var/lib/dpkg/) and then i am asked if i am root.

What is this? I don't like this. Have i installed something i cannot remove? What is root? Am i root? Do even want to be root? Does it come with some sort of capability or is more like an adjective?

Please, people of the interwebz, help me get out of this. And please note that i am not very savy with this OS/Ubuntu in general (Windows user until 4 months ago). I use the paste-and-pray approach to the terminal.

I run Ubuntu 11.10 Oneric Ocelot 32 bit.

---

### Post by drpjkurian on 2012-06-01
root is the user name or account that by default has access to all commands and files on a Linux or other Unix-like operating system. It is also referred to as the root account, root user and the superuser. please try the command

```
sudo apt-get autoremove
```
Enter your password, you may not see anything on the screen when you type the password. press enter

---

### Post by henrikgormsen on 2012-06-01
Ah, yes. Thank you. With the sudo command, it works. You're the best, internet person.

---

### Post by drpjkurian on 2012-06-02
You are most welcome.

---

