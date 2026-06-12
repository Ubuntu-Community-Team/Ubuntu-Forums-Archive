---
title: "Is there a way to log all text messages in our internal network?"
date: 2012-03-25
forum: General Help
---

### Post by greavette on 2012-03-25
Hello,

My 10 year old daughter wants to buy an ipod touch to text with her friends.  We'd like to teach her how to text responsibly and monitor what's being said.  We're not doing this surreptitiously...we've told her what we plan on doing.  Is there a way to have all text messages pass through something (a server) that will log all texts before it leaves/arrives through our router?

We do use a Threat Managment Router (Untangle) as our gateway to the internet.  This allows me to shutdown various types of applications getting access to the internet, but I'm not aware how to allow an application out and record what's being said.

I'm curious if anyone out there has a solution that would work for us.

Thank you.

---

### Post by dino99 on 2012-03-25
into synaptic, look at : nanny & zeitgeist

[http://www.google.fr/#hl=fr&sugexp=llsin&gs_nf=1&cp=22&gs_id=5&xhr=t&q=ubuntu+spy+logger+free&pf=p&output=search&sclient=psy-ab&oq=ubuntu+spy+logger+free&aq=&aqi=&aql=&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=9e125737c6db2567&biw=1297&bih=860](http://www.google.fr/#hl=fr&sugexp=llsin&gs_nf=1&cp=22&gs_id=5&xhr=t&q=ubuntu+spy+logger+free&pf=p&output=search&sclient=psy-ab&oq=ubuntu+spy+logger+free&aq=&aqi=&aql=&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=9e125737c6db2567&biw=1297&bih=860)

---

### Post by collisionystm on 2012-03-25
> **greavette said:**
> Hello,

My 10 year old daughter wants to buy an ipod touch to text with her friends.  We'd like to teach her how to text responsibly and monitor what's being said.  We're not doing this surreptitiously...we've told her what we plan on doing.  Is there a way to have all text messages pass through something (a server) that will log all texts before it leaves/arrives through our router?

We do use a Threat Managment Router (Untangle) as our gateway to the internet.  This allows me to shutdown various types of applications getting access to the internet, but I'm not aware how to allow an application out and record what's being said.

I'm curious if anyone out there has a solution that would work for us.

Thank you.


Just to be clear about the iPhone or any phone in general. Text messages do not go over your wifi unless she will be using iMessage or something similar.

---

### Post by greavette on 2012-03-25
Hello,

She's a little young for a phone (in my opinion) which is why we're allowing her to buy an ipod touch instead which would pass through wifi to our router.

I will look into nanny and zeitgeist, thank you for the suggestions.

If anyone else has solutions they think would work for me, please let me know.

Thank you.

---

### Post by CharlesA on 2012-03-25
Wireshark would capture everything set on the network, but the captured data is shown "raw" without any formatting.

EDIT: A quick googled brought me to this page:
[http://www.pricelessparenting.com/digital-children.aspx](http://www.pricelessparenting.com/digital-children.aspx)

Don't know if that will help or not.

---

### Post by collisionystm on 2012-03-25
I have been seeing mentioning of FireSheep but I believe the touch would send iMessage encrypted.

---

### Post by CharlesA on 2012-03-25
> **collisionystm said:**
> I have been seeing mentioning of FireSheep but I believe the touch would send iMessage encrypted.
Firesheep does the same thing as wireshark doesn't it?

---

### Post by collisionystm on 2012-03-25
> **CharlesA said:**
> Firesheep does the same thing as wireshark doesn't it?

Yeah but I think it gives a more simplified look to everything...

Not to sure though :p

---

### Post by CharlesA on 2012-03-25
> **collisionystm said:**
> Yeah but I think it gives a more simplified look to everything...

Not to sure though :p
Ah. I've not bothered to use it.

I mostly use wireshark.

---

### Post by greavette on 2012-03-25
Great advice!  Thanks for the link to priceless parenting.  I've used wireshark in the past, but never thought of it for this purpose.  I'll give that a try.

Thanks for the replies and links everyone.  Very much appreciated.

---

