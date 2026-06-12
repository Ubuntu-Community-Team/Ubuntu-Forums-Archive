---
title: "Own mail server marked as Spam"
date: 2012-05-23
forum: General Help
---

### Post by absoord on 2012-05-23
Hey guys.

I've been configuring my mail server those days (Postfix + Dovecot + MySQL + Spamassassin + Mailman), now everything works fine but I'm having trouble with some free mail providers (hotmail, gmail, etc), as they mark all the outgoing traffic from my server as spam.

I've configured SPF and DomainKeys (and it's proved it works!), I have STARTTLS activated, I'm not allowing to send unidentified mail, I've verified my IP is not in BlackLists, neither is my domain, I'm not even sending a large number of mails... the question is... WHY do these servers mark 'legitimate' domains as spam? :-)

I've been trying to research some info about this but there's quite lack... Does anyone know why does this happen and how to get rid of 'default' hotmail/gmail/etc. blacklists?

Thanx!!

---

### Post by galvatron408 on 2012-05-23
what is your domain?

---

### Post by lisati on 2012-05-23
I'm wondering if reverse DNS could be an issue. Have you organized a "proper" reverse DNS or are you still using the generic one provided by your ISP?

---

### Post by bootedguy on 2012-05-23
> **absoord said:**
> 
I've been trying to research some info about this but there's quite lack... Does anyone know why does this happen and how to get rid of 'default' hotmail/gmail/etc. blacklists?

Thanx!!
Your domain/IP has very likely been blacklisted. I had this problem using BlueHost for a distribution list. Solved the problem by sending email via AmazonSES. Took a little work to get it setup, but it is otherwise flawless. Amazon charges very little.

---

### Post by dcstar on 2012-05-24
> **lisati said:**
> I'm wondering if reverse DNS could be an issue. Have you organized a "proper" reverse DNS or are you still using the generic one provided by your ISP?

+1 Many mail systems today don't accept any e-mail from a source without a valid Reverse DNS.

---

### Post by absoord on 2012-05-24
First of all, thank you for your responses :-)

Indeed, I've not set any reverse IP, I'm using the one provided by my ISP. The IPs are in the 85.155.X.Y form, but I wonder what do you mean by a "proper" reverse IP. All those ISP IPs have reverse DNS in the form: 85.155.X.Y.dyn.user.ono.com.

Aditionally, there's an adittional domain set to that IP (A record), and that's the one I'm using to send-receive mails. Could you please explain a little more?

Thanx a lot!

EDITED:

I'm adding some info about how's my system currently setup.

I've purchased a domain, let's suppose domain.es
root@mail:~# host domain.es
domain.es has address 212.7.X.Y
domain.es mail is handled by 0 mail.domain.es.

This IP address appoints to a server in the Netherlands.

root@mail:~# host 212.7.X.Y
Host Y.X.7.212.in-addr.arpa. not found: 3(NXDOMAIN)

And the IP of the machine running the mail server is the already mentioned 85.155.X.Y.

root@mail:~# dig A mail.domain.es +short
85.155.X.Y.

root@mail:~# host 85.155.X.Y
Y.X.155.85.in-addr.arpa domain name pointer 85.155.X.Y.dyn.user.ono.com.

How should it look like to get rid of this problem?

Thanx!!

---

### Post by absoord on 2012-05-24
Bump!

---

### Post by absoord on 2012-05-25
Anyone can help with this? :-/

---

### Post by lisati on 2012-05-25
I notice that your reverse dns seems to suggest a dynamic IP address. There's nothing necessarily bad in that, but in the time I've been running my own email server from home, I've encountered email providers who get nervous about that such things. 

The main problem, as I understand it, is that most email providers use static IP addresses for their public IP address. When they encounter an incoming connection from a dynamic IP address, they figure that it *could* be someone you wouldn't normally expect to be running an email server and whose machine *might* have been compromised by malware. Special emphasis on "could" and "might": they don't necessarily think you're a spammer but instead they want to play it safe.

You might find this article interesting: [http://www.linuxmagic.com/best_practices/check_dynamic_reverse_dns.html](http://www.linuxmagic.com/best_practices/check_dynamic_reverse_dns.html)

---

### Post by galvatron408 on 2012-05-25
ummm, I checked and his domain has been black listed on 2 sites.

---

### Post by lisati on 2012-05-25
> **galvatron408 said:**
> ummm, I checked and his domain has been black listed on 2 sites.

Following on from this thought, here are some sites which can be used to check blacklist entries:
[LIST]
[*][http://www.blacklistalert.org/](http://www.blacklistalert.org/)
[*][http://debouncer.com](http://debouncer.com)
[*][http://whatismyipaddress.com/blacklist-check](http://whatismyipaddress.com/blacklist-check)
[*][http://lisati.homelinux.com/blacklist](http://lisati.homelinux.com/blacklist)
[/LIST]

---

### Post by absoord on 2012-05-25
Thanks again guys for your help!

Even if my reverse DNS seems to be 'dynamic', it's not actually. I'm having this IP address for 4 years and it hasn't changed since then, though my ISP can change it at anytime.

galvatron408 yes, I've checked it too and the reason seems to be what lisati said. Sorbs is one of them, and they've included the whole /16 range in their list... They're marked as 'dynamic' addresses, I tried to write those RBL lists to get removed from them and they replied me they won't because of "incorrect reverse DNS".

Well, I think there's no much more what I can do there... maybe next time I'll install it on a non-home server... :(

---

