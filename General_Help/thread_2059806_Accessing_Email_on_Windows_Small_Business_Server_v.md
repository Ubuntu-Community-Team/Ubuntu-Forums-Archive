---
title: "Accessing Email on Windows Small Business Server via Linux"
date: 2012-09-18
forum: General Help
---

### Post by neu5eeCh on 2012-09-18
Is it possible?

An outfit where my wife works uses Windows Small Business Server. They tell her that the only client that will work is MS Outlook or nothing. (She uses Xubuntu 12.04) . I'm inclined to believe them (knowing Microsoft) but thought I'd ask anyway.

I've tried setting up her E-Mail with Thunderbird and Evolution. It's possible I don't have the correct servers (mail & smtp) names, but it's also possible that WSBS simply refuses to shake hands with any client other than Outlook?  What say you?

---

### Post by dcstar on 2012-09-19
> **VTPoet said:**
> Is it possible?

An outfit where my wife works uses Windows Small Business Server. They tell her that the only client that will work is MS Outlook or nothing. (She uses Xubuntu 12.04) . I'm inclined to believe them (knowing Microsoft) but thought I'd ask anyway.

I've tried setting up her E-Mail with Thunderbird and Evolution. It's possible I don't have the correct servers (mail & smtp) names, but it's also possible that WSBS simply refuses to shake hands with any client other than Outlook?  What say you?

There are hundreds of posts on this issue already. Search them out.

---

### Post by HermanAB on 2012-09-19
Run Outlook on Wine, or set the account to forward everything to a gmail account, then use whatever mail client you want with gmail.

---

### Post by SlugSlug on 2012-09-19
Outlook in wine or access the Outlook Web Access

[https://SBSaddress.com/owa](https://SBSaddress.com/owa) or [https://SBSaddress.com/exchange](https://SBSaddress.com/exchange)

depending on version of SBS

---

### Post by neu5eeCh on 2012-09-19
> **dcstar said:**
> There are hundreds of posts on this issue already. Search them out.

Odd how not a single one turned up with a Google search.

> **HermanAB said:**
> Run Outlook on Wine, or set the account to  forward everything to a gmail account, then use whatever mail client you  want with gmail.

Thanks, that's what I'll tell her to do. 

As for Outlook, neither one of us owns a licensed copy and we're not about to buy a copy to run on Wine (or I would have considered it).

---

### Post by SlugSlug on 2012-09-19
Outlook web access then?

---

