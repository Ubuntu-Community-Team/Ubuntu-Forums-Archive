---
title: "Pidgin and Google account"
date: 2009-07-14
forum: General Help
---

### Post by poisoneggs on 2009-07-14
Hey guys, I know there are a few similar threads but I think this is different...

I have several accounts on Pidgin, and from time to time my Google one would not connect.

The day before yesterday it stopped working completely.

I have tried every variation of the account settings... none of them is working.

And now I removed the password, but when I enable the account, it doesn't even get to the point where it prompts for it.

Sometimes after trying different settings it just tells me that the SSL handshake failed, and then I have to delete the account and start again.

I don't think it's a Pidgin problem since I also tried Empathy and the same thing happens, the Google account just won't connect (and won't even ask for the password).

I don't know what kind of information would be useful here, apart from saying I am running Pidgin 2.5.8 on Ubuntu 9.04.

Thanks in advance

---

### Post by Short__Error on 2009-07-14
Have you tried useing an older version of pidgin?
 and have you checked google to see if they have updated there stuff lately?

---

### Post by Tibuda on 2009-07-14
> **Short__Error said:**
>  and have you checked google to see if they have updated there stuff lately?
I don't think this is the case. Google Talk uses an open standard (XMPP). It's not like MSN and Yahoo, that changes the protocol frequently to ban third-party clients like Pidgin.

---

### Post by Short__Error on 2009-07-14
I did not even think of that, it has been a about a year since i have used google talk.

---

### Post by poisoneggs on 2009-07-14
I was using the Pidgin in the Ubuntu repos, I think it's version 2.5.0.. anyway, I only updated because of this... I thought it might be a bug that a newer version could fix, but the problem remained.

---

### Post by poisoneggs on 2009-07-14
Anyone has any suggestion as to where the problem might be, even if you can't suggest a solution?

---

### Post by ro2nie on 2009-07-15
The problem is pidgin doesn't know your public IP address, and by default thinks your public IP is your private computer's IP (that is if you are connecting from a private network eg: behind a wifi router)

You need to go to:
Tools>Preferences>Network tab>
Then in STUN server:
stun.ekiga.net

A STUN server will provide you with your external public IP every so often, so pidgin will always know about it...

The other thing you can try is entering your public IP in the "Public IP" field. (first uncheck Autodetect public IP) (You may also enter your dyndns domain name here so you don't have this value when your IP changes, that is if your ISP gives you your public IP via DHCP)

Now delete your Gtalk account in pidgin (if you haven't already done so)... Then restart Pidgin, then add a new Gtalk account with these details in the advanced tab:

Force old port 5223
Connect port: 443
Connect server: talk.google.com
file transfer proxies: proxy.jabber.org

Then click accept, and voila!

---

### Post by poisoneggs on 2009-07-15
> **ro2nie said:**
> The problem is pidgin doesn't know your public IP address, and by default thinks your public IP is your private computer's IP (that is if you are connecting from a private network eg: behind a wifi router)

You need to go to:
Tools>Preferences>Network tab>
Then in STUN server:
stun.ekiga.net

A STUN server will provide you with your external public IP every so often, so pidgin will always know about it...

The other thing you can try is entering your public IP in the "Public IP" field. (first uncheck Autodetect public IP) (You may also enter your dyndns domain name here so you don't have this value when your IP changes, that is if your ISP gives you your public IP via DHCP)

Now delete your Gtalk account in pidgin (if you haven't already done so)... Then restart Pidgin, then add a new Gtalk account with these details in the advanced tab:

Force old port 5223
Connect port: 443
Connect server: talk.google.com
file transfer proxies: proxy.jabber.org

Then click accept, and voila!

Oh yeah!!! thank you so much, that worked perfectly!!
Thanks for your help :D

---

### Post by ro2nie on 2009-07-15
> **poisoneggs said:**
> Oh yeah!!! thank you so much, that worked perfectly!!
Thanks for your help :D

Any time... That's what we are here for!

---

### Post by rohitfeb14 on 2009-07-15
any means to use voice chat on ubuntu

---

