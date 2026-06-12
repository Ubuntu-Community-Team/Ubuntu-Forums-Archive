---
title: "read and write to tty"
date: 2011-06-20
forum: General Help
---

### Post by dfgilbert on 2011-06-20
Here's the story:

**TL;DR** - I want to setup a remote computing scheme with limited permissions on the servers I'll be computing on.  I need to force terminal commands into different TTYs.

**Long version:**
I have a home computer and two external servers.  I do not have permission to change anything on the servers (config, install applications, etc).  I can, however, use them to run python/perl scripts and applications that are installed on the servers.

In order to access the servers, I have to tunnel through a gateway.

Both servers are Solaris Machines, I'm using Ubuntu Linux on my home machine.

What I want to be able to do is have either a program or script monitor the SSH sessions between my home computer and the external servers from my home computer.

So, let TH be the terminal on my home computer, S1 and S2 be the terminals remotely connected to server 1 and server 2, respectively.

I want to write a script that can force commands from TH into S1 or S2 and also read from their standard output.  

**Main Question:**
What tools can I use to achieve this?  I read a link below, but it may as well be written in Klingon since it pre-supposes some knowledge.

Ideally, TH will spawn S1 and S2 automatically (maybe even in the background) and communicate with them.

---

