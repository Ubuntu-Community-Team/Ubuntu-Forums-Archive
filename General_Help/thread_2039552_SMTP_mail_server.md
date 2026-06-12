---
title: "SMTP mail server"
date: 2012-08-09
forum: General Help
---

### Post by winzip on 2012-08-09
I have mail server userid , password of  a **remote **SMTP mail server. ( 625 port)
I also have mail sender ID.



I want to check whether remote SMTP mail server is working or not.

How do I check   that SMTP  server can send  email to recipients  from my ubuntu box?

I have ubuntu server 10 OS ( no GUI)

---

### Post by HereInOz on 2012-08-09
Check out this site for a simple process to check the response of a remote smtp server.

[http://www.simplescripts.de/smtp-check-port-25-telnet-command.htm](http://www.simplescripts.de/smtp-check-port-25-telnet-command.htm)

---

### Post by winzip on 2012-08-09
> **HereInOz said:**
> Check out this site for a simple process to check the response of a remote smtp server.

[http://www.simplescripts.de/smtp-check-port-25-telnet-command.htm](http://www.simplescripts.de/smtp-check-port-25-telnet-command.htm)

port is 465   ( The site deals with port 25....)

How do I  send email   for port 465?

---

### Post by Cheesemill on 2012-08-09
Just replace 25 with 465 in the initial telnet command.

---

### Post by winzip on 2012-08-10
SMTP   failed  in command line ...

Can you please tell what could be the issue ?

Here I'm trying to connect a  remote SMTP mail server running at 465 port

user@user:~$ telnet [COLOR=Blue]xxx.xxx.x.x[/COLOR] 465
Trying [COLOR=Blue]xxx.xxx.x.x[/COLOR]...
Connected to [COLOR=Blue]xxx.xxx.x.x.[/COLOR]
Escape character is '^]'.

helo [COLOR=Blue]xxx.xxx.x.x[/COLOR]
[COLOR=Red]Connection closed by foreign host.[/COLOR]


(For security reason I have masked the IP)

Can you please tell what is the issue ? I see telnet  is working ...that means SMTP mail server is running

 .....then why  helo command fails ?  Where is the  problem ? How do I troubleshoot ?

---

### Post by albandy on 2012-08-10
> **winzip said:**
> SMTP   failed  in command line ...

Can you please tell what could be the issue ?

Here I'm trying to connect a  remote SMTP mail server running at 465 port

user@user:~$ telnet [COLOR=Blue]xxx.xxx.x.x[/COLOR] 465
Trying [COLOR=Blue]xxx.xxx.x.x[/COLOR]...
Connected to [COLOR=Blue]xxx.xxx.x.x.[/COLOR]
Escape character is '^]'.

helo [COLOR=Blue]xxx.xxx.x.x[/COLOR]
[COLOR=Red]Connection closed by foreign host.[/COLOR]


(For security reason I have masked the IP)

Can you please tell what is the issue ? I see telnet  is working ...that means SMTP mail server is running .....then why  helo command fails ?  Where is the  problem ? How do I troubleshoot ?

As far as I know port 465 is used for secure connections, so you cannot talk in plain text.

---

### Post by Moif_Murphy on 2012-08-10
> **albandy said:**
> As far as I know port 465 is used for secure connections, so you cannot talk in plain text.
 
Correct.
 
More information can be found here:
 
[http://www.astaro.org/astaro-gateway-products/mail-protection-smtp-pop3-antispam-antivirus/30867-7-504-testing-port-465-smtp-ssl-solved.html](http://www.astaro.org/astaro-gateway-products/mail-protection-smtp-pop3-antispam-antivirus/30867-7-504-testing-port-465-smtp-ssl-solved.html)

---

### Post by Toz on 2012-08-10
Threads merged.

---

