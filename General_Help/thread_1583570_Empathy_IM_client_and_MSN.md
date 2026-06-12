---
title: "Empathy IM client and MSN"
date: 2010-09-28
forum: General Help
---

### Post by Messyhair42 on 2010-09-28
recently my Empathy instant messenger has not been connecting to the MSN protocol. is MSN blocking non-MSN traffic or is this an isolated problem?

---

### Post by PratterFak on 2010-10-16
I just discovered that my MSN is not connecting using Empathy either. I thought it was maybe because I'm on 10.10 now, but if you are on 10.04, then that must not be the case. All my other IMs are working- AIM, Yahoo, Google, etc. It's just MSN that will not connect.

Anyone know a fix for this?

---

### Post by SeanBlader on 2010-10-17
I'm seeing this too on Maverick, fortunately most everyone I know is on some other service, so it's no big loss for me.

---

### Post by FlyingMG on 2010-10-17
I am also having a similar problem: empathy to be connected to MSN, but my contacts just do not receive any messages I am sending....

---

### Post by fbobraga on 2010-10-17
I've experienced similar behavior here - them I installed pidgin :P

---

### Post by FlyingMG on 2010-10-17
I now also installed pidgin and it works again :-)
thx for the tipp ;-)

---

### Post by moteprime on 2010-10-20
I also have this problem today with a MSN account not able to connect with no error messenge, using fresh and updated 10.10 installation.
Triend with pidgin, and it works fine.

---

### Post by meborc on 2010-10-20
it worked yesterday... it fails to work today (on fully updated 10.10)

:(

---

### Post by oyvinst on 2010-10-20
Empathy is unable to connect to my MSN/Live Messenger account here, starting from today.. Using Ubuntu 10.04.

"Network error" immediately appears when enabling MSN account. - bah. How boring is that. All other types of accounts work fine (Jabber, IRC, etc.).

---

### Post by oyvinst on 2010-10-20
> **oyvinst said:**
> Empathy is unable to connect to my MSN/Live Messenger account here, starting from today.. Using Ubuntu 10.04.

"Network error" immediately appears when enabling MSN account. - bah. How boring is that. All other types of accounts work fine (Jabber, IRC, etc.).

I guess Microsoft changed something about the protocol on the server side, and current Empathy (telepathy-butterfly) no longer complies. Probably authentication-related.. *sigh*..

---

### Post by oyvinst on 2010-10-20
Here's the most recent/relevant bug report:
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/663670](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/663670)

If the problem affects you, go to bug and click "Does this bug affect you?".

---

### Post by dumpster25 on 2010-10-20
I've already done it. Thanks for this post

---

### Post by UnterUn on 2010-10-20
Try 'emesene': seems to work fine; almost a exact MSN clone as well (which is always nice)

---

### Post by Steve H on 2010-10-20
Same problem here. It just sits there trying to connect. Started yesterday after I put my laptop into hibernate.

Is it just laptops affected or are all machines having the same problem?

---

### Post by oyvinst on 2010-10-20
> **Steve H said:**
> 
Is it just laptops affected or are all machines having the same problem?

This is not hardware-related. Microsoft probably made some changes to their MSN/Live messenger service which the Empathy client in Ubuntu doesn't handle properly.

---

### Post by oyvinst on 2010-10-20
> **UnterUn said:**
> Try 'emesene': seems to work fine; almost a exact MSN clone as well (which is always nice)

Well, there are many good MSN-only clients available, Emesene being one of them. Empathy is nice when you use 4-5 other IM-services/protocols in addition to MSN.

---

### Post by hvbakel on 2010-10-20
As a workaround (taken from the bug report) type the following in a terminal (tested on Lucid):

```
gksudo gedit /usr/share/pyshared/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py
```

then find the line that reads

```
CONTACTS = ("contacts.msn.com", "?fs=1&id=24000&kv=7&rn=93S9SWWw&tw=0&ver=2.1.6000.1")
```

and change it to

```
CONTACTS = ("contacts.msn.com", "MBI")
```

Save and restart empathy and the MSN connection should work again. Note that this bugfix will probably come soon through the official channels.

---

### Post by PeregrinGo on 2010-10-20
GREAT! This worked for me. Thanks!

> **hvbakel said:**
> As a workaround (taken from the bug report) type the following in a terminal (tested on Lucid):

```
gksudo gedit /usr/share/pyshared/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py
```

then find the line that reads

```
CONTACTS = ("contacts.msn.com", "?fs=1&id=24000&kv=7&rn=93S9SWWw&tw=0&ver=2.1.6000.1")
```

