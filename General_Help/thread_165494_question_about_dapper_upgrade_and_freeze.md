---
title: "question about dapper upgrade and freeze"
date: 2006-04-24
forum: General Help
---

### Post by yotama9 on 2006-04-24
hello

I've been usin ubuntu (the gnome version) for some time know, and after I have upgrade it to dapper I've encountered the freezing problem.

so I've decided to install the kubuntu version (partly becouse my ubuntu CD isn't with me anymore and I wanted to test something alse)

my question is that:

eventually the dapper upgrade will be released, is there any chance I'll be able to upgrade it without the tricky part (I.E. the one that couses all the freezing)?

does any one knows what couse the freezing?

thanks

---

### Post by gingermark on 2006-04-24
I don't know what caused your upgrade to freeze, maybe you could give more info so someone can help in that respect.

As far as upgrading from Kubuntu is concerned, if you plan to upgrade from Breezy my advice is to ensure the kubuntu-desktop metapackage is installed, and to "sudo apt-get dist-upgrade" rather then a normal upgrade.

If you are referring to upgrading from Dapper Beta to the final release version, I'd still advise a dist-upgrade, although the upgrade will be far less severe.

But as I say, it's difficult to answer your question, as I don't know what caused your upgrade to freeze. At what part of the upgrade did it stop? Did your sources.list file contain only Dapper repositories, or were there some Breezy ones still there?

If you describe the steps you went through to upgrade, that might help to diagnose the problem.

---

### Post by yotama9 on 2006-04-25
the upgrade process itself has no problem. the freezing acure from time time while working with dapper.

I havn't notice what couse the system to freeze but it got it's sickness once it happen every time I used gnome wifi manager

other time while using OO

sometimes everytime I loged into KDE 

and so on...
All I can tell is that the issue is known and there is a bug report about it

the system itself is LG laptop (LE 50) with ralink wifi card, 256 MB of RAM fujitsu hard drive and ATI display card (200M)

---

