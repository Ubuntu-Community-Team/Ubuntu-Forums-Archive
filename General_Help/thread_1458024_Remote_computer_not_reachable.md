---
title: "Remote computer not reachable"
date: 2010-04-19
forum: General Help
---

### Post by umeboshi80 on 2010-04-19
Hi,

I hope I am not repeating a thread. I am trying something very simple: To remotely connect from a ubuntu desktop to another ubuntu server (physically not reachable).
When I ping the server, it seems to be fine. However, when I try to ssh, the connection is closed by the host. I am the only one using the server.

It worked fine a few hours ago and I was trying to copy a lot of data using a couple of scp sessions. At some point the connection was closed and I cannot access the server anymore.

Any ideas how I can proceed from here?

Thanks a lot!
Hadassa

---

### Post by new_tolinux on 2010-04-19
I guess something went wrong somewhere.

My first try would be to reset the server (if it's in a datacentre you're probably have to telnet to some UPS in order to do so).

Although..... connect from a desktop to "a server" is a bit vague..... I guess most of us would like some more specific info about the "a server" part.

---

### Post by umeboshi80 on 2010-04-19
Hi,

Thanks for replying. Actually I have two Ubuntu machines, both desktop version with a server installed on top. They are both on the same network. When I restart the remote computer, I can work on it fine for a while and then the connection is reset and when I am trying to ssh into it again I get the following:

Read from remote host ...: Connection reset by peer
lost connection

(where ... is the ip address)

When I do ssh -vv it gets to the point where it asks me for the password and then the output is:

debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug1: channel 0: free: client-session, nchannels 1
Read from remote host ... : Connection reset by peer
Connection to ... closed.
Transferred: sent 1280, received 1752 bytes, in 98.9 seconds
Bytes per second: sent 12.9, received 17.7
debug1: Exit status -1


And this has only happened recently. I am at loss of ideas. Thanks for any input.
Hadassa

---

