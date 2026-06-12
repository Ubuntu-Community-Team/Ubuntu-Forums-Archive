---
title: "installing mysql header files"
date: 2010-09-24
forum: General Help
---

### Post by morgonhed on 2010-09-24
Hi,

I need to install the mysql client-headers on Ubuntu 10.04.

Here is what I have:

dpkg -l |grep mysqlclient

ii  libmysqlclient16                     5.1.41-3ubuntu12.3                              MySQL database client library

So I assume I need to install libmysqlclient16-dev.

But I can't:

sudo apt-get install libmysqlclient16-dev

The following packages have unmet dependencies:
  libmysqlclient16-dev: Depends: libmysqlclient-dev (>= 5.1.41-3ubuntu12) but it is not going to be installed

I have tried

sudo apt-get install libmysqlclient16-dev=5.1.41-3ubuntu12.3

but:

E: Version '5.1.41-3ubuntu12.3' for 'libmysqlclient16-dev' was not found

So how can I do this?

Many thanks!

---

### Post by morgonhed on 2010-09-24
As usual (at least for me) no support at all from this forum...

I don't know why that is, my theory is that Ubuntu people are friendly but unfortunately not that knowlegeable.

Ok - time for me to move to Debian.

And for the mysql header, this what I figured out in the end:

1) add "deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main" to /etc/apt/sources.list

2) sudo apt-get update

3) sudo apt-get install libmysqlclient16-dev=5.1.41-3ubuntu12.3

---

