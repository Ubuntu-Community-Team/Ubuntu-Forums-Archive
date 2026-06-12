---
title: "What are the differences between all these versions?"
date: 2011-12-25
forum: General Help
---

### Post by houmank on 2011-12-25
Hi,

I am new to Ubuntu and like to use it as Server on Amazon Ec2.

I just wonder what the differences between all these versions are?

Ubuntu 11.10 (Oneiric Ocelot)
Ubuntu 11.04 (Natty Narwhal)
Ubuntu 10.10 (Maverick Meerkat)
Ubuntu 10.04.3 LTS (Lucid Lynx)
Ubuntu 8.04.4 LTS (Hardy Heron)

How do I know which one to choose?
Many Thanks,
Houman

---

### Post by West201 on 2011-12-25
> **houmank said:**
> Hi,





How do I know which one to choose?
Many Thanks,
Houman

Every six months Ubuntu releases a new version with upgrades & fixes. 

Re: How do I know which one to choose? 
If you have time burn one in a USB and try each one at time. 

I personally think 10.10 is the most stable.

---

### Post by houmank on 2011-12-25
Thanks for your quick answer. So is it not like in Windows, where latest version is the recommended way?

But surely they must have fixed some issues of Maverick in Natty etc? Or doesn't it work like that? :)

---

### Post by MG&amp;TL on 2011-12-25
> **houmank said:**
> Thanks for your quick answer. So is it not like in Windows, where latest version is the recommended way?

But surely they must have fixed some issues of Maverick in Natty etc? Or doesn't it work like that? :)

Yes. 

Every 2 years, we release an LTS which has three years' upgrades/support. Other releases (every six months)have shorter support times, but have more newer, more experimental software.

recent LTS:

(12.04) (currently in development, not suitable for production use)
10.04 LTS
8.04

You realise that the server is 'headless' and won't have buttons, etc. Only a command prompt.

Btw, with a few exceptions, ubuntu itself doesn't make the software. We take upstream open-source stuff and package it for our system. So updates are from upstream, not ubuntu. Although we may tweak something for ubuntu.

---

### Post by BC59 on 2011-12-25
> **houmank said:**
> Hi,

I am new to Ubuntu and like to use it as Server on Amazon Ec2.

I just wonder what the differences between all these versions are?

Ubuntu 11.10 (Oneiric Ocelot)
Ubuntu 11.04 (Natty Narwhal)
Ubuntu 10.10 (Maverick Meerkat)
Ubuntu 10.04.3 LTS (Lucid Lynx)
Ubuntu 8.04.4 LTS (Hardy Heron)

How do I know which one to choose?
Many Thanks,
Houman

It's very simple. Ubuntu 11.10 is the latest release. Use it. The others are the older versions, just like Windows 7 and Windows Vista. Always choose the last version.

---

### Post by MG&amp;TL on 2011-12-25
> **BC59 said:**
> It's very simple. Ubuntu 11.10 is the latest release. Use it. The others are the older versions, just like Windows 7 and Windows Vista. Always choose the last version.

...as you can see, it's opinionated. LTS is *supposed* to be more stable. But sometimes it's not.

---

### Post by West201 on 2011-12-25
> **houmank said:**
> Thanks for your quick answer. So is it not like in Windows, where latest version is the recommended way?

But surely they must have fixed some issues of Maverick in Natty etc? Or doesn't it work like that? :)

Each release has it's own tastes, but keep in mind Maverick will be supported until April 2012. 

It also depends on your hardware, if it's fairly recent then I would go with a recent Ubuntu release. An older computer with an integrated video card might have trouble running Ubuntu 11.10.

Here is a wikipedia page that discusses the Ubuntu versions and they're support. 
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by ofnuts on 2011-12-25
> **MG&TL said:**
> ...as you can see, it's opinionated. LTS is *supposed* to be more stable. But sometimes it's not.LTS also means that you will have fixes in the next several years. With the other ones, you may have to upgrade to fix problems, which may require to upgrade your server software, etc...

---

### Post by houmank on 2011-12-25
Thank you all for your replies.

Since I need this only as a server for production software, stability and support is the most important thing for me.  I wont even have a UI, so I don't mind video drivers (Logging in through SSH)

This is the list of Ubuntu's to pick for Amazon EC2 Cloud.
[http://alestic.com/](http://alestic.com/)

I think I will go with Ubuntu 10.04 LTS Lucid.

Please feel free to object and correct me if necessary,
Many Thanks,
Houman

---

### Post by The Cog on 2011-12-25
That makes a lot of sense. It's for people like yourself who want stability that the LTS versions are made. I believe that 12.04 will be an LTS version though, so you may be wanting to upgrade in 6 months time whether you install 10.04 or 11.10 for now. That makes your choice for now a little harder.

---

