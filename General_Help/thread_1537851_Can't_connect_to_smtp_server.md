---
title: "Can't connect to smtp server"
date: 2010-07-24
forum: General Help
---

### Post by glendavee on 2010-07-24
I have been using evolution to send/receive email from my account with 123-reg with no problems. My home ISP is aol. 
I am currently on vacation in France and using orange.fr as my ISP. I can still receive email from 123-reg but when I try to send, get the error message "Could not connect to smtp.123-reg.co.uk: No route to host" 123-reg help seem to be either clueless or not bothered.
I've tried altering settings in evolution preferences, but nothing seems to work. Currently set to "server requires authentication"
Any suggestions?????

---

### Post by robsoles on 2010-07-24
Most ISPs block SMTP (port [COLOR=Red]45[/COLOR]) traffic that doesn't come from their own customers and quite a few block port [COLOR=Red]45[/COLOR] from their own customers to other ISPs.

You need to find out what orange.fr support as far as your outgoing mail is concerned while using their services.


EDIT: Where I have highlighted '45' in red above is because I am reminded that port 25 is the usual SMTP port and I probably shouldn't post this tired!

---

### Post by dcstar on 2010-07-24
> **glendavee said:**
> I have been using evolution to send/receive email from my account with 123-reg with no problems. My home ISP is aol. 
I am currently on vacation in France and using orange.fr as my ISP. I can still receive email from 123-reg but when I try to send, get the error message "Could not connect to smtp.123-reg.co.uk: **No route to host**" 123-reg help seem to be either clueless or not bothered.
I've tried altering settings in evolution preferences, but nothing seems to work. Currently set to "server requires authentication"
Any suggestions?????

That message means **your** networking is faulty, do:

```
telnet smtp.123-reg.co.uk 25
```

smtp.123-reg.co.uk resolves to 94.136.40.63 on my system, what happens on yours?

---

### Post by robsoles on 2010-07-24
mmmh, yep - I shouldn't post this tired, I should have written '25' everywhere I wrote 45 in my prior post - sorry.


If OP can open [http://www.123-reg.co.uk/](http://www.123-reg.co.uk/) with a browser but cannot send mail nor telnet as specified by dcstar then, although I was stating wrong port, it is basically due to ISP or other blocker on port 25 as I suggested.


The fact that you OP can receive emails OK but cannot send them makes me think it is an ISP level block being applied by orange.fr (I am with an Australian ISP that doesn't block outgoing SMTP from/on my connection and I could hit the smtp.123-reg.co.uk server on port 25)

---

### Post by glendavee on 2010-07-24
When I telent, here's result.

david@david-laptop:~$ telnet smtp.123-reg.co.uk 25
Trying 94.136.40.63...
telnet: Unable to connect to remote host: No route to host
david@david-laptop:~$ 

Presume this means orange.fr is blocking?
Interesting that I can send on my aol account (smtp.aol.com:587)

---

### Post by robsoles on 2010-07-24
> **glendavee said:**
> When I telent, here's result.

david@david-laptop:~$ telnet smtp.123-reg.co.uk 25
Trying 94.136.40.63...
telnet: Unable to connect to remote host: No route to host
david@david-laptop:~$ 

Presume this means orange.fr is blocking?
Interesting that I can send on my aol account (smtp.aol.com:587)

I just checked and smtp.123-reg.co.uk:587 is listening for SMTP connections as well. The :587 on the end of your AOL SMTP address indicates to the mail program to use port 587 for that server.

try
```
telnet smtp.123-reg.co.uk 587
```

and if you get roughly similar to
```
Trying 94.136.40.63...
Connected to smtp.123-reg.co.uk.
Escape character is '^]'.
220 mail5.atlas.pipex.net ESMTP Exim 4.71 - "ATLAS SMTP Service" Sat, 24 Jul 2010 15:21:55 +0100
```
then type
```
quit
```
and then change the address in your mail SMTP setting for 123-reg.co.uk to have :587 at the end as well.

The reason the server is running this alternative port is because where port 25 is commonly blocked due to high number of exploits in the past the alternative(s) are rarely blocked.

---

### Post by glendavee on 2010-07-24
Many thanks Robsoles. Adding the :587 did the trick!

---

