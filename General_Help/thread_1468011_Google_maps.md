---
title: "Google maps"
date: 2010-05-01
forum: General Help
---

### Post by valvegrid on 2010-05-01
Here's an interesting problem. Here in the UK I use google.co.uk, when I try and use google maps on the UK site it doesn't work, you enter an address and nothing happens, but when I use google.com the American site it all works fine using the same browser, Firefox. 

All the other browsers work fine, Opera, Chromium using the .co.uk site.

It all seemed to go wrong with the latest update of Java, but I can't imagine that's the problem if it's working on the .com site and not the .co.uk site.

It's obviously not a major problem, it more like one of these little itches you get and can't seemed to find any relief :)

---

### Post by valvegrid on 2010-05-01
I'll mark as solved. If it helps anyone else I cleared the cookies from the google folder in Edit>Preferences and all has gone back to normal. It must have been a duff cookie somewhere :oops:

---

### Post by graemev on 2010-05-02
> **valvegrid said:**
> I'll mark as solved. If it helps anyone else I cleared the cookies from the google folder in Edit>Preferences and all has gone back to normal. It must have been a duff cookie somewhere :oops:

Don't be embarrassed. I've hit exactly this problem. I ran firefox --safe-mode and all worked file. I tired disabling all plugins , no joy ...then reset all prefs to default . Google maps started working ... just now I realised they ONLY work for maps.google.com ... not for maps.google.co.uk  .... so in the light of your note , I'll check what cookies I have for .co.uk

... I had 1 cookie for maps.google.co.uk I deleted it restarted firefox ... same behaviour maps.google.com work fine, maps.google.co.uk fails (it none of the buttons work)

---

### Post by graemev on 2010-05-02
So I just did this... got a link for 'pointing at the top of big ben:

Given this link:

[http://maps.google.com/maps?f=q&source=s_q&hl=en&geocode=&q=big+ben&sll=51.369624,-0.822259&sspn=0.009257,0.018089&ie=UTF8&hq=Big+Ben&hnear=Big+Ben,+Westminster,+London,+UK&ll=51.499026,-0.126665&spn=0.004615,0.012789&t=h&z=17](http://maps.google.com/maps?f=q&source=s_q&hl=en&geocode=&q=big+ben&sll=51.369624,-0.822259&sspn=0.009257,0.018089&ie=UTF8&hq=Big+Ben&hnear=Big+Ben,+Westminster,+London,+UK&ll=51.499026,-0.126665&spn=0.004615,0.012789&t=h&z=17)


Hand edit it to get:

[http://maps.google.co.uk/maps?f=q&source=s_q&hl=en&geocode=&q=big+ben&sll=51.369624,-0.822259&sspn=0.009257,0.018089&ie=UTF8&hq=Big+Ben&hnear=Big+Ben,+Westminster,+London,+UK&ll=51.499026,-0.126665&spn=0.004615,0.012789&t=h&z=17](http://maps.google.co.uk/maps?f=q&source=s_q&hl=en&geocode=&q=big+ben&sll=51.369624,-0.822259&sspn=0.009257,0.018089&ie=UTF8&hq=Big+Ben&hnear=Big+Ben,+Westminster,+London,+UK&ll=51.499026,-0.126665&spn=0.004615,0.012789&t=h&z=17)






Open two tabs (.com and .co.uk)

They are totally different   ... checking again I see I have a cookie for google.co.uk
called PREF   ... so I wonder if some pref has got set which i breaking maps.google.co.uk

See attached files ...only 1st 15k (site limits) less thane one line co.uk was 172K .com was 224k

---

### Post by graemev on 2010-05-02
Well it WAS a cookie of soem sort ... removed one at time .,.. go joy ... gave up and removed all the ones for site google.co.uk  ...this fixed it , maps.google.co.uk now works.

FYI I'll attach the list of cookies I had JUST before it got fixed:

---

