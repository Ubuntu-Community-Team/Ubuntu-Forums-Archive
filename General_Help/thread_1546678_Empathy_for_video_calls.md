---
title: "Empathy for video calls?"
date: 2010-08-05
forum: General Help
---

### Post by bigseb on 2010-08-05
I while back I tried installing Skype form the software centre but for some reason it wouldn't work. Now, with a fresh install of Lucid, I see that Empathy comes pre-installed and allows video chatting. Is it worth setting up a account? Does anyone have experience with Empathy?

---

### Post by chopinhauer on 2010-08-06
> **bigseb said:**
> 
Is it worth setting up a account? Does anyone have experience with Empathy?


Empathy is not yet another IM network, but a multi-protocol client with support for many networks. Therefore you probably already have an account that Empathy can use (GMail account, Facebook, MSN, Yahoo!, AIM).

Voice/video chat works great on the XMPP network (the network used by GMail/GTalk and partially by Facebook), but MSN and Yahoo! should work too (though I wouldn't recommend any of them).

---

### Post by LowSky on 2010-08-06
skype isn't in the software center?????

---

### Post by chopinhauer on 2010-08-06
> **LowSky said:**
> 
skype isn't in the software center?????


You'd have to add the Canonical Partner repository. Add
```
deb http://archive.canonical.com/ubuntu lucid partner
```
in System > Administration > Software Sources.

And if you want a client that doesn't suck (your bandwidth) use Empathy with a nice XMPP account (like the one from Google). You'll be also able to share your desktop with people through Empathy.

---

### Post by bigseb on 2010-08-06
I already have a gmail account, I suppose video chatting is automatically included in that (haven't the foggiest idea). Can one use that account to video chat to, say, yahoo for example?

---

### Post by chopinhauer on 2010-08-06
> **bigseb said:**
> I already have a gmail account, I suppose video chatting is automatically included in that (haven't the foggiest idea). Can one use that account to video chat to, say, yahoo for example?

No, the Yahoo!, MSN, AIM and Skype messengers are closed networks, you can only chat with people within that network.

On the other hand with an XMPP service like GMail you can chat with every other XMPP server in the world (jabber.org for example or all gmx.de users). It's a little bit like the difference between Facebook messages (you need a Facebook account to send/receive) and e-mail (any e-mail service in the world is ok).

If you already have a lot of contacts on one network, you'd be probably obliged to create an account on that network. But if you have a choice, it's better to choose XMPP, since it leaves you more freedom: you don't like your service provider, you change it just like you do with e-mail.

---

### Post by bigseb on 2010-08-07
> **chopinhauer said:**
> No, the Yahoo!, MSN, AIM and Skype messengers are closed networks, you can only chat with people within that network.

On the other hand with an XMPP service like GMail you can chat with every other XMPP server in the world (jabber.org for example or all gmx.de users). It's a little bit like the difference between Facebook messages (you need a Facebook account to send/receive) and e-mail (any e-mail service in the world is ok).

If you already have a lot of contacts on one network, you'd be probably obliged to create an account on that network. But if you have a choice, it's better to choose XMPP, since it leaves you more freedom: you don't like your service provider, you change it just like you do with e-mail.
Very interesting. Had no idea how it worked, good to finally find out. 

OT: I used to use skype to call family in New Zealand but since switching to Ubuntu in February that hasn't been possible any more. I did try installing skype from the software centre but it just wouldn't run :( On the other hand there's no point in messing with Empathy if it can't call skype. Thanks for your help anyway.

---

### Post by davidmohammed on 2010-08-07
are you using 64 bit or 32 bit skype?

64bit needs to be setup slightly differently to get it to work.  See [here]("http://linux.dipin.info/2010/01/how-to-install-skype-on-ubuntu-1004.html") (for both on how to install)

---

### Post by bigseb on 2010-08-11
> **davidmohammed said:**
> are you using 64 bit or 32 bit skype?

64bit needs to be setup slightly differently to get it to work.  See [here]("http://linux.dipin.info/2010/01/how-to-install-skype-on-ubuntu-1004.html") (for both on how to install)
Installed just fine but the sign-in button (and the sign-up button) is blanked out. Cannot log-in :( How do I rectify this?

---

### Post by chopinhauer on 2010-08-11
> **bigseb said:**
> Installed just fine but the sign-in button (and the sign-up button) is blanked out. Cannot log-in :( How do I rectify this?

That is the big problem with Skype: since it is proprietary software, only Skype engineers can really help you. Try asking on [Skype's technical support](http://support.skype.com).

Apart from Google Talk, there is another very good solution for Voice over IP: SIP. It has the advantage of being designed primarily for calling over the Internet.

And since it is an open protocol there are [many providers](http://www.voipproviderslist.com/) all over the world that allow you to place calls on the classical telephone network, usually for very low rates or a flat rate.

And if you are tired of using a headset to call, dedicated hardware is relatively cheap (just a little bit more than a classical wireless phone) and good. For example Siemens Gigaset and Linksys offer both Analog Telephone Adapters to connect your analog phone to the Internet and place calls through SIP and dedicated SIP phones than can use the analog phone line and the Internet indiscriminately: cf. [Voip-info](http://www.voip-info.org/). Smartphones can use SIP too.

In France every DSL provider gives you a modem with an integrated ATA, so you can call most of the world for free and the rest for low rates using your old telephone set. Personally I haven't placed a call from my computer in a very long time.

---

