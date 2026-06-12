---
title: "email refused"
date: 2009-11-18
forum: General Help
---

### Post by jmore9 on 2009-11-18
Hello!

Anyone have any idea why i keep getting the following :

Delivery to the following recipient failed permanently:

    [email]xxxx@xxxxxx.com[/email]

Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the recipient domain. 
 The error that the other server returned was: 550 550 5.7.1 Requested action not taken: message refused (state 18).

I needed to block out the address.

---

### Post by Giblet5 on 2009-11-18
This is most likely due to the recipient server rejecting email that originates from gmail.com.

You can try sending an email to [email]abuse@xxxxx.xxx[/email] and state that you're trying to send legitimate communications to [email]xxxx@xxxxx.xxx[/email] and received a rejection notice.

They'll probably bounce that too.

A lot of businesses block gmail because there are a lot of idiots who use gmail accounts to send spam.

I block entire countries on my email server. There are a lot of idiots in the world.

---

### Post by jmore9 on 2009-11-18
I sent the same test message using thunderbird and have not gotten that error message as yet.

So that must be the reason my message sent from googles gmail site was refused.

Thanks for the info

---

### Post by Giblet5 on 2009-11-18
Do you use the same gmail smtp relay server under tbird?

That is not the default behavior under tbird.....

Say I have an earthlink account and a gmail account. I only configure the earthlink smtp server. I can still send/receive on the gmail account, but the From: header will show earthlink while the Reply-To: header shows gmail.com.

See RFC-822 for details on how this works.

---

