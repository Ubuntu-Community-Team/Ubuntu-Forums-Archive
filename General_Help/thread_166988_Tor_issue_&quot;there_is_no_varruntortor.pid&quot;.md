---
title: "Tor issue: &quot;there is no /var/run/tor/tor.pid&quot;"
date: 2006-04-27
forum: General Help
---

### Post by Luke771 on 2006-04-27
The Tor anonymizer needs a file called /var/run/tor/tor.pid, but that file keeps disappearing: anybody knows why? And how to fix that?

Shut down sequence:```


Stopping this..................[ok]
stopping that..................[ok]
stopping that thing too.....[ok]
Stopping Tor daemon ......[not running]
.........[There is no /var/run/tor/tor.pid]
```


I start again and check it out:
Try running Tor from the command line and get the same line about no /var/run/tor/tor.pid being there; Tor can't start.

Then I go to /var/run/tor/ and create an empty file called tor.pid
The permissions to the tor directories are already set to property of "luke" (my user name) instead of property of some user called "debian-tor" as they were created by the repository installer.

I try to run Tor from the command line again, and it works.
(privoxy is already running as daemon) I run Firefox, switch proxy to Privoxy (yes, the forwarding line is there) 
Works fine.

OK

I shut down again, and the sequence goes like stopping this, OK. Stopping that, OK, ```


Stopping Tor daemon...........[OK]
```

Fine.

After a while I use the computer again, and while shutting down I get the same line:

```


Stopping Tor daemon .....[not running]
.................[there is no /var/run/tor/tor.pid]
```

I know that I can make it work by making a file called tor.pid in /var/run/tor/, but I don't understand why it keeps disappearing and how do I fix that
And what is a .pid file anyway?

---

### Post by j-strap2 on 2006-04-28
Which version of Tor are you using, the standard breezy package? Last time I looked, the standard breezy package was fairly old - upgrading to the latest stable release is recommended.

The .pid file is used to track the process ID that Tor is running as - the shutdown script uses it to kill the process. Some of the ubuntu Tor packages are misconfigured so that the Tor scripts can't find the .pid file.

There are some up-to-date ubuntu packages. Add these lines to your /etc/apt/sources.list, reload and update in synaptic and Bob's your uncle:

deb [http://mirror.noreply.org/pub/tor/](http://mirror.noreply.org/pub/tor/) breezy main 
deb-src [http://mirror.noreply.org/pub/tor/](http://mirror.noreply.org/pub/tor/) breezy main

---

### Post by i M@N on 2007-06-17
Hello Luke.

i had the same problem a few minutes ago, here is how i fixed it :
First i made and empty /var/run/tor/tor.pid file (create tor.pid in your /home and sudo mv tor.pid /var/run/tor/tor.pid) and then gave it to deban-tor :
```
sudo chown debian-tor:debian-tor /var/run/tor/tor.pid
```
i added myself to the debian-tor group :
```
sudo adduser iman debian-tor
```
Then i've modified the file /etc/tor/torrc :
```
sudo gedit /etc/tor/torrc
```
to put in :
> User debian-tor
Group debian-tor

i started / restarted tor :
```
sudo /etc/init.d/tor start
sudo /etc/init.d/privoxy start
```

and everything woked fine. ;)

Hope that helps,

@+...

---

