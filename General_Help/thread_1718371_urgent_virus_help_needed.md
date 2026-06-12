---
title: "urgent virus help needed"
date: 2011-03-31
forum: General Help
---

### Post by flipper T on 2011-03-31
someone has sent an email link to a canadian chemist to all of my contacts from my hotmail account. 

nobody has physical access to my laptop but me. i did not send it.

how to fix ?

is the issue with hotmail or ubuntu ? i do not dual boot.

i have changed the passwords to all my email accounts.

---

### Post by TBABill on 2011-03-31
I had that happen with my Yahoo account. It's not your machine that's infected but rather someone either figured out your password or scraped it from a browser session from some machine you had used, even if it wasn't your personal machine (such as checking email from a library or something). I just changed my password to something MUCH more secure and all is well.

---

### Post by flipper T on 2011-03-31
thanks

i have took the nuclear option and deleted the hotmail account.

is that an end to it ?

can i be sure that my laptop is not "infected"

---

### Post by TBABill on 2011-03-31
Your laptop cannot be infected by a Windows virus and I haven't seen reports of any Linux viruses in the wild. If you had a Win virus on the machine it would lie dormant because it cannot execute in a Linux environment. If you're concerned, there are virus scanners within the repositories that you can install and run. But the fact that someone got into your email account via a web-hosted service doesn't at all suggest your machine was directly accessed.

---

### Post by flipper T on 2011-03-31
thx again TBABill

just shocked (and slightly embarrassed) that this has happened.

have had to email all my contacts to apologize...grrr

---

### Post by SeijiSensei on 2011-03-31
> **flipper T said:**
> just shocked (and slightly embarrassed) that this has happened.

I manage closed-subscription mailing lists and have seen this happen before.  My list subscribers got a spam email that was allegedly sent by one of the subscribers.  Someone stole your Hotmail credentials for this scam, so ending your account was definitely the right approach.

That said I've been puzzled about how these accounts are compromised.  As far as I know, they all use HTTPS connections, so your credentials should have been encrypted.  If, for some reason, you use an online mail server and don't see an HTTPS URL in your address bar, you need to use a different provider.

---

### Post by flipper T on 2011-03-31
i think i know how this happened...

like many people, i guess, i have tended to use the same password for many different sites. these details could then be easily taken from non-secure sites and used to attack secure sites such as hotmail...oh hum, live and learn.

will mark as solved, but feel free to add.

---

### Post by jerome1232 on 2011-03-31
> **SeijiSensei said:**
> I manage closed-subscription mailing lists and have seen this happen before.  My list subscribers got a spam email that was allegedly sent by one of the subscribers.  Someone stole your Hotmail credentials for this scam, so ending your account was definitely the right approach.

That said I've been puzzled about how these accounts are compromised.  As far as I know, they all use HTTPS connections, so your credentials should have been encrypted.  If, for some reason, you use an online mail server and don't see an HTTPS URL in your address bar, you need to use a different provider.

DNS Redirection/poisoning to a phishing website that looks just like the real mail server probably. That the most common way I know of to steal account information. Your unknowingly submitting your credentials to the bad guy!

Always make sure the connection is encrypted, I'm pretty sure firefox will trip out if someone is trying to fake an authentic site but doesn't have their certificate. Kind of how it trips out when I browse to my cups server since it doesn't have a valid authorized certificate (see the screenshot)


I highly recommend getting a few security oriented addons for firefox, such as noscript and better privacy.

---

### Post by Brad55 on 2011-03-31
Yea I had this happen to my Gmail about a week ago, and they told me  it was China that hacked my account. My account sent out about 300 e-mails. It had nothing to do with my computer or software it was all done in my Gmail account.

---

### Post by rg4w on 2011-03-31
> **flipper T said:**
> like many people, i guess, i have tended to use the same password for many different sites. these details could then be easily taken from non-secure sites and used to attack secure sites such as hotmail...oh hum, live and learn.
Unfortunately that also means those other accounts that use the same password may also be at risk.

Might be a good time to do a round of password updates across the systems you use.  Probably not a bad idea to do that periodically anyway.

---

### Post by flipper T on 2011-03-31
thx rg4w

i have taken a look at my saved passwords in chrome & changed where needed

---

