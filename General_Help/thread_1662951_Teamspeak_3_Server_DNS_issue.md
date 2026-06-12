---
title: "Teamspeak 3 Server DNS issue"
date: 2011-01-08
forum: General Help
---

### Post by Weidbrewer on 2011-01-08
I am currently having an issue with trying to set up a Teamspeak 3 Server on my Ubuntu 10.04 64 machine.  I've got it installed and it starts.  I am also able to connect from another machine on my network, however, it crashes after a few minutes.  Here is the log:

```
2011-01-02 17:18:38.392145|INFO    |ServerLibPriv |   | Server Version: 3.0.0-beta30 [Build: 12998], Linux
2011-01-02 17:18:38.418723|INFO    |DatabaseQuery |   | dbPlugin name:    SQLite3 plugin, Version 2, (c)TeamSpeak Systems GmbH
2011-01-02 17:18:38.558337|INFO    |DatabaseQuery |   | dbPlugin version: 3.7.3
2011-01-02 17:18:38.621778|INFO    |DatabaseQuery |   | checking database integrity (may take a while)
2011-01-02 17:18:38.786132|INFO    |SQL           |   | pruning old database log entries where timestamp is older than 90 days
2011-01-02 17:18:38.841682|WARNING |Accounting    |   | Unable to find valid license key, falling back to limited functionality
2011-01-02 17:18:39.043949|INFO    |FileManager   |   | listening on 0.0.0.0:30033
2011-01-02 17:18:39.044166|ERROR   |              |   | TS3ANetwork::ResolveHostName failed error: -2 (Name or service not known) 2
2011-01-02 17:18:39.057913|ERROR   |              |   | Could not open default UDP connection for weblist
2011-01-02 17:18:39.093873|ERROR   |              |   | TS3ANetwork::ResolveHostName failed error: -2 (Name or service not known) 2
2011-01-02 17:18:39.094382|ERROR   |              |   | resolving '' to binary ip failed, using 0.0.0.0 instead
2011-01-02 17:18:39.215582|INFO    |VirtualServer |  1| listening on 0.0.0.0:9987
2011-01-02 17:18:39.237072|INFO    |CIDRManager   |   | updated query_ip_whitelist ips: 127.0.0.1, 
2011-01-02 17:18:39.237647|INFO    |Query         |   | listening on 0.0.0.0:10011
2011-01-02 17:23:39.084638|CRITICAL|NET           |   | AddToSet epoll_ctl fail with 1
```

When I posted it over on the Teamspeak forums, I was told that it is a DNS issue, and that I need to start my DNS server...however, their only advice on how to do this was to google a tutorial.  More often than not, when I blindly follow a random tutorial, it ends in tears.  Does anyone here have any idea what the best way to solve my problem is?  

Thanks in advance!

---

### Post by dcstar on 2011-01-08
> **Weidbrewer said:**
> I am currently having an issue with trying to set up a Teamspeak 3 Server on my Ubuntu 10.04 64 machine.  I've got it installed and it starts.  I am also able to connect from another machine on my network, however, it crashes after a few minutes.  Here is the log:

```
2011-01-02 17:18:38.392145|INFO    |ServerLibPriv |   | Server Version: 3.0.0-beta30 [Build: 12998], Linux
2011-01-02 17:18:38.418723|INFO    |DatabaseQuery |   | dbPlugin name:    SQLite3 plugin, Version 2, (c)TeamSpeak Systems GmbH
2011-01-02 17:18:38.558337|INFO    |DatabaseQuery |   | dbPlugin version: 3.7.3
2011-01-02 17:18:38.621778|INFO    |DatabaseQuery |   | checking database integrity (may take a while)
2011-01-02 17:18:38.786132|INFO    |SQL           |   | pruning old database log entries where timestamp is older than 90 days
2011-01-02 17:18:38.841682|WARNING |Accounting    |   | Unable to find valid license key, falling back to limited functionality
2011-01-02 17:18:39.043949|INFO    |FileManager   |   | listening on 0.0.0.0:30033
2011-01-02 17:18:39.044166|ERROR   |              |   | TS3ANetwork::ResolveHostName failed error: -2 (Name or service not known) 2
2011-01-02 17:18:39.057913|ERROR   |              |   | Could not open default UDP connection for weblist
2011-01-02 17:18:39.093873|ERROR   |              |   | TS3ANetwork::ResolveHostName failed error: -2 (Name or service not known) 2
2011-01-02 17:18:39.094382|ERROR   |              |   | resolving '' to binary ip failed, using 0.0.0.0 instead
2011-01-02 17:18:39.215582|INFO    |VirtualServer |  1| listening on 0.0.0.0:9987
2011-01-02 17:18:39.237072|INFO    |CIDRManager   |   | updated query_ip_whitelist ips: 127.0.0.1, 
2011-01-02 17:18:39.237647|INFO    |Query         |   | listening on 0.0.0.0:10011
2011-01-02 17:23:39.084638|CRITICAL|NET           |   | AddToSet epoll_ctl fail with 1
```

