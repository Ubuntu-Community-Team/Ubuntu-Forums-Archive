---
title: "Ubuntu server... where to start?"
date: 2009-12-03
forum: General Help
---

### Post by LucasG on 2009-12-03
Well, I have just purchased a dedicated server from a local company in my country. I'm used to companies knowing how to run servers, but... most of the companies where I live now, have no clue, and there are no alternatives. So... I've told them to install Ubuntu Server x64 to run my personal gameservers... and well. I'm expecting a completely default installation, hopefully with right partitions.

Where should I start on securing and keeping my server running smoothly without too much crap? I know my way around linux, but I am in no way an advanced user, I wouldn't know how to compile a Kernel for example, and know almost nothing about iptables, plus, I'm worried my provider has not opened all the ports that linux uses by default, if any apart from 21 that should be opened.

Your help is really appreciated,

Thank you!

---

### Post by zman121 on 2009-12-03
I'd recommend checking out linux-mag.com and linux journal.  

The journal, in fact, sells a CD of back issues.  I can't vouch for it, as I haven't bought a copy yet.


I'd recommend serious reading / google research, as securing a system is a methodical process, not a question I can give  a drive-by answer to.

As a bare minimum, for any system connected to the web, its admin better learn about ssh (and why telnet is a really bad idea),  iptables,  tcpwrappers (hosts.allow and hosts.deny), and don't turn on any service if you haven't yet studied how to secure it.

It'll get easier as you study more and see how the pieces fit together.  If you google something specific that puzzles you, post a more specific question and I bet someone here will try to help you understand. 

Best of luck.

---

### Post by oldos2er on 2009-12-03
This is for 8.04, but it should apply to later releases too: [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by LucasG on 2009-12-03
> **zman121 said:**
> I'd recommend checking out linux-mag.com and linux journal.  

The journal, in fact, sells a CD of back issues.  I can't vouch for it, as I haven't bought a copy yet.


I'd recommend serious reading / google research, as securing a system is a methodical process, not a question I can give  a drive-by answer to.

As a bare minimum, for any system connected to the web, its admin better learn about ssh (and why telnet is a really bad idea),  iptables,  tcpwrappers (hosts.allow and hosts.deny), and don't turn on any service if you haven't yet studied how to secure it.

It'll get easier as you study more and see how the pieces fit together.  If you google something specific that puzzles you, post a more specific question and I bet someone here will try to help you understand. 

Best of luck.

I do know about ssh and a bit of iptables, as well as hosts.allow hosts.deny. Just wanting to go deeper.

---

### Post by wojox on 2009-12-03
Here's

[https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html)

[https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html)

---

### Post by memilanuk on 2009-12-03
Also... try searching in the Ubuntu community documentation for 'Server'

---

