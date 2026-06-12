---
title: "often but random browser problem"
date: 2010-11-14
forum: General Help
---

### Post by m0laria on 2010-11-14
Hello,

I'm running ubuntu 10.10 (upgraded from the beta), and I am getting a weird problem with in all browsers. It seems that links just randomly go wonky. For instance, I click the home page, and it directs me to About.com (one of my favorites on my favorite bar in firefox is from About.com). Or, I click on the reddit link from my igoogle page, and it takes me to google.com. The weird thing is, when this happens, certain websites will work, but others won't work (they will always link to google.com, or about.com, or whatever random website is chosen from my favorites to become my "home page"). Any help would be appreciated.

Here is my uname output: Linux ***-*** 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

Thanks.

---

### Post by Foxheadz on 2010-11-14
Have you tried just removing and reinstalling the browser?

---

### Post by pqwoerituytrueiwoq on 2010-11-14
> **Foxheadz said:**
> Have you tried just removing and reinstalling the browser?
i doubt that would do any good deleteing the browsers settings probably would
press [ctrl]+[H] in your home folder locate .mozilla open the firefox folder
and delete the xxxxx.default folder and that will reset firefox

---

### Post by m0laria on 2010-11-14
When it happens in firefox, those same websites are also not working/accessible in Chrome as well.

---

### Post by m0laria on 2010-11-15
So I both apt-get remove and apt-get install 'ed firefox, and also deleted the hidden firefox folder forcing the reset, and I still experience the same problem. Here's another example of what happens. For instance, I go to google news, and click a link, and it directs me to this:

**Invalid URL**

 The requested URL "/2010/CRIME/11/14/ohio.family.missing/", is invalid. Reference #9.940bc841.1289798223.35dff685

---

### Post by Foxheadz on 2010-11-15
> **m0laria said:**
>  The requested URL "/2010/CRIME/11/14/ohio.family.missing/", is invalid. Reference #9.940bc841.1289798223.35dff685

That sounds more like a link to a file on a computer not a url...

---

