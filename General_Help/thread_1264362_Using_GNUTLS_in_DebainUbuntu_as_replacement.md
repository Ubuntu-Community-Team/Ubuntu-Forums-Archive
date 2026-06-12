---
title: "Using GNUTLS in Debain/Ubuntu as replacement"
date: 2009-09-12
forum: General Help
---

### Post by chrroessner on 2009-09-12
Hi,

first of all, I am not sure where to go with my question, so I decided to put it under General Help.

I am using Ubuntu since Dapper and I like it really very much! Unfortunately some pieces of software do not use openssl or they have been ported to gnutls.

1.) Please could somebody answer in detail, why openssl not to be used? If licensing, where are the passages that do not match with gpl?

2.) I am using openldap for example and there a working openssl is absolutely important. I have read in "OpenLDAP - Das Praxisbuch", a german title, that neither the authors of the book nor the developers from openldap do recommend using gnutls, because its design is heavily broken. There was a large thread in February 2008, so I asked the core developer himself, Howard Chu.

```

> Hi Howard,
>
> excuse me please, if I write directly. I guess you have much work and I
> do not want to grab your time.
>
> I am an Ubuntu user and as you surely know, this distribution is using
> parts from Debian. So, as from what you wrote gnutls is a bad idea. And
> I do have much problems and also some bug reports are open on that
> topic. So I thought I asked the core developer of openldap, if openssl
> _really_ is an license issue and if so, why? Is there no way to clear
> this problem?
>
> I am afraid, Ubuntu and Debian are going to port nearly anything to use
> gnutls (mysql, freeradius, ...) and I think this would be a dramatically
> error. So I hope to find somebody, who could tell about the main
> problem.
>
> If openldap is allowed to use openssl, I would report your answer to
> this email in the bug tracker with the hope of changing the openldap
> package back to original.
>
> Thanks really, really for an answer in advance.

---
For mysql and freeradius I am not quite sure if my statement was correct!
---

Sorry, but you are asking the wrong person. The OpenLDAP Project fully 
supports OpenSSL, the license issue is not of our making. It's completely a 
Debian / Ubuntu policy issue; they claim that only GPL licensed software is 
allowed (even though they obviously are still shipping OpenSSL and other 
non-GPL'd software) in their distribution.

Also, we're just caught in the middle; this is a conversation for the Debian 
and OpenSSL people, no one in the OpenLDAP Project has any power to resolve it.

```

So as of my opinion: Could somebody explain that to me? I mean: It really does not make sense to port working good software from opennssl to a broken gnutls library. With much respect to the gnutls people: You are surely doing open source and this is great, but if the result is not usable, ...

So my main problem here is: If using Ubuntu with LTS, instead of i.e. Red Hat or SLES, how can I use a distribution that starts breaking main important server packages?

I need to say that I am from Germany and it might sound some kind of harder, who I write, because my English is more technical than eh? yes. So this shall not be an aggression against anybody.

Hope somebody reads it and liks to discuss this.

Christian

---

