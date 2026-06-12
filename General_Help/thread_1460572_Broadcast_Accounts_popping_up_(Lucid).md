---
title: "Broadcast Accounts popping up (Lucid)"
date: 2010-04-23
forum: General Help
---

### Post by ICU81-MI? on 2010-04-23
I installed the Lucid Release Candidate today, and for some reason Broadcast Accounts keeps opening itself, even after I've added all the accounts I'm going to. Is this happening with anyone else, and how can I make it stop?

Thanks.

---

### Post by Marco Ceppi on 2010-04-23
This is also happening to me on my station after upgrading. A window is spawned for each account I have in Broadcasts. I believe this has something to do with syncs from Ubuntu One but I'm not entirely sure. Not sure if this is a bug or not I may file a bug report soon about it.

Marco

---

### Post by ICU81-MI? on 2010-04-24
The problem seems to have gone away on its own today... Not sure if it was a system update or what, but I guess it's a non-issue on my end. If I figure out what it was, I'll keep you posted.

---

### Post by Eemeez on 2010-04-29
Also happening to me. Fresh install and all updated.

---

### Post by KRiODOXiS on 2010-05-01
Same thing happennig here any solutions?

---

### Post by Eemeez on 2010-05-02
For me, the problem disappeared after second restart ...

---

### Post by waveslider on 2010-05-03
This is happening to me, too. Fresh installation. Restarted multiple times, but it is still recurring. There are always 3 windows that pop up, despite the fact that I've only added two accounts (Facebook two days ago, and Twitter just a few minutes ago).

Edit: This appears to be recurring on my broadcast accounts update interval - currently every 5 minutes. I wonder if it could be related to some auth issue (although both of my accounts seem to be authenticated just fine).

---

### Post by Marco Ceppi on 2010-05-05
My installation was an in-place upgrade from 9.10 - However after a fresh install this issue went away. I was able to temporarily fix it by going to the accounts window, deleting all accounts, then re-adding them.

---

### Post by ahmader on 2010-09-05
It is happening to me two with two account and popping every now and then after I updated latest system update this week. Restarted once and still going on

---

### Post by daveysan on 2010-09-06
ahmander, Have you changed one of your account passwords? I found the same as you, but in my case it was because I had changed my facebook password a few months back. I don't use Gwibber (though I may start to again) but I am wondering if a recent change to it makes it try to reauthenticate with all the accounts. Just a  thought

---

### Post by eltama on 2010-09-06
It can be related to the change in the authentication method of tweeter. I had the same problem, but after re-authenticating in tweeter it seems to be working fine.

---

### Post by argraff on 2010-09-07
@eltama - I'm confused. What's tweeter?

I am also having this problem. It's really really annoying. I may delete all the accounts and readd them. Will report back.

Edit: Tweeter = Twitter. Sorry, I wasn't being smart, just thought it was another service/program that I hadn't heard of yet!

---

### Post by argraff on 2010-09-07
Ok, for me it was that Twitter needed to be re-authenticated for some reason. Did that, haven't seen anything since. (Fingers crossed.)

---

### Post by daveysan on 2010-09-07
There seems a good chance you are running in to the problem I had - check very carefully you didn't change the password on one of your accounts ...

---

### Post by daveysan on 2010-09-07
argraff - seems our posts crossed in the ether :-)

---

### Post by eltama on 2010-09-08
> **argraff said:**
> @eltama - I'm confused. What's tweeter?

I am also having this problem. It's really really annoying. I may delete all the accounts and readd them. Will report back.

Edit: Tweeter = Twitter. Sorry, I wasn't being smart, just thought it was another service/program that I hadn't heard of yet!

lol sorry, I meant Twitter.
Good to know that it's working fine now.

---

### Post by argraff on 2010-09-08
No popups since re-authenticating with Twitter. I think it's solved for me.

I haven't changed my passwords to the services I use in quite a while, so I'm not sure that was the root of my particular instance, although I'm quite sure that would produce the same result. 

Hope this helps someone!

---

### Post by grj23 on 2010-09-08
Same thing just started to happen to me.  I noticed that my twitter account wasn't authorising for some reason.  So far I've removed the twitter account, and that seems to have fixed it for now.

---

### Post by HughJarse on 2010-09-17
What a heap of junk. Re-authorised twitter, still doing it. This is why I *hate* doing auto updates.
Testing would be nice.

---

### Post by outleradam on 2010-11-10
I just reauthorized and am having the same problem under Maverick.   However, mine will not add the client anymore.  I try and facebook just says Success Authorized, but I have no add button.  So I'm dead in the water now.

---

### Post by vene-ubu on 2011-03-20
Same Here with Ubuntu 10.10:

At login keyring asked for password multiple times.   To solve it I searched forums and followed a suggestion to delete passwords and encrption keys.

After that all got worse.  I keep getting the keyring password window and gwibber is popping this Broadcast account window, no mattter if I remove and readd twitter (I only have twitter).  
UbuntuOne Also had troubles, solved by reentering password.

---

