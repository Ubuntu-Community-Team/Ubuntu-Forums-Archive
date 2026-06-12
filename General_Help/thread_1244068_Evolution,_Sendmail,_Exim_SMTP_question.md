---
title: "Evolution, Sendmail, Exim: SMTP question"
date: 2009-08-19
forum: General Help
---

### Post by funfrank on 2009-08-19
Hi, 

Maybe somebody more experienced with mail servers can answer this question for me.  I've solved my problem, but I don't know why -- other than the fact that I'm one lucky noob.

I have a work email address.  I can access its pop server from home, but I can't access its smtp server from home.  I think this is fairly normal.

I wanted to be able to send email with that address.  I didn't care which smtp server handled it, I only wanted the address to appear intact -- intact as the address given for "reply to", and "sent from".

I use evolution.  I set the outgoing mail server option as sendmail.  I tried to send a message, and it didn't work.  I installed the exim4 package from the repository, did not adjust anything, and lo and behold, my mail was sent.  Can anybody tell me why?  

First question: My perusal of the forums leads me to think that my outgoing mail is somehow being handled through a server on my machine called "localhost".  I thought servers were big computers that sit in a basement.  

Second question: why wouldn't the evolution sendmail option handle this task alone?  Why did it need exim to be installed?  

Final question: what is postfix's role in all of this?  Is exim4 a replacement for postfix?

funfrank

---

### Post by jonobr on 2009-08-19
Sounds to me as if sendmail was not configured to run or handle your email and when yuou install exim the defaults did and ran ok to allow you to send that email

The localhost is just a hostname which is used to define the computer you are working on.

Localhost usually points to a reserved IP address known as the loopback address (127.0.0.1)
This is an internal address on the machine.

So if you disconnect your ethernet card, or cable and ping 127.0.0.1 or localhost its your machine responding using its loopback address its not a server on your machine, and the hostname localhost(127.0.0.1) refers to itself.

A server is any machine that provides a service. Although the idea of server rooms etc invoke thoughts of either big honking machines with two tape spools spinning or hige machines with large flashy lights, a server can be on a very low spec machine.

Where the dusty basement comes in is if your offering a service on your server, and it needs to be dependable, then it needs to have high availbibilty hard ware, software, power supplies and so on as well as air conditioning, proper cabling, I could go on for ever,

But I am typing to you now on a machines thats acting as a server but is way short of that

As for exim4 vs postfix, AFAIK they are just alternatives to sendmail 
like asking whats the difference between bmw x5 and a Volvo XC90

They both are very different but they ultimately do the same thing

---

### Post by funfrank on 2009-08-21
That makes good sense.  My remaining questions then, have more to do with sendmail/exim/postfix.

If localhost is simply an address on my machine, what exactly does sendmail et al. use it for?  Why doesn't the mail go directly out to the internet directly from my mail client.  And, I guess this is the same question, for what reason do we use smtp?  

I was thinking that I would like to configure sendmail so that I could remove exim from my system.  Any advice in that direction would be great.

---

### Post by dcstar on 2009-08-21
> **funfrank said:**
> 
If localhost is simply an address on my machine, what exactly does sendmail et al. use it for?  **Why doesn't the mail go directly out to the internet directly from my mail client.**  And, I guess this is the same question, for what reason do we use smtp?  


Because **you** haven't configured it to do so - a mail client will only do what the users set it up to do.

Just set up Evolution - like everyone else does - to use your ISP's SMTP server.

---

### Post by funfrank on 2009-08-22
I was interested in a different solution.  I don't use my ISP's smtp server.  Besides, I'm interested in how the system works -- i.e. --  if one can connect to the internet, why does one need a mail server to send mail?  I don't think it's possible to configure sendmail/postfix/exim to avoid smtp, my friend. 

My other question still remains.  Any advice regarding how to configure sendmail would be appreciated.  I would like to remove the redundant exim software.  I am only using it because I am relying on its default configuration to send my mail.

---

