---
title: "Internet browsers don't load any webpages..?!"
date: 2010-07-26
forum: General Help
---

### Post by The_Eggert on 2010-07-26
Hello :)
I just installed Ubuntu, and the Wifi works just fine - E.g. downloading updates works like a charm ;)
But when I try to access a page in Firefox or Chrome they just keep loading the webpage, but never show me anything :(

For the record, I'm using 10.04 32-bit..

Don't know how must more information to give..But from this, does anyone have an idea, on how to fix it?

---

### Post by P4man on 2010-07-26
Could it be an IPv6 issue with your provider? You could try disabling it.  Have a look here:

[http://www.uluga.ubuntuforums.org/showpost.php?p=9590208&postcount=2](http://www.uluga.ubuntuforums.org/showpost.php?p=9590208&postcount=2)

You can also test if its a DNS issue. Try this in the browser:

[http://74.125.77.104](http://74.125.77.104)

Does it give google homepage ? If so; you have a DNS problem and you could  try using another DNS server. Google's DNS servers are pretty fast and dont give me any problems ever; you can change the settings in the network manager (right click network icon; edit connection). Google DNS servers are 8.8.8.8 and 8.8.4.4.

---

### Post by Lost-Found on 2010-07-26
That's weird - I have the same problem, if i write google in my browser, its +10 secs loading, if i press that links its under 1 sec...

...but I cant figure out the dns settings, I'm on dynamic ip. Could you help me where to put the dns's?

NVM: Did it in etc/resolve... Jesus, I've been hasling with this for 2 days now and that worked.

Can anyone anwser me why this "suddenly" happend though?  had it working for so long, and boom it fell off..

---

### Post by The_Eggert on 2010-07-26
@P4man:
Thanks for the quick answer :)
As soon as I get around to try it, I'll let you know if it works ;)

> **P4man said:**
> Could it be an IPv6 issue with your provider? You could try disabling it.  Have a look here:

[http://www.uluga.ubuntuforums.org/showpost.php?p=9590208&postcount=2](http://www.uluga.ubuntuforums.org/showpost.php?p=9590208&postcount=2)

And just out of couriousity, do I have to do it that way around?
Doesn't it give the same result, by just right-clicking the networking icon, and editing my connections (disabling IPv6) that way around, or what? :)

---

### Post by P4man on 2010-07-26
I dont think you can really disable it there; you can set it to ignore; but AFAIK thats not quite the same. You can also disable IPv6 in firefox (about:config and then ipv6disable or something along those lines) but I honestly dont know how there relate or interact.

---

### Post by The_Eggert on 2010-07-27
> **P4man said:**
> I dont think you can really disable it there; you can set it to ignore; but AFAIK thats not quite the same. You can also disable IPv6 in firefox (about:config and then ipv6disable or something along those lines) but I honestly dont know how there relate or interact.

Thanks, I guess you're right ;)

And FYI, changing the DNS to Googles, and disabling IPv6 (the right way ;)) pretty much worked out for me - There is, however, still some sites I can't access for some reason..But for now, I'm setting it as solved ;)

Thanks for your help :)

---