When I posted it over on the Teamspeak forums, I was told that it is a DNS issue, and that I need to start my DNS server...however, their only advice on how to do this was to google a tutorial.  More often than not, when I blindly follow a random tutorial, it ends in tears.  Does anyone here have any idea what the best way to solve my problem is?  

Thanks in advance!

Put whatever DNS name it is trying to use in the /etc/hosts file.

---

### Post by Weidbrewer on 2011-01-08
> **dcstar said:**
> Put whatever DNS name it is trying to use in the /etc/hosts file.

Bear with me - I've heard the term "DNS" before, but am not 100% clear on what it is.  How do I know what name it is, and in the /etc/hosts file is there something that says something to the effect of "DNS name goes here"?

---

### Post by dcstar on 2011-01-09
> **Weidbrewer said:**
> Bear with me - I've heard the term "DNS" before, but am not 100% clear on what it is.  How do I know what name it is, and in the /etc/hosts file is there something that says something to the effect of "DNS name goes here"?

[https://secure.wikimedia.org/wikipedia/en/wiki/Domain_Name_System](https://secure.wikimedia.org/wikipedia/en/wiki/Domain_Name_System)

---

### Post by Weidbrewer on 2011-01-09
> **dcstar said:**
> [https://secure.wikimedia.org/wikipedia/en/wiki/Domain_Name_System](https://secure.wikimedia.org/wikipedia/en/wiki/Domain_Name_System)


AAAAAAAAAAAAAARGH!  :D:D:D

Okay,not trying to sound ungrateful, but this is the second forum I've just gotten a wiki entry in response.  Yeah, woosh, right over my head.

Seriously is there *anyone* out there who can dumb this down for me, or is this issue seriously this complex and best abandoned as a bad idea for me to pursue?

---

### Post by Weidbrewer on 2011-01-10
Any ideas?

---

### Post by Weidbrewer on 2011-01-14
Figure I'll throw one more "HELP!" in here.


HELP! :D

---

### Post by frenzy_usa on 2011-01-15
How are you starting the TS3 server? From the command line (using ./ts3server_linux_x86 or ./ts3server_linux_amd64) or as a startup script in /etc/init.d?

---

### Post by Weidbrewer on 2011-01-15
Startup script.

More or less buy these instructions:

[http://robert.penz.name/296/howto-install-teamspeak-3-server-on-ubuntu-10-04-lucid/](http://robert.penz.name/296/howto-install-teamspeak-3-server-on-ubuntu-10-04-lucid/)

---

### Post by frenzy_usa on 2011-01-16
Did you try running the following commands?
```
update-rc.d -f teamspeak remove
update-rc.d teamspeak defaults 99
```
They are from comment #14 on the page you mentioned.  These commands will delay the start up of the TS3 server until after everything else has been loaded.

---

### Post by Weidbrewer on 2011-01-17
Thanks for the reply!

No, I did not try those, as I wasn't really clear on what they do...And since it took me so long to get TS3 installed and running, I was a bit nervous about trying any commands with "remove" in them.  
So, 
[LIST=1]
[*]What do these commands do
[*]Are they terminal commands, or things that I need to add to the script
[*]Does it matter that I am able to start the server and connect, but it fails after a few minutes?  (want to be 100% sure it's the same issue - it looks like it from the user's comments, but I'm paranoid.)
[/LIST]

Thanks again for the help!

---

### Post by VagueNess on 2011-05-07
I'm using Ubuntu Server 11.04 with TeamSpeak 3 and I'm having the exact same problem. I followed the same guide as the thread starter, and I'm having the same errors. 

TeamSpeak gets started by the init.d script from that guide, I can connect just fine, but after about five minutes TeamSpeaks crashes, as you can see from the "CRITICAL" error in the logs.

When I start TeamSpeak manually, either using the standard TS3 start shell script or the init.d script, I do not have these problems or errors.

I have tried the solutions posted in the guide, that have been posted here also (i.e., changing the order of the boot scripts so that TeamSpeak gets started last, after any networking startup scripts). These seem to work for others, but unfortunately not for me. Besides that, I have tried setting Required-Start in the init.d script to both "$all" and to "$networking $named", and I have tried putting the script in rc.local. All of these attempts were without succes.

So now I've run out of ideas, and I really hope someone here has one. If anyone needs any logs files or other information, I'd be happy to provide that.

Thanks.

---

