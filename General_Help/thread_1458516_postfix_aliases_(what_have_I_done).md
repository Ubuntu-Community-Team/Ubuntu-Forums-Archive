---
title: "postfix aliases (what have I done?)"
date: 2010-04-20
forum: General Help
---

### Post by ambre on 2010-04-20
Hi,

Until yesterday I had a working email server using Postfix and Fetchmail that collected the family's emails from various ISP's and delivered them to the relevant account.

However, I noticed that locally server generated emails (eg. To: [email]root@ytl.lan[/email]) were not being delivered because they were being routed to my default ISP who didn't recognise the address, bounced them and Postfix shreaded them.  Having never seen any such emails since setting up my server, I guess this has been going on since day one.

I found out via Google that I should be using an alias for root and so created the file /etc/aliases and entered postmaster:joe and root:joe, then reloaded Postfix.

Great!  I now receive locally generated emails addressed to root.

Oh dear!  Now any email picked up by fetchmail and routed to joe gets readdressed to joe@localhost and routed out again to my default ISP where it gets bounced and trashed.

What have I done?

Thanks for looking,
Ambre

---

### Post by dcstar on 2010-04-20
> **ambre said:**
> Hi,

Until yesterday I had a working email server using Postfix and Fetchmail that collected the family's emails from various ISP's and delivered them to the relevant account.

However, I noticed that locally server generated emails (eg. To: [email]root@ytl.lan[/email]) were not being delivered because they were being routed to my default ISP who didn't recognise the address, bounced them and Postfix shreaded them.  Having never seen any such emails since setting up my server, I guess this has been going on since day one.

I found out via Google that I should be using an alias for root and so created the file /etc/aliases and entered postmaster:joe and root:joe, then reloaded Postfix.

Great!  I now receive locally generated emails addressed to root.

Oh dear!  Now any email picked up by fetchmail and routed to joe gets readdressed to joe@localhost and routed out again to my default ISP where it gets bounced and trashed.

What have I done?

Thanks for looking,
Ambre

```
sudo dpkg-reconfigure postfix
```

---

### Post by ambre on 2010-04-21
Tried your suggestion David and nothing has changed - external mail is still getting readdressed.

Fetchmail collects email for [email]joe@ISP1.com[/email], [email]joe@ISP2.com[/email], [email]jane@ISP2.com[/email] and [email]joe@ISP3.com[/email] and routes them to either joe or jane's mailbox.

What do I need to do to stop Postfix trying to readdress emails for joe@ISP1 as joe@localhost and routing them back to the relayhost where they get bounced and then trashed by Postfix and just deliver them locally?

Ambre

---

### Post by dcstar on 2010-04-21
> **ambre said:**
> Tried your suggestion David and nothing has changed - external mail is still getting readdressed.

Fetchmail collects email for [email]joe@ISP1.com[/email], [email]joe@ISP2.com[/email], [email]jane@ISP2.com[/email] and [email]joe@ISP3.com[/email] and routes them to either joe or jane's mailbox.

What do I need to do to stop Postfix trying to readdress emails for joe@ISP1 as joe@localhost and routing them back to the relayhost where they get bounced and then trashed by Postfix and just deliver them locally?

Ambre

Check the /etc/postfix/main.cf file and your /etc/hosts file.

---

### Post by ambre on 2010-04-22
The problem is now fixed.

My thanks to David for pointing me in the right direction.

For others reading this thread the solution had nothing to do with aliases.  The clues were there all the time.  The messages that were causing the problem had all been readdressed to joe@localhost.  localhost was not included in 'mydestinations' list.  As soon as I realised this and amended the list everything started working again.

Regards,
Ambre

---

