---
title: "SSH w/PuTTY Freezing Session"
date: 2012-08-01
forum: General Help
---

### Post by adeptusmechanicus on 2012-08-01
I've had an issue on multiple Amazon EC2 instances running Ubuntu 12.04 where any command I run which causes much of the terminal to redraw causes the SSH session to become unresponsive. 

I'm using PuTTY to connect to these instances and I've tried multiple versions of putty. .60, .62, and the development snapshot. Some of the commands that make it lock up are 'top', 'cat', any terminal multiplexer, and 'vim'. 

I've tried multiple character encodings, the ISO-8859-1 Latin encoding and UTF-8 and different keyboard emulation settings. My /etc/default/locale is set to UTF-8.  

I also tried using the Poderosa SSH client for windows and it had the same issue. I'm thinking the issue lies with the server configuration, but I don't know why, because it is nearly a stock install. 

Any help would be appreciated.

Update: I don't think this is PuTTY related, because I just confirmed that Cygwin has the same error.

---

### Post by adeptusmechanicus on 2012-08-02
Any ideas?

---

### Post by YankeePride13 on 2012-08-02
I don't know what the particular issue is here, but I can say that I have no issues connecting to my Amazon EC2 instance with putty.

I know this reply is not much help, but it at least confirms that you have something wrong in your config somewhere.

Perhaps contact Amazon support?

---

### Post by adeptusmechanicus on 2012-08-02
Thank you, I guess I will do so. 
It's just very bizarre, the symptoms I am experiencing. I didn't know if it was a known 12.04 bug or something else.

---

