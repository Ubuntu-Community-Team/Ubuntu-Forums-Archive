---
title: "telnet timeout"
date: 2012-01-21
forum: General Help
---

### Post by advanced93 on 2012-01-21
Hello,

I'v installed postfix and dovecot. All config files should be okay, I'v followed [https://help.ubuntu.com/11.04/serverguide/C/postfix.html](https://help.ubuntu.com/11.04/serverguide/C/postfix.html) 

But the problem is when im supposed to write "telnet mail."mydomain".com 25 it stands:

Trying "ip"...
Trying "ip"...
"telnet: Unable to connect to remote host: Connection timed out"

Port 25 is open and I have tested to ping the mailserver from my own Windows machine and that works correctly.

So why does it keeps on getting timed out?

---

### Post by imachavel on 2012-01-21
did you open it as

i.p. address: port number

e.g.

rdp 10.1.10.1:3389?

is port 3389 open?

did you toggle between NAT and bridged networking??

I never had any telnet success myself. You could try team viewer but those same ports need to be open. Sorry, I just don't know.

---

### Post by abhijeet.1308 on 2012-01-21
can you please provide some detail about what actully you what to do?  and if you want to connect windows m/c plz turn off windows firewall and anti-virus firewall if any...

---

### Post by advanced93 on 2012-01-21
> **imachavel said:**
> did you open it as

i.p. address: port number

e.g.

rdp 10.1.10.1:3389?

is port 3389 open?

did you toggle between NAT and bridged networking??

I never had any telnet success myself. You could try team viewer but those same ports need to be open. Sorry, I just don't know.

Yes, I just opened port 3389 up but still same error.

---

### Post by advanced93 on 2012-01-21
> **abhijeet.1308 said:**
> can you please provide some detail about what actully you what to do?  and if you want to connect windows m/c plz turn off windows firewall and anti-virus firewall if any...

Im doing this on a linux server (ubuntu) not Windows.

---

