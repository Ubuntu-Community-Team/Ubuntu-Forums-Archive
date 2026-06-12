---
title: "Help with performance issue"
date: 2009-09-09
forum: General Help
---

### Post by dbpbandit on 2009-09-09
I'm having some performance issue with Jaunty; every time I open a wine app the system comes to a crawl. It does recover and the app launches but I just don't see this as normal? It's so bad that if I'm playing music (from local files) the music pauses until the app launches. Any suggestions? I am running Jaunty on a DELL Optiplex 755 with dual processors and 4 GB of RAM. Thanks. 

-Dave

---

### Post by Sam Lars on 2009-09-10
I noticed that when you open things with Wine it takes a lot of loading... does that change when you open a second program?

---

### Post by jondkent on 2009-09-10
Might be worth ensuring that it is wine that is doing this.

Run *top* in a console and then launch your wine application and see how much cpu/memory it is using.  Obivously if it starts eating all you memory/cpu you know what is going on, if not need to start looking at other things.

Which application are you running under wine?

What other apps have you got running at the same time as wine?

Cheers,

Jon

---

### Post by dbpbandit on 2009-09-18
Looks like it is eating up my resources. One thing I did was start using Amarok instead of Rhythm box, that stopped my music from stopping and made everything else run better as well. I guess the music player was using a lot of resources I wasnt aware of.... Thanks for the help though. I wasnt aware ot that "top" command, prety nice little command to have.

-Dave

---

