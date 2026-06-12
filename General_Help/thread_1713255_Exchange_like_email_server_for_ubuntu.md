---
title: "Exchange like email server for ubuntu?"
date: 2011-03-23
forum: General Help
---

### Post by wwarsin on 2011-03-23
I am currently taking a Linux+ class, and I am assigned to a group that has to find/install/setup/demo a working Email server that is compatible with outlook and has the same functions as Microsoft Exchange.

Our group cannot find any mail servers that would suit our needs, (it has to be free).

Is there any? Any help would be very aprecciated!


Thanks

---

### Post by blueridgedog on 2011-03-23
Zimpbra?

[http://en.wikipedia.org/wiki/Category:Free_groupware](http://en.wikipedia.org/wiki/Category:Free_groupware)

Also, SOGo...article in January 2011 Linux Journal...[http://www.linuxjournal.com/article/10894](http://www.linuxjournal.com/article/10894)

[http://en.wikipedia.org/wiki/SOGo](http://en.wikipedia.org/wiki/SOGo)

What you are looking for is called "groupware".

---

### Post by kseise on 2011-03-23
Open-Xchange is probably what you are looking for.  [http://www.open-xchange.com/](http://www.open-xchange.com/)

---

### Post by wwarsin on 2011-03-30
thanks for the replies, we had originally looked at zimbra, but we couldn't get it to install after looking at their site more closely we found that they don't support ubuntu 10.10 x32. We are going to try it on suse.

We *did* see open-xchange but didn't look to deep because it looked like you had to pay, now i see they have a "Community download" link that we didn't see on their site.

I think we're going to check both out... 

I would have thought there would be more free exchange like email servers available in/for linux

---

### Post by SeijiSensei on 2011-03-30
> **wwarsin said:**
> I would have thought there would be more free exchange like email servers available in/for linux

Exchange is a highly proprietary system.  It and Active Directory are the two principal means by which Microsoft maintains its presence in the server room at lots of businesses.  There is no comparable open-source product, though I hear Zimbra comes closest.  Novell Groupwise ran on Linux servers, I believe, but that's quickly becoming a dead-end with Novell's imminent sale to Attachmate.

If you have an Exchange server available for study, see if you can identify the services it provides, then see what the alternatives are in the open world.  (Alternatively you could use Microsoft marketing materials to do a comparison.)  Some functions are pretty obviously replaceable, like SMTP and IMAP for email.  Some are a bit harder to reproduce like calendaring.  Things like workflow management and the like are even less likely to be replaced easily by open-source products.

You also need to consider how Exchange integrates with Active Directory.  It might also have some hooks to Sharepoint and other Microsoft technologies that are pervasive in MS shops.

---

