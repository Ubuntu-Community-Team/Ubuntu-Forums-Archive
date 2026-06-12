---
title: "How do i install tor in ubuntu 9.10"
date: 2009-12-30
forum: General Help
---

### Post by spinny on 2009-12-30
Hey guys, i was asking for help on this forum, but the answers crawled to a stop...

[http://ubuntuforums.org/showthread.php?t=1308832](http://ubuntuforums.org/showthread.php?t=1308832)

Here is what i read and what i tried...

Quote:
Originally Posted by tiger2wander View Post
Read this: [https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

good luck!
I read the above directions and i did what it said, and here is the output from my terminal....

jim@ubuntubox:~$ sudo /etc/init.d/tor start
[sudo] password for jim:
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
done.
jim@ubuntubox:~$ sudo /etc/init.d/privoxy start
jim@ubuntubox:~$ netstat -a | grep 9050
tcp 0 0 localhost:9050 *:* LISTEN
jim@ubuntubox:~$

So i have also installed torbutton in firefox, and when i press it it goes green but then gives me the following message...

The most recent Tor proxy test failed to use Tor.

So i did the test again and it still failed. So now what do i do?? This is getting really frustrating to get a program going that in my opinion should be part of firefox.

So here is what i am running...

ubuntu netbook remix 9.10
wireless connection to a linksys router (linux version un modified)

I humbly request some help as i am still pretty green with ubuntu.

thanks

Any ideas, on how i get it to work??

Thanks

---

### Post by spinny on 2009-12-31
BUMP....

is this in the right forums??? if not could someone move it to the propperf forum so i can get some help?

Thanks so much, for the help as i have been stuck on this problem for weeks now.

---

### Post by spinny on 2010-01-03
No one can help me with tor??? 

please, i am stuck.

thanks

---

### Post by lostalot on 2010-01-03
I'm looking for some advice on installing, configuring, and using Tor myself.  I am a little surprised you haven't yet heard an answer on here, but be aware that many people have not gotten back from holidays yet (it is New Years after all).  My suggestion is to be patient and keep looking around for answers.  The answers will come if you are tenacious enough, and looking hard enough.  That's my plan. :)

---

### Post by bodhi.zazen on 2010-01-03
Follow the instructions on this page :

[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

add the tor repository to your sources ,

using any editor, open /etc/apt/sources.list

```
gksu gedit /etc/apt/sources.list
```

Add the tor repository

> deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) karmic main
Add the key:

```
gpg --keyserver keys.gnupg.net --recv 886DDD89[FONT=monospace]
[/FONT]gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```


Install tor:

```
sudo apt-get update
sudo apt-get install tor torgeoipdb
```

Now open firefox, install the tor button.

Restart firefox

Open the tor button preferences

In the preferences, unselect the polipo box

Use custom proxy settings

In SOCKS HOST use 127.0.0.1 port 9050

Change from socks v5 to socks v4

that is it, tor is now working =)

At the bottom of firefox, toggle the tor button

Confirm by going to 

[https://check.torproject.org](https://check.torproject.org)

---

### Post by xMoDx on 2011-08-24
> **spinny said:**
> BUMP....

is this in the right forums??? if not could someone move it to the propperf forum so i can get some help?

Thanks so much, for the help as i have been stuck on this problem for weeks now.

try this one
[http://xmodx.com/be-invisible-using-tor-in-linux/]("http://xmodx.com/be-invisible-using-tor-in-linux/")

---

