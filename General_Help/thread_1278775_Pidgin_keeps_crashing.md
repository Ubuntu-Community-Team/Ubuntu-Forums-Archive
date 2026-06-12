---
title: "Pidgin keeps crashing"
date: 2009-09-29
forum: General Help
---

### Post by Volt9000 on 2009-09-29
Normally Pidgin behaves itself, but once in awhile it crashes, seemingly for no reason.
Does Pidgin keep logs somewhere of what it does, or is there a way I can run Pidgin in debug mode to see what's going on under the hood and possibly track the crash?

---

### Post by zeroseven0183 on 2009-09-30
What version of Pidgin are you using?

---

### Post by Volt9000 on 2009-09-30
Ah yes, I forgot that critical piece of information. :oops:

Pidgin version 2.5.2 running on Intrepid Ibex 8.10.

---

### Post by 13thSlayer on 2009-09-30
Run in a terminal. Post the output of a terminal here. That might be helpful.

---

### Post by Volt9000 on 2009-10-06
Ok, well finally Pidgin crashed. Not too helpful though...

```

Segmentation fault

```

I just found out Pidgin can be run in debug mode, which may help in finding the problem. Once it crashes again I'll post the log.

---

### Post by superatrain on 2009-10-08
I also have been experiencing this, and for quite a while too.

I've just set up full debug logging and will try and post my results soon.

---

### Post by Volt9000 on 2009-10-08
Alright, Pidgin has finally crashed. Here's the last bit...

```

(18:33:43) g_log: msn_nexus_get_token: assertion `nexus != NULL' failed
(18:33:43) g_log: msn_nexus_get_token_str: assertion `token != NULL' failed
(18:33:43) g_log: xmlnode_set_attrib: assertion `node != NULL' failed
dns[19016]: Oops, father has gone, wait for me, wait...!
Segmentation fault

```

This appears to be an XML parsing error, I would think.

---

### Post by Wiebelhaus on 2009-10-08
When I check new mail and then open or close the new mail window it crashes every time , I've unable to drill down the reason.

---

### Post by SR_ELPIRATA on 2009-10-08
My Pidgin crashes too but not all the time. Doing it from the console gets me the seg fault that you described but also other messages. Today, pidgin is again being unable to log into yahoo, I dont use it for retrieving email, just to talk with my yahoo buddies, but right now, no matter what, yahoo can't connect.

I had this earlier, some months ago, and changing the server helped me, but I'm beginning to wonder why they change this so much and what else I can use that does work....

Any clues?

ELP

---

### Post by SeanHodges on 2009-10-12
I had this same issue.

I fixed mine by backing up my Pidgin config, and setting it up from scratch:

```
mv ~/.purple ~/.purple-old
```

---

