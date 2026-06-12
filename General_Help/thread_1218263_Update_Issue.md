---
title: "Update Issue"
date: 2009-07-20
forum: General Help
---

### Post by 696f6e6963 on 2009-07-20
When I run apt-get update as root I get the following error that tells me to run apt-get update to correct the problems - yet that is the command that is giving me the error...

> root@local: apt-get update
...
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 1341B in 0s (1981B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 80E7349A06ED541C
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B
W: You may want to run apt-get update to correct these problems


How do I fix this?

Note: I am running ubuntu server so please don't tell me to use the GUI. :)

---

### Post by keithweddell on 2009-07-20
Yes it's not a very helpful error message.  The reason you are getting the errors is that you don't have the gpg keys for those repositories on your system.  [This link]("https://help.launchpad.net/Packaging/PPA") should get you started on the PPA archive - scroll down to the section "Adding a PPA's keys to your system".  The process should be similar for the ftp archive.  The debian.org site might have some further help.

Keith

---

### Post by grayn0de on 2009-07-20
[FONT=Arial][SIZE=2]try something like:

```
gksudo -- wget -O - "[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xFC66403D8670A035")[80E7349A06ED541C]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xFC66403D8670A035")" | apt-key add - 
```then

```
gksudo -- wget -O - "[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xFC66403D8670A035")[9AA38DCD55BE302B]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xFC66403D8670A035")" | apt-key add - 
```and finally...

```
sudo apt-get update && sudo apt-get upgrade
```Not sure exactly if it will work, though. I've been having bad luck accessing the keyserver, lately.[/SIZE][/FONT][SIZE=2] :?
[/SIZE]

---

### Post by 696f6e6963 on 2009-07-20
Thanks guys. grayn0de, your solution worked well.

---

