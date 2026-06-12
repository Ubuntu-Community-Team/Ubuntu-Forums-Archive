---
title: "Evolution has send problems"
date: 2010-12-04
forum: General Help
---

### Post by 99_rover on 2010-12-04
Hi Folks

Like some others I am having a frustrating time trying to get my email to work in Ontario using Bell Sympatico as a supplier

Up until recently I was running Thunderbird and all was working fine - then it suddenly stopped allowing send - I got the dreaded SMTP timeout

Tried everything I could find in posts all over the forums - no luck. Bell was no help - unless you use Windows they really don't (can't) help.

Went back to Evolution - and hurray it worked fine - had to start it out of the terminal - but hey to get email anything was good.

Today - suddenly (with no upgrade - that stopped sending as well. Once again tried just about every combination on the SMTP send server that I can think of - no luck - incoming works fine

Has anyone got a tried and true means of beating this - I REALLY don't want to have to reload windows..........

Rover

---

### Post by drpjkurian on 2010-12-05
hi try the instruction mentioned in the #5 of the[ post]("http://http://ubuntuforums.org/showthread.php?t=1233537")

---

### Post by 99_rover on 2010-12-05
Sorry - I have no idea to what you are referring

Rover

---

### Post by 99_rover on 2010-12-05
Here is what I am trying (Evolution)

Receiving 
server :  pophm.sympatico.ca
Port (default)
U/N:  email
Security: SSL
Authentication: password (checked)

Sending
server : smtphm.sympatico.ca (was using smtp8 when it failed but this now does not work either
port : tried default, 25, 587
authentication - tried check and uncheck
security - tried SSL, TLS, none
authentication tried none, PLAIN, LOGIN

Interestingly telnet smtphm.sympatico.ca 25 sends me to ----

Connected to smtp.bc.hotmail.com.
Escape character is '^]'.
220 BLU0-SMTP58.blu0.hotmail.com Microsoft ESMTP MAIL Service, Version: 6.0.3790.4675 ready at  Sun, 5 Dec 2010 07:28:06 -0800

not sure why......

---

### Post by HermanAB on 2010-12-05
Uhmmmm, the default SSMTP port is 465.

---

### Post by 99_rover on 2010-12-05
Hi Herman

Tried 465 as well - I keep getting a timeout on send

Rover

---

### Post by drpjkurian on 2010-12-05
sorry mate
the link is [http://ubuntuforums.org/showthread.php?t=1233537](http://ubuntuforums.org/showthread.php?t=1233537).

try an another one
[http://ubuntuforums.org/showthread.php?t=77339](http://ubuntuforums.org/showthread.php?t=77339)

---

### Post by HermanAB on 2010-12-05
OK, use telnet to debug your network issues.  For example:
$ telnet servername 465

You should get the server banner.  If not, check your firewalls and routers.

---

### Post by 99_rover on 2010-12-09
Thanks for the responses Kurian and Herman

Telnet is no help shows a hotmail server in another province - no indication if that is right or not

Kurian tried the links you show and it seems as though everyone has a different solution - none of which are currently working for me

So far the only thing that has worked for sending email is dust my ancient and dearly loved celeron box off and run Outlook under *shudder* Windows XP
This actually works for both send and receive using the standard Bell settings

However would love to get this to work under Linux and Evo

Rover

---

