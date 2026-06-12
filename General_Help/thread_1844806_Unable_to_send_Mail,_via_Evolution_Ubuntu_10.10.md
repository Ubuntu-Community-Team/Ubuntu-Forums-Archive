---
title: "Unable to send Mail, via Evolution Ubuntu 10.10"
date: 2011-09-15
forum: General Help
---

### Post by Bobrm2 on 2011-09-15
Since early this afternoon I suddenly can't send out emails. The only thing that changed was upgrades.

   My system is 10.10 and latest Evolution, and I see no change int Edit/preferences/account preferences/sending email.

  Would appreciate assistance, and will continue to search here and the net. Thanks


Bob R

---

### Post by haqking on 2011-09-15
> **Bobrm2 said:**
> Since early this afternoon I suddenly can't send out emails. The only thing that changed was upgrades.

   My system is 10.10 and latest Evolution, and I see no change int Edit/preferences/account preferences/sending email.

  Would appreciate assistance, and will continue to search here and the net. Thanks


Bob R


What is the error ?

connection refused, cant contact server, etc etc ?

can you ping the smtp server you are having issues with ?

---

### Post by Bobrm2 on 2011-09-15
There is no error message(s), just 3 mails sitting in the outbox? I really should know how to use the terminal to ping, but I don't;(. Thanks for stepping in.

Bob R

---

### Post by lisati on 2011-09-15
Take a look at the bottom of the main Evolution window. Error messages sometimes appear there, and if you click on them you can sometimes get more information.

---

### Post by haqking on 2011-09-15
> **Bobrm2 said:**
> There is no error message(s), just 3 mails sitting in the outbox? I really should know how to use the terminal to ping, but I don't;(. Thanks for stepping in.

Bob R


find out the smtp server settings (you put them in so i hope you know where to find them ;-)

then press ctrl+alt+t which will bring up terminal

then simple as can be:

```
ping -c 3 <smtp.whatever.com>
```
replace the < > with your smtp server obviously

---

### Post by Bobrm2 on 2011-09-15
No error messages at bottom of Evolution main screen.

ping send:
bob@Ubuntu:~$ ping -c 3 smtp.windstream.net
PING smtp.windstream.net (162.39.147.58) 56(84) bytes of data.

--- smtp.windstream.net ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms

bob@Ubuntu:~$

---

### Post by haqking on 2011-09-15
> **Bobrm2 said:**
> No error messages at bottom of Evolution main screen.

ping send:
bob@Ubuntu:~$ ping -c 3 smtp.windstream.net
PING smtp.windstream.net (162.39.147.58) 56(84) bytes of data.

--- smtp.windstream.net ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms

bob@Ubuntu:~$


i got the same result, 100% packet loss.

Server is down i suspect

actually looks like they reject pings then, as telnet is working.

try connecting on port 587 instead of 25

---

### Post by Bobrm2 on 2011-09-15
Have been on the phone with the ISP, Still unable to send the last two of this afternoons outgoing mail. Following pertains:

bob@Ubuntu:~$ ping -c 3 windstream.net
PING windstream.net (162.39.145.20) 56(84) bytes of data.
64 bytes from www2.windstream.net (162.39.145.20): icmp_req=1 ttl=56 time=72.2 ms
64 bytes from www2.windstream.net (162.39.145.20): icmp_req=2 ttl=56 time=66.2 ms
64 bytes from www2.windstream.net (162.39.145.20): icmp_req=3 ttl=56 time=75.5 ms

--- windstream.net ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 66.285/71.368/75.572/3.848 ms
bob@Ubuntu:~$

---

### Post by haqking on 2011-09-15
> **Bobrm2 said:**
> Have been on the phone with the ISP, Still unable to send the last two of this afternoons outgoing mail. Following pertains:

bob@Ubuntu:~$ ping -c 3 windstream.net
PING windstream.net (162.39.145.20) 56(84) bytes of data.
64 bytes from www2.windstream.net (162.39.145.20): icmp_req=1 ttl=56 time=72.2 ms
64 bytes from www2.windstream.net (162.39.145.20): icmp_req=2 ttl=56 time=66.2 ms
64 bytes from www2.windstream.net (162.39.145.20): icmp_req=3 ttl=56 time=75.5 ms

--- windstream.net ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 66.285/71.368/75.572/3.848 ms
bob@Ubuntu:~$

that is pinging the webserver.

Like i said i can telnet to the SMTP server so perhaps changing your port which is probably defaulting to 25 to 587 instead so where your smtp settings are just append the colon and 587 on end so.

smtp.windstream.net:587

try that ?

---

### Post by Bobrm2 on 2011-09-15
Well, I changed the port to ...windstream.net:587 with negative results.

 I don't know if this, and I can't see why, but the two messages still in the outbox, are addressed to [email]undisclosedrecepent@windstream.net[/email].  all valid addressee are BCC'ed. Was trying to protect the actual addressees.????

---

### Post by haqking on 2011-09-15
> **Bobrm2 said:**
> Well, I changed the port to ...windstream.net:587 with negative results.

 I don't know if this, and I can't see why, but the two messages still in the outbox, are addressed to [EMAIL="undisclosedrecepent@windstream.net"]undisclosedrecepent@windstream.net[/EMAIL].  all valid addressee are BCC'ed. Was trying to protect the actual addressees.????


have you tried just removing them from your outbox.

and try sending a test mail say to yourself or something, perhaps they are just stuck.

and if 587 didnt work, remove it and go back to previous.

What did the ISP say in response ?

---

### Post by Bobrm2 on 2011-09-15
I did, and resent one of the to the new email address. I passed with flying colors, and landed back in the inbox as should have done. I don't know but for now the problem, though not the "why" is solved. Thanks you for you help.

Bob

Oh, will delete the :587

---

### Post by haqking on 2011-09-16
> **Bobrm2 said:**
> I did, and resent one of the to the new email address. I passed with flying colors, and landed back in the inbox as should have done. I don't know but for now the problem, though not the "why" is solved. Thanks you for you help.

Bob

Oh, will delete the :587


No worries, temporary glitch by the sounds of it.  It happens.

remember to mark the thread as solved using thread tools.

Cheers

---

