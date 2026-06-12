---
title: "How much of a dead end is IE for Ubuntu?"
date: 2012-05-15
forum: General Help
---

### Post by Roasted on 2012-05-15
Traditionally, any company that requires me to use Internet Explorer, I instantly walk away and cross them off the list of possibilities. Several video surveillance manufacturers fell into this category when I was searching for cameras. That said, I cannot apply that mentality to this situation because it's for a work scenario beyond my control. The maintenance crew runs Ubuntu on their Lenovos, but one of their HVAC systems requires IE for ActiveX. IETab for Chrome was a dead end, and the machines are low powered enough that I'm not sure a virtual instance of XP would work. The best idea we have on the table now is setting up a VM of Windows on a server and having the crew remote desktop into it.

Is Internet Explorer on Linux that much of a dead end? Or is there someway, somehow a way to get it on a Linux box?

---

### Post by wilee-nilee on 2012-05-15
Gotta use wine I believe, not sure of the most recent version of IE you can run though.

I would just use a virtual, or dualboot a windows setup.

Honestly if it meant a job based on IE I would take the job.

The loyalty to only open source is not really a functional approach to life in my opinion at least for me.

There are so many other areas that can be put to a change in ways of  thinking and acting that this one, which is rather quaint, is at least  for me a wasted approach.

Not sure if this is the issue here just my .02 cents

I would go into to details of the areas really needing help, but it would break the COC.

---

### Post by westie457 on 2012-05-15
Would either of these work for you?

[http://www.tatanka.com.br/](http://www.tatanka.com.br/) (IEs4Linux)

[http://wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html](http://wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html)

---

### Post by Roasted on 2012-05-15
> **wilee-nilee said:**
> Gotta use wine I believe, not sure of the most recent version of IE you can run though.

I would just use a virtual, or dualboot a windows setup.

Honestly if it meant a job based on IE I would take the job.

The loyalty to only open source is not really a functional approach to life in my opinion at least for me.

There are so many other areas that can be put to a change in ways of thinking and acting that this one, which is rather quaint, is at least for me a wasted approach.

Not sure if this is the issue here just my .02 cents

I would go into to details of the areas really needing help, but it would break the COC.

I was stated my personal opinion versus what I'm facing here at work. If it were up to me, I'd walk and ditch the product all together, but that's only because I'm stubborn and refuse to be told what to do over something so simple like a web browser. But here I am at work where we're running Linux yet this application needs IE... so I just need to figure out a way to make it work, if at all possible. 

For what it's worth, when I load up IE7 64 bit on 12.04 64 bit in wine, it extracts for a while and comes back saying "Internet Explorer is not supported on this operating system."

> **westie457 said:**
> Would either of these work for you?

[http://www.tatanka.com.br/](http://www.tatanka.com.br/) (IEs4Linux)

[http://wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html](http://wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html)

Thanks! I'll look into these.

---

### Post by lilmagnus on 2012-05-15
> **Roasted said:**
> ...The best idea we have on the table now is setting up a VM of Windows on a server and having the crew remote desktop into it...

I like this idea. Simply because of the maintenance factor. One place to load any controls necessary. I assume you'll be running a server edition of Windows to support multiple RDP sessions? Another option may be to prop up a small virtual desktop environment. There's even a [few]("https://www.google.com/search?q=xen+vdi&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs#hl=en&safe=off&client=ubuntu&hs=OnV&channel=fs&sclient=psy-ab&q=open%20source%20virtual%20desktop&oq=open%20source%20virtual%20&aq=1&aqi=g4&aql=&gs_l=serp.11.1.0l4.5898.14712.0.17126.20.13.0.7.7.0.177.1270.9j4.13.0...0.0.6u7721GZgck&pbx=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&fp=4e45555d180c00bb&biw=1270&bih=648&pf=p&pdl=300") open source initiatives in that space.

---

