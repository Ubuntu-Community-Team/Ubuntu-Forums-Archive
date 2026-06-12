---
title: "Evolution will recieve but not send e'mail"
date: 2009-08-30
forum: General Help
---

### Post by 5BallJuggler on 2009-08-30
Hi all, had a quick look for this on the forums, but can't seem to find it.

I've been using ubuntu for a good while now and have no issues when i'm at home(in the UK), but I came out to Japan yesterday on business. everything works fine except evolution e'mail.

If i connect to the internet and start evolution it will download all of my mail from the server (which is good), however I wrote a reply to an e'mail that I had recieved and then tried to send it, it is now just sitting there in my outbox

I have tried changing some smtp settings, but as I don't know what i'm doing it has remained inoperable.

i'm using pop.freeserve.net to recieve
and smtp.freeserve.net to send

can someone please give some ideas on what to change please.

Thanks in advance
Phil

---

### Post by Bucky Ball on 2009-08-30
Try 'pop.freeserve.net' for both.

Are you absolutely sure that you are pointing at the correct mail out server for freeserve?

---

### Post by 5BallJuggler on 2009-08-30
> **Bucky Ball said:**
> Try 'pop.freeserve.net' for both.

Are you absolutely sure that you are pointing at the correct mail out server for freeserve?

I have just tried this and unfortunately it didn't work, 

these settings work at home,I thought that they should stay the same abroad.

---

### Post by Copernicus1234 on 2009-08-30
In that case your ISP is blocking access to it from abroad.

I had a ISP that did that too. You could only connect to the smtp server from their own ip range.

Try:

```
telnet pop.freeserve.net 25
telnet pop.freeserve.net 110
```

in a command prompt. If connection is accepted on port 110 but not 25, then they are blocking smtp in the firewall.

I tried it from here (Sweden) and I get blocked on port 25.

---

### Post by 5BallJuggler on 2009-08-30
the telnet command pop.freeserve.net 110 works ok, 
should the same apply smtp.freeserve.net 110?

this is the output from the terminal
```

phil@phil-netbook:~$ telnet pop.freeserve.net 25
Trying 193.252.22.154...
^C
phil@phil-netbook:~$ telnet smtp.freeserve.net 25
Trying 193.252.22.188...
^C
phil@phil-netbook:~$ telnet smtp.freeserve.net 110
Trying 193.252.22.188...
^C
phil@phil-netbook:~$ telnet pop.freeserve.net 110
Trying 193.252.22.136...
Connected to pop.freeserve.com.
Escape character is '^]'.
+OK connected to pop3 on 3611
``` 

when I use the command pop.freeserve.net:110, in evolution i get 

"Error while performing operation.

Welcome response error: connected to pop3 on 3611"
when i try to send messages.

---

### Post by 5BallJuggler on 2009-08-30
> **Copernicus1234 said:**
> In that case your ISP is blocking access to it from abroad.

I had a ISP that did that too. You could only connect to the smtp server from their own ip range.

Try:

```
telnet pop.freeserve.net 25
telnet pop.freeserve.net 110
```

in a command prompt. If connection is accepted on port 110 but not 25, then they are blocking smtp in the firewall.

I tried it from here (Sweden) and I get blocked on port 25.


Sorry, I just reread this. so myy smtp is blocked while abroad. is there a way around this??

---

### Post by Ms_Angel_D on 2009-08-30
You could try maybe using gmail instead for sending, or some other free mail service with free SMTP access.

---

### Post by dandnsmith on 2009-08-30
I found that, for me, the easiest solution was to open a gmail account and use that to send emails when out of the country.

I had a look at several possible ways, including some locally installed direct mail senders, but this one worked where others wouldn't.

---

