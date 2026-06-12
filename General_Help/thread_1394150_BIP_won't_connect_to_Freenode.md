---
title: "BIP won't connect to Freenode"
date: 2010-01-30
forum: General Help
---

### Post by MetalMusicAddict on 2010-01-30
I'm hoping some other BIP users know what's up. I know Freenode went through a couple of changes this weekend so I think that's what I'm hitting.

Relevant lines from my BIP log:
```
[SIZE="2"]30-01-2010 06:40:40 Connecting user 'user' to network 'freenode' using server irc.freenode.net:6667
30-01-2010 06:40:51 ERROR: read(fd=7): Connection lost: Operation now in progress
30-01-2010 06:40:51 ERROR: Error while reading on fd 7
30-01-2010 06:40:51 ERROR: read_lines error, closing freenode ...
30-01-2010 06:40:51 ERROR: freenode dead, reconnecting in 600 seconds[/SIZE]
```

Has printed that over and over for about 10hrs now and I can connect directly to Freenode just fine. Just not through BIP.

---

### Post by merpattersonnet on 2010-01-31
I am also seeing this exact same symptom using Bip to connect to Freenode via SSL.  This happens from both ERC (emacs IRC client) and from AndChat (android IRC client) and seems to be in bip, having nothing to do with the client.

---

### Post by djbclark on 2010-03-12
I also saw this when I moved from 0.80 to 0.82; downgrading back to 0.80 fixed the problem.

---

### Post by oubiwann on 2011-05-16
Yup, I'm having the same problem:

[FONT="Courier New"]16-05-2011 15:09:58 [freenode] Connecting user 'XXX' using server irc.freenode.net:6667
16-05-2011 15:09:59 [freenode] Connected for user XXX[/FONT]

[snip a bunch of backlog notices]

[FONT="Courier New"]16-05-2011 15:10:58 ERROR: read(fd=5): Connection lost: Success
16-05-2011 15:10:58 ERROR: Error while reading on fd 5
16-05-2011 15:10:58 ERROR: [freenode] read_lines error, closing...
16-05-2011 15:10:58 ERROR: [freenode] reconnecting in 0 seconds
16-05-2011 15:10:59 ERROR: read(fd=23): Connection lost: Success
16-05-2011 15:10:59 ERROR: Error while reading on fd 23
16-05-2011 15:10:59 ERROR: client read_lines error, closing...
16-05-2011 15:11:00 [freenode] Connecting user 'XXX' using server irc.freenode.net:6667
16-05-2011 15:11:00 [freenode] Connected for user XXX[/FONT]

I checked my version of bip ([FONT="Courier New"]dpkg -l bip[/FONT]) and I have 0.8.2-1. I'll see what other versions are available for 10.04 LTS ...

---

### Post by oubiwann on 2011-05-16
> **oubiwann said:**
> Yup, I'm having the same problem:

[snip]

 I have 0.8.2-1. I'll see what other versions are available for 10.04 LTS ...

Well, I just tried installing the latest package from Oneiric (which also required the latest SSL). The installations went fine, but the bug persists. Here are the packages I downloaded to my server:

[http://launchpadlibrarian.net/64948052/libssl0.9.8_0.9.8o-5ubuntu1_i386.deb](http://launchpadlibrarian.net/64948052/libssl0.9.8_0.9.8o-5ubuntu1_i386.deb)
[http://launchpadlibrarian.net/70814284/bip_0.8.8-1_i386.deb](http://launchpadlibrarian.net/70814284/bip_0.8.8-1_i386.deb)

Since the latest didn't work, I'll downgrade to 0.8 like djbclark mentioned...

---

### Post by oubiwann on 2011-05-16
> **oubiwann said:**
> Since the latest didn't work, I'll downgrade to 0.8 like djbclark mentioned...

Yup, that worked for me. I downloaded and installed the following (0.8.0-1), and now I can connect to Freenode (again) just fine:

[http://launchpadlibrarian.net/26203261/bip_0.8.0-1_i386.deb](http://launchpadlibrarian.net/26203261/bip_0.8.0-1_i386.deb)

---

