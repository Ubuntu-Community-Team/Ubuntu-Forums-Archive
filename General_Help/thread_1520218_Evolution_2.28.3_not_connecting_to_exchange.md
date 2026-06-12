---
title: "Evolution 2.28.3 not connecting to exchange"
date: 2010-06-29
forum: General Help
---

### Post by Village on 2010-06-29
I'm looking for a little help on this; have set up a computer running Ubuntu 10.04 and with it Evolution 2.28.3 I am trying to get this to connect to my office's exchange server. Try as I might I can't seem to get it to connect. I can get it to connect to the server to see the files (but not my personal part of the server for some reason, but that's another issue)

On my home computer (Ubuntu 9.10 & Evolution 2.28.1) I have been able to get it to connect to the exchange server just fine, it did it first time when I first started the programme last week (I haven't used Evolution for about a year before this). 
I have tried putting the exact same settings but no luck. 

Is there a know problem with Evolution 2.28.3 or (more likely) am I doing something wrong?

Thanks for any advice,

Village

---

### Post by Village on 2010-07-21
Just to add to this. I believe that the reason that Evolution would not connect to the MS Exchange is because the computer itself is plugged into the network on which the Exchange is based. 
If I tried to use Evolution to access the MS Exchange from outside the network it worked. 

In short I think it was because I was trying to use the web login address (as you are supposed to with Evolution) from the internal network. 
MS Exchange did not like this and so it would not work.

---

### Post by borobudur on 2010-07-22
Hey, I'm trying to connect to ms exchange on ubuntu 10.04 inside the companies intranet and this doesn't work.
Did you find a solution for this problem?
Thanks!

-- addition
I was able to install the MAPI plugin over synaptic (version  0.28.3-0ubuntu1). Like this I was able to connect to the ms exchange  server 2007 here at work (intranet). 

The mail account works just fine (identically like outlook) but the  calendar doesn't seem to work.

Anyone has solved this problem??

---

