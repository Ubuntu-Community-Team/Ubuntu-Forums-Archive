---
title: "Ubuntu. Windows domain. LTSP. Likewise-Open."
date: 2011-03-26
forum: General Help
---

### Post by Roasted on 2011-03-26
I have two Ubuntu servers running LTSP thin clients. They are both Edubuntu 10.10 64 bit. I joined each of them to the domain using Likewise 6 off of the web site. If I log in as myself on the first Ubuntu box, I can select a link to our Windows file server and I just connect instantly. On the other box it asks me to authenticate. I’m wondering why it asks me to authenticate when on the other box I don’t need this.

This doesn’t seem like a big deal, but this is for a lab in a school district. This is certainly going to be obnoxious when you have a ton of students in there. It would be nice if I could get the auto-authenticate thing to work like the other server does. The only catch is, I don’t recall doing *anything* different on either box. Can anybody shed some light?

---

### Post by Roasted on 2011-03-27
After some discussing it with other users, they were suggesting that I need to join the fat client chroot to the domain, as I should look at the fat client chroot as an entirely separate computer from the actual server, even though they are both one. That being said, I looked in /etc/hostname and it was blank. /etc/hosts has a commented line saying "This is a ltsp chroot and this file will be rewritten in boot process of terminal" along with 127.0.0.1 localhost.

That said, do I need to join the fat client chroot to our Windows domain for it to behave the way I like it to? I suppose it makes sense, but I'm just a little curious.

---

