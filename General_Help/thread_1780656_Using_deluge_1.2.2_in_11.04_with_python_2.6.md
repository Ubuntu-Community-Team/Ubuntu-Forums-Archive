---
title: "Using deluge 1.2.2 in 11.04 with python 2.6"
date: 2011-06-12
forum: General Help
---

### Post by chrisbay90 on 2011-06-12
I am running a linux server with Ubuntu 10.04. It runs a deluge daemon. Deluge 1.2.2 with python 2.6. I have the client running in Ubuntu 11.04.

The problem is, some of the plugins require python 2.6 while I have 2.7. After some digging I have found that 11.04 supports and has installed python 2.6 /usr/bin/python2.6

I have edited all the deluge files
```
/usr/local/bin/deluge
/usr/local/bin/deluge-gtk
/usr/local/bin/deluge-console 
/usr/local/bin/deluge-web
/usr/local/bin/deluged
```

to read
```
#!/usr/bin/python2.6
```
in the first line.

Now the deluge client does not start. If i open it from a terminal i get.
```
$ deluge
Traceback (most recent call last):
  File "/usr/local/bin/deluge", line 5, in <module>
    from pkg_resources import load_entry_point
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 2675, in <module>
    parse_requirements(__requires__), Environment()
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 552, in resolve
    raise DistributionNotFound(req)
pkg_resources.DistributionNotFound: deluge==1.2.2

```

Could anyone help me get this working? P.S. it is the 'stats' plugin that i would like to get working.

---

### Post by chrisbay90 on 2011-06-13
bump

---

### Post by Cas07 on 2011-06-13
Why are you using deluge 1.2.2?? the latest version is 1.3.2 although 1.3.1 is currently in PPA for Lucid.

You cannot mix major version of Deluge (i.e. 1.2 and 1.3) client and servers

Also we have a support forum that will usually get you a quicker answer: [http://forum.deluge-torrent.org/viewforum.php?f=7](http://forum.deluge-torrent.org/viewforum.php?f=7)

---

### Post by chrisbay90 on 2011-06-14
> **Cas07 said:**
> Why are you using deluge 1.2.2?? the latest version is 1.3.2 although 1.3.1 is currently in PPA for Lucid.

You cannot mix major version of Deluge (i.e. 1.2 and 1.3) client and servers

Also we have a support forum that will usually get you a quicker answer: [http://forum.deluge-torrent.org/viewforum.php?f=7](http://forum.deluge-torrent.org/viewforum.php?f=7)

Thank you for taking the time to reply to my question, Cas7

My server is Ubuntu 10.04. The version in the 10.04 Ubuntu repo is  1.2.2, hence so are all my clients (one of wich is Ubuntu 11.04).

I will upgrade the server if there is a convincing reason to. However I  don't believe this will solve my problem as it is caused by the version  of python installed on the client.

Will head over there if this forum fails me.

Thank you.

---

### Post by Cas07 on 2011-06-14
It does not matter what version of Python is installed on the server or client so you do not need to edit Deluge. See these posts about plugins and python2.7:

[http://forum.deluge-torrent.org/viewtopic.php?f=7&t=31015&start=10#p153929](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=31015&start=10#p153929)
[http://forum.deluge-torrent.org/viewtopic.php?f=9&t=36527](http://forum.deluge-torrent.org/viewtopic.php?f=9&t=36527)

I just updated the [PPA]("https://launchpad.net/~deluge-team/+archive/ppa") with the latest version for Lucid.

---

