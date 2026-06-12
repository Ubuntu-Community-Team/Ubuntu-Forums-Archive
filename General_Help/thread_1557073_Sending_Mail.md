---
title: "Sending Mail"
date: 2010-08-20
forum: General Help
---

### Post by vanderkerkoff on 2010-08-20
Hi There

I've got an Ubuntu 8.04 server, I have full access, I built it.

I need to send mail to our internal SMTP server from the command line for some scripts.

I need to set the from address in that email to something specific.

Can someone tell me the easiest way to accomplish this please?

Let's pretend I'm a moron :-)

---

### Post by Bachstelze on 2010-08-20
mutt or a simple PHP script using the mail() function.  There are a lot of other ways obviously, but I would probably use one of those two.

---

### Post by vanderkerkoff on 2010-08-20
Hi Bachstelze

When I installed MySQL aptitude installed Exim, an MTA.

I've also got the mail() command or function present on the machine.

So are you saying that I need to use mutt to put together the email, then that will send mail through Exims config?

I really have no idea what is going on here, it seems ridiculously complicated.

In rails I add the smtp host to one file and the rails app can send mail, this is nuts for what I want to do.

---

### Post by vanderkerkoff on 2010-08-20
Ok I'm getting there.

I've configured Exim to act as my MTA, and found out how to put the MTA address into it.

I've also created a ~/.muttrc file and added these lines to it in order to change my From address


set from='valid@email.address'
set use_from=yes

For some reason the mail is still trying to send with the from address being the username I"m logged in with@machinename.  Our MTA is not going to let that through.

Anyone got any ideas what I'm doing wrong here?

---

### Post by vanderkerkoff on 2010-08-20
Ahh. blessed is the IRC chat room.

A wondrous human called scandal helped me out, here's the correct ~/.muttrc file


set from='valid@email.address'
set use_from=yes
set use_envelope_from=yes

Works now.

Thanks Bachstelze

---