and change it to

```
CONTACTS = ("contacts.msn.com", "MBI")
```

Save and restart empathy and the MSN connection should work again. Note that this bugfix will probably come soon through the official channels.

---

### Post by hackedbellini on 2010-10-20
> **hvbakel said:**
> As a workaround (taken from the bug report) type the following in a terminal (tested on Lucid):

```
gksudo gedit /usr/share/pyshared/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py
```then find the line that reads

```
CONTACTS = ("contacts.msn.com", "?fs=1&id=24000&kv=7&rn=93S9SWWw&tw=0&ver=2.1.6000.1")
```and change it to

```
CONTACTS = ("contacts.msn.com", "MBI")
```Save and restart empathy and the MSN connection should work again. Note that this bugfix will probably come soon through the official channels.

Perfect! Worked like a charm here! (Maverick Meerkat)

---

### Post by onemanclapping on 2010-10-21
PERFECT! Thank you very much!

---

### Post by achilleas.k on 2010-10-21
Thanks hvbakel.
Worked!

---

### Post by Legeril on 2010-10-21
thanks [hvbakel]("http://ubuntuforums.org/member.php?u=44935") your a genius

---

### Post by papibe on 2010-10-21
> > **hvbakel said:**
> As a workaround (taken from the bug report) type the following in a terminal (tested on Lucid):

```
gksudo gedit /usr/share/pyshared/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py
```
...


That file doesn't exist on my system. As a matter of fact, the papyon directory under pyshared does not exist.


Sorry, my mistake, the file is there and this workaround works!
(too many terminals open... oops ;))

---

### Post by Swiftjay on 2010-10-21
Works perfectly fine in marverick 10.10 thanks alot for this fix will do when i get back home as well as work pc.  Although I have to say that emesene program is quite nice b4 I saw this.  But I use aim so it seems pointless having that and this too.

---

### Post by ThePhysician on 2010-10-21
Thanks, this fixed one of my two main issues with Empathy. Now if only somebody would address [my other one]("http://ubuntuforums.org/showthread.php?t=1601936").

---

### Post by hvbakel on 2010-10-21
For the record, the credit for the bugfix goes to kakaroto ([https://bugs.launchpad.net/ubuntu/+source/papyon/+bug/663670/comments/15](https://bugs.launchpad.net/ubuntu/+source/papyon/+bug/663670/comments/15)). I'm just sharing the fix here.

---

### Post by cinnabubbles on 2010-10-21
Thanks A TON!!!

MSN works now, yippee!

---

### Post by sistematico on 2010-10-21
Works!

---

### Post by aceves on 2010-10-21
Thanks, worked for me too!! =D>

Although I going to check emesene...

---

### Post by vipseixas on 2010-10-21
It worked for me!

It's amazing how this Microsoft stuff is weird... It would be so nice if everyone only used GTalk.

---

### Post by cam3roon on 2010-10-21
Worked for me too!! thanks a lot

---

### Post by Alex1331 on 2010-10-21
Thank you! :D

---

### Post by vandirk on 2010-10-21
Yep, Empathy stopped signing into MSN accounts on both the PC and eeePC a day ago. Using ubuntu 10.04.

This fixes it on both. Thanks team!

---

### Post by rdelfin on 2010-10-21
I echo the rest, than you for the valuable help :KS

---

### Post by GeorgePRPE on 2010-10-23
Amazing! It worked like a charm...

> **hvbakel said:**
> As a workaround (taken from the bug report) type the following in a terminal (tested on Lucid):

```
gksudo gedit /usr/share/pyshared/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py
```

then find the line that reads

```
CONTACTS = ("contacts.msn.com", "?fs=1&id=24000&kv=7&rn=93S9SWWw&tw=0&ver=2.1.6000.1")
```

and change it to

```
CONTACTS = ("contacts.msn.com", "MBI")
```

Save and restart empathy and the MSN connection should work again. Note that this bugfix will probably come soon through the official channels.

---

### Post by AffiliateX on 2010-10-23
Ahh good, it works now. Feared I'd have to be stuck on Emesene. You guys are life savers, thanks.

---

### Post by meborc on 2010-10-25
updates fixed it for me ;)

---

### Post by gandaran on 2010-10-25
> **meborc said:**
> updates fixed it for me ;)

the libpurple updates from getdeb repository fixes it.

---

### Post by sean.clarke on 2010-10-25
Is this working for everyone?

