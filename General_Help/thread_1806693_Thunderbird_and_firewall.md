---
title: "Thunderbird and firewall"
date: 2011-07-18
forum: General Help
---

### Post by Gordonisnz on 2011-07-18
Good day.

im using the latest version of thunderbird, & can receive messages ok but cant send.

it just says "sending....." & nothing else. yesterday I left it for over an hour - nothing happens.

I've been advised it may be with my firewall (I do not remember setting one up on this PC - my other Pc broke the last few days ago)..

Q1. How do i know if i have a firewall installed on Ubuntu. 

q2. How do i tell it to allow Thunderbird to send ?

Q3. any other reason why Thunderbird mauy be blocked from sending.

(the server settings on thunderbird are OK )

---

### Post by mcduck on 2011-07-18
1. Unless you have configured a firewall yourself, you don't have one. The default install of Ubuntu has no running services that would listen for incoming network connections, so a firewall isn't necessary and therefore it's not enabled by default.

2. That would depend on what firewall you are using. Still, as pretty much every Linux firewall in the end uses iptables for the actual filtering, you can run "*sudo iptables --list*" to check the current iptables rules.

3. Most likely reason would be wrong settings for outgoing mail server.

---

### Post by sanderj on 2011-07-18
As mcduck says: probably a wrongly filled out SMTP-server.

Or a SMTP-server blocked by your ISP: some ISPs only want you to use their SMTP-server to avoid spamming.

So: which SMTP-server have you filled out? Which port?

---

### Post by Gordonisnz on 2011-07-22
> **sanderj said:**
> As mcduck says: probably a wrongly filled out SMTP-server.

Or a SMTP-server blocked by your ISP: some ISPs only want you to use their SMTP-server to avoid spamming.

So: which SMTP-server have you filled out? Which port?

I'm using the SMTP server of the website i'm emailing for.

eg [EMAIL="username@website.org"]username@website.org[/EMAIL]  / smtp.website.org

NOT the smtp of my ISP.


QUERY :- How will i know if my ISP is blocking my mail ?

I don't think this is the problem - see my other thread.

[http://ubuntuforums.org/showthread.php?t=1810326](http://ubuntuforums.org/showthread.php?t=1810326)

- I create the email

- LOTS of problems sending,  I give up & click the 'send later' option.

- i close down Thunderbird,  Re-open it 

*I DO NOT CHANGE ANY SETTINGS*

- Once open, I tell Thunderbird to send my outgoing mail, & it sends straight away.


I want it to either send mail ALL the time - 24/7,  not "only just after I load Thunderbird"....

Ps im not a spammer - i only need to send 10-20 emails a day (I have 20+ accounts on the one domain...) - But i want to be able to send emails at the time i choose, & not get frustrated.

---

### Post by Gordonisnz on 2011-07-23
AH - I'm getting somewhere :)  - does this mean I have an active firewall, but its corrupted somehow ? 

Could it be interfering with my thunderbird ?

> 
gordon@gordon-desktop:~$ nautilus
gordon@gordon-desktop:~$ iptables -L
FATAL: Error inserting ip_tables (/lib/modules/2.6.32-31-generic/kernel/net/ipv4/netfilter/ip_tables.ko): Operation not permitted
iptables v1.4.4: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
gordon@gordon-desktop:~$ 



off to find google.... - Or log in as root...

---

### Post by Gordonisnz on 2011-07-23
Did iptables -L

and got this :-

> 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
gordon@gordon-desktop:~$ 


---

### Post by mcduck on 2011-07-23
> **Gordonisnz said:**
> Did iptables -L

and got this :-

No firewall, all traffic is allowed, just like I assumed.

Try using the SMTP server for your ISP. It's quite normal that you need to use the server for the ISP that you are connected to at the moment. (Actually I've never even used a ISP that would allow you to do anything else than that :P)

That won't affect what address the mail appears to be sent from.

---

### Post by Gordonisnz on 2011-07-23
How will that help ?

if the SMTP server is wrong - It'll ALWAYS be wrong.

It wouldn't work just when I log in, & then stop later on... ?

---

### Post by mcduck on 2011-07-23
> **Gordonisnz said:**
> How will that help ?

if the SMTP server is wrong - It'll ALWAYS be wrong.

It wouldn't work just when I log in, & then stop later on... ?

It's only used for outgoing mail, and you said you had problems with sending mail. Incoming mail is of course handled using the incoming mail server instead. In your first post you said you can receive mail but can't send any, so it's definitely a issue with outgoing mail server.

---

### Post by Gordonisnz on 2011-07-23
and ??


the outgoing server DOES work (after i log in,) -  but then any new emails, wont work.

if i 'send later', log off, log in & send the emails - the outgoing server DOES work..

---

### Post by sanderj on 2011-07-23
> **Gordonisnz said:**
> 

I don't think this is the problem - see my other thread.

[http://ubuntuforums.org/showthread.php?t=1810326](http://ubuntuforums.org/showthread.php?t=1810326)


Why have you created another thread?

---

### Post by mcduck on 2011-07-23
> **Gordonisnz said:**
> and ??


the outgoing server DOES work (after i log in,) -  but then any new emails, wont work.

if i 'send later', log off, log in & send the emails - the outgoing server DOES work..

Then why you said in the first post that you can't send mail?

Either way, using the ISP's outgoing server would likely help you. It's up to you if you bother to try that or not.

(And I'm not going to jump to other thread to discuss the same problem, it's generally not accepted to post multiple threads about the same problem. that just wastes the time and resources of the people using their own time to help people on these forums)

---

