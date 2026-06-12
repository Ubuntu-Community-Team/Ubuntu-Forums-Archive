---
title: "Problem with sending email using Evolution, &quot;no route to host&quot;"
date: 2009-08-19
forum: General Help
---

### Post by lejonmanen on 2009-08-19
Hello!

I'm having trouble getting Evolution to work with an email account of mine. When I send/receive mail I get the message "No route to host" (in swedish).

Sending and receiving mail works like a charm when I use Thunderbird on Windows so the mail server appears innocent. Can someone point me in the right direction here? Could it have something to do with proxy settings in Evolution?

---

### Post by enz1m3 on 2009-08-21
It does look like you mistyped the domain name (or server host) or the proxy settings aren't correct.

Can you open a terminal and type:

$ sudo tracert YOUR_HOSTNAME_HERE

And see if you can "reach" to the hostname?

---

### Post by lejonmanen on 2009-08-22
Thanks for the reply. I did what you asked:

[FONT=Courier New]david@ubuntu:~$ sudo tracert mail.tele2.se
[sudo] password for david:
traceroute to mail.tele2.se (212.247.156.1), 30 hops max, 60 byte packets
 1  modem.lan (192.168.0.254)  74.791 ms  74.050 ms  73.195 ms
 2  d83-183-96-1.cust.tele2.se (83.183.96.1)  32.294 ms * *
 3  * * *
 4  * * *
 5  * * *
 6  * kst-core-1.pos1-0-0.swip.net (130.244.39.141)  38.002 ms  36.232 ms
 7  * * kst-ncore-1.tengigabiteth2-1.swip.net (130.244.52.106)  36.401 ms
 8  * kst-ncore-2.tengigabiteth2-2.swip.net (130.244.52.110)  36.748 ms  36.829 ms
 9  kst-spe-2.tengigabiteth3-4.swip.net (130.244.206.134)  36.711 ms  36.261 ms  36.060 ms
10  mail.tele2.se (212.247.156.1)  47.138 ms  55.964 ms  35.417 ms
[/FONT]

---

### Post by enz1m3 on 2009-08-22
Ok, so it's no probable it's gnome proxy settings because usually when you set those, it affects the system also...

Have you tried using thunderbird (just to see if it's evolution-related or general-related)?

---

### Post by lejonmanen on 2009-08-22
I have got it working with Thunderbird on another machíne, running Windows XP, but that is connected to the same router. My proxy setting is "Direct internet connection".

---

### Post by enz1m3 on 2009-08-22
I was talking about thunderbird but on that ubuntu machine

---

### Post by lejonmanen on 2009-08-22
Thanks!

I finally got it working. For those who might suffer the same problem: I was doing two things wrong,


[LIST=1]
[*]I used the wrong user name and password
[*]I had to specify to Evolution that it would use port 587, by setting "server" to "mail.tele2.se:587"
[/LIST]

---

### Post by enz1m3 on 2009-08-22
Ok, sorry I couldn't help, but I'm glad you found your way :)

---

### Post by sayantandas on 2009-11-21
Thanks . adding port 587 helped me in sending my messages again. 

But i have run into a problem now. The inline pictures are not sent. Attachments go properly. Even my signature picture does not appear to be sent anymore. it comes with a grey patch in the place of the picture. any suggestions?

---

