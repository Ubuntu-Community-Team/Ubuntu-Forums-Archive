---
title: "Open Port"
date: 2006-05-11
forum: General Help
---

### Post by cssutto on 2006-05-11
A shields up scan shows my port 25 as open.

What is the command line to close a port?

CSSJR

---

### Post by nocturn on 2006-05-11
[QUOTE=cssutto]A shields up scan shows my port 25 as open.

What is the command line to close a port?

CSSJR[/QUOTE]

That is smtp/E-mail...  Did you configure a mailserver to run publicly?
You close the port either by firewalling it or by disabling the service that uses it. 

25 should not be open on a default install though.

---

### Post by cgjones on 2006-05-11
Is the computer connected directly to the Internet, or are you behind a router/firewall?

---

### Post by cssutto on 2006-05-11
I am not behind a firewall.

I have been paranoid about that when using W2K, but I understnd the conventional widom to be that is a waste with linux.

I know it is an email port.

But the question is how do I close it from a command line.

I know how to do it with a firewall.

CSSJR

---

### Post by cssutto on 2006-05-11
I should have mentioned that I am running Evolution, that the port was closed for a couple of weeks and only just now showed up as open.

I ran chkrootkit and rkroot and both showed up clean.

So the question is:  What opened it and is there something other than a rootkit to see whether I have been hacked.

I have recently had some problems with Evolution and that could be what caused it, but I need to find out.

CSSJR

---

### Post by nanotube on 2006-05-11
first, run command
```
sudo netstat -plant
```
to see what process is listening on that port. chances are, it will be something like sendmail or whatnot.
then, to kill it, best way is to use the startup/shutdown script for it that is located in /etc/init.d. then, you want to update your list of startup services to remove that, using update-rc.d command.

but post your output of that netstat command i gave you, so we can see what service you are running, and i can then give you exact commands to stop it and to remove it from startup, if you want.

---

### Post by Ramses de Norre on 2006-05-11
Virus scans are not needed on linux, but a firewall is pretty handy though!
I'd use firestarter (in the repos).

---

### Post by cssutto on 2006-05-11
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
tcp        0      0 127.0.0.1:32769         0.0.0.0:*               LISTEN     7898/hpiod
tcp        0      0 127.0.0.1:32770         0.0.0.0:*               LISTEN     7954/python
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     7874/cupsd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     8136/master
tcp        0      0 127.0.0.1:631           127.0.0.1:39939         ESTABLISHED7874/cupsd
tcp        0      0 127.0.0.1:631           127.0.0.1:39180         ESTABLISHED7874/cupsd
tcp        0      0 127.0.0.1:32769         127.0.0.1:45538         ESTABLISHED7898/hpiod
tcp        0      0 127.0.0.1:45538         127.0.0.1:32769         ESTABLISHED7954/python
tcp        0      0 127.0.0.1:39939         127.0.0.1:631           ESTABLISHED8502/gnome-cups-ico
tcp        0      0 127.0.0.1:39180         127.0.0.1:631           ESTABLISHED8646/firefox-bin
tcp        0      0 127.0.0.1:39178         127.0.0.1:631           TIME_WAIT  -
tcp        0      0 127.0.0.1:39179         127.0.0.1:631           TIME_WAIT  -

---

### Post by jazzmuzik on 2006-05-11
[QUOTE=cssutto]I am not behind a firewall.

I have been paranoid about that when using W2K, but I understnd the conventional widom to be that is a waste with linux.

I know it is an email port.

But the question is how do I close it from a command line.

I know how to do it with a firewall.

CSSJR[/QUOTE]

Your experience shows why the conventional wisdom is wrong on using a firewall. If Firestarter had been running you wouldn't have an exposed port now.

If anybody can explain why people are encouraged not to use a firewall in Ubuntu, I'd like to hear it.

---

### Post by kabus on 2006-05-11
[QUOTE=jazzmuzik]Your experience shows why the conventional wisdom is wrong on using a firewall. If Firestarter had been running you wouldn't have an exposed port now.

If anybody can explain why people are encouraged not to use a firewall in Ubuntu, I'd like to hear it.[/QUOTE]

Why would you need a firewall to prevent an open port? 
Either you want that port open or you don't, in which case you'd shut down the service in question. Or am I missing something here?

---

### Post by Al3xanR0 on 2006-05-11
[QUOTE=Ramses de Norre]Virus scans are not needed on linux, but a firewall is pretty handy though!
I'd use firestarter (in the repos).[/QUOTE]

Are you sure about that? I am behind a firewall and clamav found two worms. The worms did not impact my system that I can tell and I have not had an occurence since then, but a virus scan found them.

---

### Post by Ramses de Norre on 2006-05-11
It will find files maybe, files that are virusses when executed on a windows install. But they wont do no harm on Linux. If they would do: you can say you've found the first spreaded Linux virus ;)

---

### Post by cssutto on 2006-05-11
I have to leave the office for a couple of hours, so I will see your replies later today.

But even with a firewall, if something from within wants to open a port, it will.

If it wants to leave it open, it will.  I found that out with all sorts of protection on W2K.

