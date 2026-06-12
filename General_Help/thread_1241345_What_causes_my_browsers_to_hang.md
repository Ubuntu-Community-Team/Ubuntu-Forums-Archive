---
title: "What causes my browsers to hang??"
date: 2009-08-15
forum: General Help
---

### Post by 3pinner on 2009-08-15
Its driving me nuts!!!!!!!!!!
doesn't matter if I'm using Firefox or Opera, or trying to download e-mail.
I click on a site or type in a web address, the page starts to load then stops, and hangs........................then loads a couple more pieces...............................and hangs..............again................forever.


Ive disabled IPV6, I'm using opendns, my setup is ubuntu 8.10, through a linksys router, DSL connection my ISP is Verizon. Its been going on for months.
Any ideas/solutions?
Thanks

---

### Post by Mardoct909 on 2009-08-15
Check your home network for issues. If it's good, call up Verizon and ask them about it.

It's not a browser issue.

---

### Post by 3pinner on 2009-08-15
> **Mardoct909 said:**
> Check your home network for issues. If it's good, call up Verizon and ask them about it.

It's not a browser issue.

issues such as?????

Could it be an Ubuntu problem?

---

### Post by blueridgedog on 2009-08-15
Just to test, you could boot off of a liveCD and test the browsing.  

Also, while browsing you could look for errors with the following in a terminal:

```
tail /var/log/messages
```

As a last resort, you could run tcpdump and look at the stream of packets coming to your interface.

---

### Post by 3pinner on 2009-08-20
I am increasingly beginning to think this is more of a verizon issue. many of my neighbors have similar problems.
But I also think there may be an issue with my system not recognizing my eth0 port. I have a wired system, and that is the only network card on the computer, and it works or I would't be posting here.
Any suggestions?

---

### Post by nilarimogard on 2009-08-20
Try this: [http://webupd8.blogspot.com/2009/08/experiencing-choppy-videos-in-firefox.html](http://webupd8.blogspot.com/2009/08/experiencing-choppy-videos-in-firefox.html) and this: [http://webupd8.blogspot.com/2009/07/increase-firefox-3-perormance-by.html](http://webupd8.blogspot.com/2009/07/increase-firefox-3-perormance-by.html)

---

### Post by 3pinner on 2009-08-20
Thank you for the tips. Now I need to see how to apply them to Opera my usual browser.

---

### Post by 3pinner on 2009-08-20
Yep. A verizon issue. I don't know what they did, but using OpenDns and my browser is SMOKIN' !
now if it will only last more than a week..............

---

