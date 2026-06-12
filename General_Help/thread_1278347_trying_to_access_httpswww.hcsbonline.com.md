---
title: "trying to access https://www.hcsbonline.com/"
date: 2009-09-29
forum: General Help
---

### Post by EricMattessich on 2009-09-29
So I go to login to my banks website [https://www.hcsbonline.com/](https://www.hcsbonline.com/) and I get no such luck on my Ubuntu 9.04 machine while my windows machine with firefox has no issue at all.  So I thought maybe its the browser and that turned out to be untrue after I installed, Opera, Konquer, IE6 and IE7.  I don't know what to try next, do you guys have any ideas on things I should try?  Could someone please just put [https://www.hcsbonline.com/](https://www.hcsbonline.com/) into their browser also to make sure its not just me.  Thanks guys in advance!!!

-Eric

---

### Post by lloyd_b on 2009-09-29
> **EricMattessich said:**
> So I go to login to my banks website [https://www.hcsbonline.com/](https://www.hcsbonline.com/) and I get no such luck on my Ubuntu 9.04 machine while my windows machine with firefox has no issue at all.  So I thought maybe its the browser and that turned out to be untrue after I installed, Opera, Konquer, IE6 and IE7.  I don't know what to try next, do you guys have any ideas on things I should try?  Could someone please just put [https://www.hcsbonline.com/](https://www.hcsbonline.com/) into their browser also to make sure its not just me.  Thanks guys in advance!!!

-Eric

Loads just fine here.

Please run "ifconfig" in a terminal window, and post the output.  

What may be happening is that your MTU (max transmission unit, or maximum packet size) under Linux is set too high for some segment of path between you and that site.

To test this: Assuming you're connecting via "eth0" (you don't provide much info, so I have to guess), try running "sudo ifconfig eth0 mtu 1500", and then try connecting.  Then try stepping down (1400, 1300, etc.)  If you get it down to 1000 and it's still not connecting, then it's probably not an MTU issue.

Lloyd B.

---

### Post by undecim on 2009-09-29
Are you able to get to other web sites with https?

---