### Post by jonobr on 2009-08-23
HEllo


Just to reiterate, ISPs get jumpy about users using SMTP and sending emails and in most cases cblock the SMTP port to stop you from sending emails.

However, if your sure that you can,

[Here]("Here") a link on about installing from synaptic and then installation tips.

I havent used sendmail myself in a long time, and you need to be very sure of your firewalling and security/confg when setting stuff like this up.

You may inadvertently become a mail relay or a spammer without knowing it.

When its all setup you can test smtp by using the terminal and commands

like this 

> 
telnet localhost 25 

then when the port opens type

> helo google.com as an example


> mail from:me@here.com
identifies who you are

> rcpt to:you@there.com

Identifies who is receiving the email

> data

enter your text

You arte usually given indication how to terminate the end of the mail.

Usually a period . on a line by itself.

All of the above allows you to send an email from the command line and means you dont need to worry about a gui

---

### Post by amitkrane on 2009-09-05
[SIZE=2][FONT=Times New Roman]I have some questions regarding sendmail...not sure if this discussion is the most appropriate place to be going ahead with it, however I shall ask it out nyways. If there is any other better thread for me to be askign the same, please feel free to let me know.

And my questions, here we go::

I am running Ubuntu 8.04 Hardy Heron LTS Desktop edition. I am trying to configure sendmail as my need is to be able to send mail from the command line.

1] Is the sendmail distribution for the ubuntu version broken by any chance ? I have not come across any forum stating so, but just to be asking as I see a reasonable number of posts discussing relating to the issues in its configuration ?

2] My /etc/hosts file shows up as ::
> 
127.0.0.1 localhost
127.0.1.1 amit-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts and my /etc/hostname shows up as ::
> amit-laptop    {not sure if need to touch this file, for any configuration}

3] I have installed sendmail MTA using the typical approach, namely
[/FONT][/SIZE][SIZE=2][FONT=Times New Roman]> [/FONT][/SIZE][SIZE=2][FONT=Times New Roman]sudo apt-get install sendmail

I also installed mailx utility & tried sending email to myself as 
> echo testing | mail -s Bla [EMAIL="myemail@somewhere.com"]myemail@somewhere.com[/EMAIL][/FONT][/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE] 
 [SIZE=2][FONT=Times New Roman]However there seems to be some issue
I checked /var/log/mail.{info, err, log}& all seem to be pointing to 

[/FONT]>  [FONT=Times New Roman]My unqualified host name (amit-laptop) unknown; sleeping for retry
amit-laptop sm-msp-queue[8027]: unable to qualify my own domain name (amit-laptop) -- using short name[/FONT][/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2][FONT=Times New Roman]Any help and.or pointers are appreciated.. [/FONT][/SIZE] 
 [SIZE=3]
[/SIZE] 
 [SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE]

---

### Post by jobst on 2009-09-06
> **funfrank said:**
> Hi, 
First question: My perusal of the forums leads me to think that my outgoing mail is somehow being handled through a server on my machine called "localhost". I thought servers were big computers that sit in a basement. 
funfrank

You do not need to send through your works SMTP server, just the the REPLY-TO to your work address and people will reply to you correctly. You might want to check with your works SysAdmin whether there is access to the SMTP server, I would think NOT for security reasons. However, you could get a username/password combo to do so. If the SysAdmin allows you to send through the work server you could set the SMARTHOST in the sendmail config file to your companies mailserver.
Before that I would test whether you can actually ¨see it¨ by doing ¨telnet SMTP_HOST 25¨, sometimes ISP´s block access to the outside world for port 25.

> **funfrank said:**
> Hi, 

Second question: why wouldn't the evolution sendmail option handle this task alone?  Why did it need exim to be installed?  
Final question: what is postfix's role in all of this?  Is exim4 a replacement for postfix?

funfrank

Exim, Postfix and sendmail doing all the same thing, they are mail servers and you only need one of them. however, for your laptop to send mail you only need sendmail, but not the server.


jobst

---

