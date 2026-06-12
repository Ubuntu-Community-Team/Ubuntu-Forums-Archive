---
title: "Empathy and Google Talk - Network Error"
date: 2009-11-02
forum: General Help
---

### Post by starfunker on 2009-11-02
I've tried to use my Google talk account with Empathy.  I have put in my login and password, but empathy keeps saying 'network error'.  I've tried various things (including using TLS/SSL) but nothing has worked.

Any ideas?

---

### Post by starfunker on 2009-11-02
/bump

Anyone got any ideas?

---

### Post by rhauff on 2009-11-02
Same here.  I have never used Empathy before, so created a new Jabber account, but get only "Network Error".

I am using a WEP protected wireless connection, and whatever default firewall is.  Have not checked it yet.

---

### Post by starfunker on 2009-11-02
Well, I've just got it working.  I deleted the google talk account from empathy.  I then used my google talk id and password under the Jabber option instead, with the 'reuse an existing account' option ticked.

Seems to be working fine, which is strange.

---

### Post by dy-namo on 2009-11-15
I'm having the same problem as well. I've tries everything too. This blows man.

---

### Post by mariusbutuc on 2009-11-16
I also had this problem and I "fixed" it by filling in (correctly) my login ID as *username***@gmail.com** instead of just *username*. 

That's what worked for me.

---

### Post by ariel on 2009-11-16
upstream bug.

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/477233](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/477233)

---

### Post by gramoun_kal on 2009-11-19
Solution:

[LIST]
[*]Edit > Accounts
[*]Select google talk account
[*]Open "Advanced"
[*]Fill in "talk.google.com" in the field "Server"
[*]Click Apply
[/LIST]

---

### Post by RichardLaurenson on 2009-12-01
would be good if this be marked as SOLVED...

 @gramoun_kal
 Thanks for the info.

---

### Post by fatbuttlarry on 2010-01-13
Here's a link to the bugzilla report:
[https://bugzilla.gnome.org/show_bug.cgi?id=601089]("https://bugzilla.gnome.org/show_bug.cgi?id=601089")

For those familiar with obtaining gabble debug logs please add them to the bugzilla report as it may help resolve this issue quicker.

-Tres

---

### Post by eddieandmags on 2010-02-07
I had the same issues with gtalk and empathy. I figured out that SSL/TSL protection has to be clicked under advanced as well as use old. This worked for me

---

### Post by Dngrsone on 2010-02-11
So, in conclusion-- click all the boxes, make sure your username is *username@gmail.com* (that is, use your gmail address, don't just enter the example given) and set the server to **talk.google.com**.

Thank you all for your help.

---

### Post by AndyCooll on 2010-03-22
My experience has been that you just need your login id and password. And that you should not have "talk.google.com" under advanced > server. That should be left blank.

When I imported my settings from Pidgin, talk.google.com was automatically imported too and I couldn't connect. It took me ages to figure out that no override server details were needed.

Leave port 5222 in though.

:cool:

---

### Post by afrodeity on 2010-03-27
Is there a testbot or some number I can call to test my empathy setup?

---

### Post by create.vibe on 2010-05-25
ya, I deleted my Google talk account, then I readded it but this time I selected Jabber instead of Google Talk.  I changed the Server field under Advanced to the google server, talk.google.com, used my full email as username with my password, and I left all the SSL options unticked.  It set up just fine and seems to be stable.  I guess there's a problem with the pre-set Google Talk setting in empathy.

I'm using 10.04

---

### Post by zuzuag on 2010-05-28
[LEFT]Hi, all bro...
Now! i am using the ubuntu 10.04,
I seem this error.
when i read this post, i tried.
but i can't...really i can't.
please, help me.
[/LEFT]

---

### Post by hannah187 on 2010-06-14
Got same issues here. I have fresh installed Ubuntu 10.04. Yeah empathy does not connect to Google Talk. Network error is what I get.

---

### Post by w4rr3n on 2010-07-05
I've tried all of the suggestions in this thread, but I'm still receiving a "Network Error". The maddening thing is that it worked for 24 hours, then after a reboot it would not connect. All my other protocols connect and are stable.

Any other thoughts?

-Thanks

*edit*
Problem solved. It was an issue with my IPblock list. I noticed a Google IP being blocked repeatedly after an attempted connection. I whitelisted the IP and now it is up and running...  and I feel rather silly.

---

### Post by ceerow on 2010-09-13
but I still have that problem with yahoo and ms
NETWORK ERROR.. any help?

---

### Post by Orange Kingdom on 2011-06-15
network error on icq (again)

---

### Post by MarjaE on 2011-06-17
> **gramoun_kal said:**
> Solution:

[LIST]
[*]Edit > Accounts
[*]Select google talk account
[*]Open "Advanced"
[*]Fill in "talk.google.com" in the field "Server"
[*]Click Apply
[/LIST]


This solution does not work in 11.04. There is no longer an "Advanced" menu to open. Can we please mark this as "no longer solved"?

---

### Post by payxystaxna on 2012-03-13
> **MarjaE said:**
> This solution does not work in 11.04. There is no longer an "Advanced" menu to open. Can we please mark this as "no longer solved"

I am also having trouble when using Google Talk account on Oneiric, due to the advanced menu no longer being available.

---

### Post by wijit on 2012-06-01
Despite the thread was tagged as SOLVED, I still have the problem. I tried both google talk and jabber accounts but they resulted the same. I prefer to use Empathy than Google Talk since Empathy not only can text/video chat but also file transfer and desktop share. Would someone guide me out of the problem?

---

### Post by CharlesA on 2012-06-01
> **wijit said:**
> Despite the thread was tagged as SOLVED, I still have the problem. I tried both google talk and jabber accounts but they resulted the same. I prefer to use Empathy than Google Talk since Empathy not only can text/video chat but also file transfer and desktop share. Would someone guide me out of the problem?
Create a new thread, this one is going back to sleep...

---