So the way to stay closed is to regularly get ports checked by either shields up or one of the other services available.

And to not allow crap on your machine that opens ports.

Running W2K, the firewall runs you nuts constantly asking whether this should be or that should be and many times it is for some MS service that you can not research to find out what it is doing, such as the services, so you will end up eventually giving a permission you should not have.

I hope to get away from that in linux.

And all of that crap slows down the machine but worse, it constantly interrupts your work asking for a permission to do this or do that.

So If I can get away without it, that is one oif the several reasons I came over to linux.

CSSJR

---

### Post by cgjones on 2006-05-11
In Linux, if you close a port, it stays closed. Unless something runs as root that needs to open a port, but I haven't seen too many programs that do this. And you need to be careful what you run as root anyways, just like in Windows. The firewall in Linux is pretty much transparent, once you have the correct rules set up. Doing this manually can get kind of tricky, so you might want to use a front-end program such as Firestarter.

---

### Post by jazzmuzik on 2006-05-11
Firestarter won't bother you a bit once installed. I'm astounded by the reasons for not using a firewall. If a port gets inadvertantly opened, the firewall will keep if from being opened to the outside world. And just because all ports are closed may not mean you are totally protected. A firewall practically IS Linux since Linux is a networking OS.

---

### Post by nanotube on 2006-05-11
[QUOTE=cssutto]Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
tcp        0      0 127.0.0.1:32769         0.0.0.0:*               LISTEN     7898/hpiod
tcp        0      0 127.0.0.1:32770         0.0.0.0:*               LISTEN     7954/python
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     7874/cupsd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     8136/master
tcp        0      0 127.0.0.1:631           127.0.0.1:39939         ESTABLISHED7874/cupsd
tcp        0      0 127.0.0.1:631           127.0.0.1:39180         ESTABLISHED7874/cupsd
tcp        0      0 127.0.0.1:32769         127.0.0.1:45538         ESTABLISHED7898/hpiod
tcp        0      0 127.0.0.1:45538         127.0.0.1:32769         ESTABLISHED7954/python
tcp        0      0 127.0.0.1:39939         127.0.0.1:631           ESTABLISHED8502/gnome-cups-ico
tcp        0      0 127.0.0.1:39180         127.0.0.1:631           ESTABLISHED8646/firefox-bin
tcp        0      0 127.0.0.1:39178         127.0.0.1:631           TIME_WAIT  -
tcp        0      0 127.0.0.1:39179         127.0.0.1:631           TIME_WAIT  -[/QUOTE]

hmm, well that shows some weird "master" thing sitting on 25. what's that? have you installed anything like that?

well, the pid is 8136 - try killing it with "sudo kill -9 8136"
but i don't really know what it is...

---

### Post by Ramses de Norre on 2006-05-11
```
ps -aef|grep 8136
```should show two processes, one for grep searching and the other is the process using port 25.

---

### Post by jazzmuzik on 2006-05-11
I suspect port 25 isn't open then if the ip is 0.0.0.0. I show port 25 being available on my system, but it's not open to the outside world:

```

netstat -alnp --protocol=inet|cut -c-6,21-94|tail +2|grep -v ESTABLISHED|grep -v CLOSE_WAIT

tcp   0.0.0.0:25              0.0.0.0:*               LISTEN     -

```

---

### Post by cssutto on 2006-05-11
Ramses:

This is what that command returned.

Of course, I have no idea what it means.

1000     15165 15142  0 17:27 pts/1    00:00:00 grep 8136

CSSJR

---

### Post by cssutto on 2006-05-11
hmm, well that shows some weird "master" thing sitting on 25. what's that? have you installed anything like that?


The only think I have installed within the last day or two is Real Player, which I never trusted and would not have on W2K. 

CSSJR

---

### Post by kabus on 2006-05-11
[QUOTE=nanotube]hmm, well that shows some weird "master" thing sitting on 25. [/QUOTE]

I suspect it's postfix. At least that's how postfix looks on my system.

---

### Post by cssutto on 2006-05-11
sudo postfix stop cured the problem.

But I thought that I read somewhere that Evolution used postfix in some way to speed things up.

At any rate, I downloaded a bunch of emails and I could not tell any difference.

CSSJR

---

### Post by cssutto on 2006-05-11
I spoke too soon.

I shut my machine down at the office, took it home and when I got it set up, checked Shields Up and 25 is open again.

Interesting.

CSSJR

---

### Post by nanotube on 2006-05-11
well, to stop postfix from loading at boot, you have to edit your startup config. can you look in your /etc/init.d folder, and see if anything looking like postfix is there? if you find it, run command
```
sudo update-rc.d -f postfix remove
```
(of course, replace "postfix" with the name of that startup script you find, if it is not, in fact, exactly "postfix".)

---

### Post by cssutto on 2006-05-11
Thanks.

I remember that other packages may use postfix, so we will see what happens.



CSSJR

---

### Post by nanotube on 2006-05-12
hmm, well, another thing you could do is simply put up a firewall and block off that port.
for a short and simple firewall config script and instructions, see the first link in my sig, and go to the firewall section.

---

