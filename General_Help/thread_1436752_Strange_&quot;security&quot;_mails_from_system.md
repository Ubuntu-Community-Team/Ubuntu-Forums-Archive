---
title: "Strange &quot;security&quot; mails from system"
date: 2010-03-23
forum: General Help
---

### Post by paulkater on 2010-03-23
Hi all,
Since I am running Ubuntu 9.10, I get strange mails from the machine. Several times a day I see something like ('coal is my hostname):

subject: *** SECURITY information for coal ***

and the mail body is:

coal : Mar 23 07:35:02 : root : <insert weird graphical character>

Does anyone know where this comes from, what it means and how to deal with this?

Thanks!

---

### Post by djchandler on 2010-03-23
Are you exposed to an outside network and remote log-in has been enabled?

This looks to me like the kind of message you may get if someone is trying to log-in as root and guess the root password. Of course the root account is disabled by default in Ubuntu.

Check your firewall settings. Go to [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2") and check for exposed ports. Correct your iptables to address your problem. I've used Firestarter in the past, but it is seemingly out of favor with those perhaps more knowledgeable than I.

---

### Post by paulkater on 2010-03-23
Thanks for your reply. Shields Up tells me that FTP and HTTP are enabled (which I know), remote login like telnet is not open though.

Doesn't look like something too serious then, but I will look around a bit more to see if I can dig something up.

---

### Post by pbpersson on 2010-03-23
What exactly were you doing at Mar 23 07:35:02?  Were you even using the machine?  If the FTP port is open to the outside world, there are always automated processes trying to find a way in.

---

### Post by rnerwein on 2010-03-23
hi
you got some mail: coal : Mar 23 07:35:02 : root : <insert weird graphical character>
i can tell you in former times ( 25 years ago ) we almost made funny things with mail. mail wasn't
scanned by the system for specail characters. we send mail to other friends with special ESC characters  inside. the keyboard driver will read those characters and interpreted them as commands when you open the mail. we only did funny things. but you can imagine whats hapen if
your F1 key ist set to a short cut like "rm .....".
have a look at your mail - to be on the secure side use "hd -c your_mail_file"
ciao

---

### Post by paulkater on 2010-03-23
> **pbpersson said:**
> What exactly were you doing at Mar 23 07:35:02?  Were you even using the machine?

Yes, I was on the machine then. I have found so far that the strange security mails seem to be an effect from Postfix. The date-stamp on the mails is exactly the same as mails that are sent. Funny thing is though that not all sent mails trigger such a security e-mail.
I'll have to look further, if it has to do with a specific domain or something that mayhaps give a strange response to Postfix. Even when Postfix uses the mailserver of my ISP as a relayhost. Hmmm

---

### Post by paulkater on 2010-03-23
> **rnerwein said:**
> have a look at your mail - to be on the secure side use "hd -c your_mail_file"
ciao

Thank you for this tip, I had a look but that does not reveal anything alarming, so far. I'll keep an eye on that too, though.

---

### Post by djchandler on 2010-03-29
> **paulkater said:**
> Thanks for your reply. Shields Up tells me that FTP and HTTP are enabled (which I know), remote login like telnet is not open though.

Doesn't look like something too serious then, but I will look around a bit more to see if I can dig something up.

They should show being in stealth mode so anybody pinging your ip doesn't get an echo. When you scan those ports including HTTP and FTP at Shields Up the whole array should be colored green. Anything else indicates trouble IMO.

---

### Post by paulkater on 2010-03-29
I am not sure why, but since a few days I have not seen these strange mails anymore. I'll see what I can do about the echoes wrt Shields Up though. Thanks.

---

