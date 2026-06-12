---
title: "Cannot Kill Process Even With Sudo"
date: 2009-07-08
forum: General Help
---

### Post by keemosabi on 2009-07-08
When I try to kill this process I am not able to and I get this result:

```
matthew@matthewServer:~$ sudo kill `cat /var/run/mysqld/mysqld.pid`
cat: /var/run/mysqld/mysqld.pid: Permission denied
Usage:
  kill pid ...              Send SIGTERM to every process listed.
  kill signal pid ...       Send a signal to every process listed.
  kill -s signal pid ...    Send a signal to every process listed.
  kill -l                   List all signal names.
  kill -L                   List all signal names in a nice table.
  kill -l signal            Convert between signal numbers and names.

```What can I do to fix this?  I entered my sudo password in before.

---

### Post by wojox on 2009-07-08
Try 

```
sudo /etc/init.d/mysql stop
```

---

### Post by keemosabi on 2009-07-08
> **wojox said:**
> Try 

```
sudo /etc/init.d/mysql stop
```
That worked perfectly.  Thank you for the help.

Is there a reason why the kill command did not work?

---

### Post by wojox on 2009-07-08
Because when you kill you have to know the PID aka Process ID

---

### Post by Slim Odds on 2009-07-08
By default, kill sends the SIGTERM signal (-15), which tells the process to terminate itself (which it might not want to do).

Add the -9 switch (which is the SIGKILL signal). That will really kill it.

```
kill -l
``` to list the signals

---

### Post by niteshifter on 2009-07-09
Hi,

Whoa there people. Killing with SIGKILL can be dangerous. Just try SIGTERM, and if it's refused do a bit of investigating:
```
ps aux
```
Show all that is running. Now, in this case - and to save a bunch of paging up and down, let's do this:
```
ps aux | grep mysqld
```
On my system that gave this:
```
root      5414  0.0  0.0   1772   520 ?        S    19:16   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     5456  0.0  0.7 127096 16336 ?        Sl   19:16   0:02 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      5457  0.0  0.0   1700   552 ?        S    19:16   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
dlk      13467  0.0  0.0   3008   776 pts/0    S+   22:46   0:00 grep mysqld

```
Whoops, that's owned by root and user mysql, I sense trouble so I do this:
```
sudo -i
```
to get myself a root shell and then do this:
```
pstree -p
```
From whose output I clipped this:
```
        &#9500;&#9472;multiload-apple(6788)
        &#9500;&#9472;mysqld_safe(5414)&#9472;&#9516;&#9472;logger(5457)
        &#9474;                   &#9492;&#9472;mysqld(5456)&#9472;&#9516;&#9472;{mysqld}(5459)
        &#9474;                                  &#9500;&#9472;{mysqld}(5460)
        &#9474;                                  &#9500;&#9472;{mysqld}(5461)
        &#9474;                                  &#9500;&#9472;{mysqld}(5462)
        &#9474;                                  &#9500;&#9472;{mysqld}(5464)
        &#9474;                                  &#9500;&#9472;{mysqld}(5465)
        &#9474;                                  &#9500;&#9472;{mysqld}(5466)
        &#9474;                                  &#9500;&#9472;{mysqld}(5467)
        &#9474;                                  &#9492;&#9472;{mysqld}(5470)
        &#9500;&#9472;netspeed_applet(6786)
```
Which one to SIGKILL? Better choose wisely or else. Or else being a corrupted database(s) and / or an unstable system.
At this point - and never mind I've been using MySQL since the 3.x days - this looks complex so my next stop is the MySQL documentation (perhaps [http://google.com/linux](http://google.com/linux) as well). Where wojox' sage advice - just tell it to stop - is found. 

It's tempting to assume any given program is just the 'one thing' - but that may or may not be the case. Dig around a bit first, and the pstree (part of the psmisc package) is a handy visual tool for this.

---

