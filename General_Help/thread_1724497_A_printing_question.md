---
title: "A printing question"
date: 2011-04-08
forum: General Help
---

### Post by rakuba on 2011-04-08
Using 10.10, I have an Epson 1520 attached via parallel port, it works very well, the printer setup says it is shared. 
I would like to be able to print to it from my mac mini, but when I send anything I get the message network host is busy, will retry in x seconds, but of course it never gets anywhere.
Does anyone have any useful tips for getting this working
Thanks in advance.

---

### Post by rakuba on 2011-04-08
> **rakuba said:**
> Using 10.10, I have an Epson 1520 attached via parallel port, it works very well, the printer setup says it is shared. 
I would like to be able to print to it from my mac mini, but when I send anything I get the message network host is busy, will retry in x seconds, but of course it never gets anywhere.
Does anyone have any useful tips for getting this working
Thanks in advance.

Following up to myself, I had a nose round the cups interface and set it up for sharing there,
sent a page from the mac... nothing coming out this end
The mac now says printing, gets to 14% then printer paused, ad infinitum.
However when I look at completed jobs in the cups interface it claims to have printed all 3 pages I sent to it.
But of course it has not,
so if anyone has any ideas, I will be glad to hear them, cheers

---

### Post by rakuba on 2011-04-08
Fixed it!!!
I have a nose through the cups online documentation and discovered that I had to run a cupsctl command on the mac, which I did.
Now it is fully functional and even more useful than it was before, ie windows only and no support in macosx.

---

