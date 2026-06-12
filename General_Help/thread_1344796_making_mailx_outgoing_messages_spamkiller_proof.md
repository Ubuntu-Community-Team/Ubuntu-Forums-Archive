---
title: "making mailx outgoing messages spamkiller proof"
date: 2009-12-03
forum: General Help
---

### Post by yanvolking on 2009-12-03
Hello Community,

I have installed mailx together with exim4 ([B]sudo apt-get install mailx exim4)

I then configured exim 4 to go through my gmail account :

[/B]# dpkg-reconfigure exim4-config 

[LIST]
[*]Choose YES, split configuration into small files 
[*]Choose mail sent by SMARTHOST; received via SMTP or fetchmail 
[*]Type System Mail Name: e.g. company.com 
[*]Type IP Adresses to listen on for incoming SMTP connections: 127.0.0.1 
[*]Leave Other destinations for which mail is accepted blank 
[*]Leave Machines to relay mail for: blank 
[*]Type Machine handling outgoing mail for this host (smarthost): smtp.gmail.com::587 
[*]Choose NO, don't hide local mail name in outgoing mail. 
[*]Chose NO, don't keep number of DNS-queries minimal (Dial-on-Demand).
[/LIST]
then 

Run 
# editor /etc/exim4/passwd.client 
and add the following lines: 

gmail-smtp.l.google.com:yourAccountName@gmail.com:y0uRpaSsw0RD
*.google.com:yourAccountName@gmail.com:y0uRpaSsw0RD
smtp.gmail.com:yourAccountName@gmail.com:y0uRpaSsw0RD

So now in general mailx works to send emails to external e-mail addresses, 
but with certain destination addresses
the messages are blocked by anti spam technology.

Does anyone know of a trick to make mailx outgoing messages immune to most
 anti spam filters?

Thanks

---

### Post by llamabr on 2009-12-03
Some spam filters are blocking your emails because of the ip address that they originate from.  There are commercial services you can buy, but no way to trick other machines.  Places like aol, for example, have always bounced my emails.  I just don't send anything to aol.

---

### Post by dcstar on 2009-12-03
> **yanvolking said:**
> 
..........
So now in general mailx works to send emails to external e-mail addresses, 
but with certain destination addresses
the messages are blocked by anti spam technology.

Does anyone know of a trick to make mailx outgoing messages immune to most
 anti spam filters?


Nothing whatsoever to do with mailx, it is because people block spam from your smarthost destination: gmail.

If you want to avoid that, then don't use gmail as you now have your own SMTP server.

---

### Post by yanvolking on 2009-12-04
Hi David,

Thanks for your very interesting answer.  However, can you tell me how I can find out what is my own SMTP server, and how I can have that reflected in my mailx setup?

Yan

---