MSN functionality was broke (login timed out), I received an update (now running empathy-2.32.0.1-0ubuntu1) and yes, empathy now connects to MSN, however all my "buddies" are offline even though I can see them online with other clients. If I login via pidgin ik kicks empathy offline and I can see my buddies online, shutdown pidgin, reconnect with empathy and everyone is always shown as offline.

I have obviously restarted etc. and still have the problem.

Maverick x64 - fully updated.

Any ideas?

---

### Post by mvynck on 2010-11-05
> **sean.clarke said:**
> Is this working for everyone?

MSN functionality was broke (login timed out), I received an update (now running empathy-2.32.0.1-0ubuntu1) and yes, empathy now connects to MSN, however all my "buddies" are offline even though I can see them online with other clients. If I login via pidgin ik kicks empathy offline and I can see my buddies online, shutdown pidgin, reconnect with empathy and everyone is always shown as offline.

I have obviously restarted etc. and still have the problem.

Maverick x64 - fully updated.

Any ideas?

Having the same problem here...

---

### Post by Steve H on 2010-11-10
Looks like the problem has returned. I've tried removing and installing empathy but still getting "Network Error" with MSN. All other protocols are working fine.

Any ideas?

:confused:

SORTED: Killed the telepaty-butterfly process and activated MSN in Empathy. Signed in fine.

---

### Post by yakinikku on 2010-11-12
> **mvynck said:**
> Having the same problem here...

having the same problem here too

---

### Post by bvanaerde on 2010-11-21
Still nothing... this is getting really annoying.
ICQ is not working either.

---

### Post by RussellEngland on 2010-11-22
The fix worked for me but now its stopped again :(

---

### Post by bvanaerde on 2010-11-22
Weird thing is I'm using 3 MSN accounts at the same time, and only one is not working.

---

### Post by masterpro on 2010-11-22
The problem also returned on my system :(

I Have 10.10 x64 , upgraded from 10.04.

Im using as an alternative the Pidgin.

---

### Post by zonyl on 2010-11-22
+1  MSN is giving me a network error now again.

---

### Post by bonfire89 on 2010-11-23
> **zonyl said:**
> +1  MSN is giving me a network error now again.

Yep, mine has stopped working too :(

---

### Post by Ghilteras on 2010-11-26
same here

---

### Post by Karpah on 2010-11-28
> **Steve H said:**
> SORTED: Killed the telepathy-butterfly process and activated MSN in Empathy. Signed in fine.

This just fixed the problem for me.

---

### Post by zeppfrog on 2010-12-30
:popcorn: That did the trick, thanks for the posting.

---

### Post by denis6902 on 2011-01-30
> **hvbakel said:**
> As a workaround (taken from the bug report) type the following in a terminal (tested on Lucid):

```
gksudo gedit /usr/share/pyshared/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py
```then find the line that reads

```
CONTACTS = ("contacts.msn.com", "?fs=1&id=24000&kv=7&rn=93S9SWWw&tw=0&ver=2.1.6000.1")
```and change it to

```
CONTACTS = ("contacts.msn.com", "MBI")
```Save and restart empathy and the MSN connection should work again. Note that this bugfix will probably come soon through the official channels.

This trick didnt work for me, when it opened the line "CONTACTS = ("contacts.msn.com", "MBI")" was already set, i didnt have to change anything, but still get Network Error :S

---

### Post by astrobob.tk on 2011-02-10
> **hvbakel said:**
> As a workaround (taken from the bug report) type the following in a terminal (tested on Lucid):

```
gksudo gedit /usr/share/pyshared/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py
```then find the line that reads

```
CONTACTS = ("contacts.msn.com", "?fs=1&id=24000&kv=7&rn=93S9SWWw&tw=0&ver=2.1.6000.1")
```and change it to

```
CONTACTS = ("contacts.msn.com", "MBI")
```Save and restart empathy and the MSN connection should work again. Note that this bugfix will probably come soon through the official channels.

I opened the file, but the code you said to change is already changed in my case; the problem persists. It's been happening often lately. It sometimes connects & sometimes doesn't, like now :(

---

### Post by allekirankumar on 2011-04-05
Hello Everyone,

I am new to this forum. I am big fan of Ubuntu. I am using 10.10 from past 3 months. My problem with empathy is i cannot connect to facebook remaining gtalk, yahoo, msn am able to connect. Please can any one help with this. I tried entering [email]username@chat.facebook.com[/email] etc., still i cant... Help me

Thank you

---

### Post by berot3 on 2011-04-26
for me in natty the changes were already made too... i also removed telepath-butterfly, but changed nothing...

i will try pidgin or emsence... 

why is empathy having such problems with MSN?!?



**EDIT:** yep, emesene works just fine

---

