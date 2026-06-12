---
title: "Sluggish user account?"
date: 2010-07-08
forum: General Help
---

### Post by andonato on 2010-07-08
Hi, I'm running Hardy on a Dell mini 9 netbook. I have two user accounts set up - my primary account which I work in most of the time, and a second account which I switch to from time to time.

The problem is that when i switch to the second user the system gets very sluggish. It takes forever to do things, even open a browser. Sometimes it will freeze up completely requiring a restart of X or even worse, a hard power down (yes, I know that's bad). The machine runs reasonably well under the primary user. Any idea what is going on or how I can fix it?

---

### Post by QLee on 2010-07-08
[QUOTE=andonato]Hi, I'm running Hardy on a Dell mini 9 netbook. I have two user accounts set up - my primary account which I work in most of the time, and a second account which I switch to from time to time.

The problem is that when i switch to the second user the system gets very sluggish. It takes forever to do things, even open a browser. Sometimes it will freeze up completely requiring a restart of X or even worse, a hard power down (yes, I know that's bad). The machine runs reasonably well under the primary user. Any idea what is going on or how I can fix it?[/QUOTE]

I presume you mean switch user with fast user switching not log off and log on as another user. 

I wonder how much RAM you have in that netbook, it is just a single core processor isn't it. So, if both users are logged on and running two instances of X there is a chance that the resources of the netbook are strained when you fast user switch. Do you see much swap activity, how big is your swap?

If it was my system, after I swiitched to the 2nd user and logged on, I would try switching back to primary (leaving the 2nd logged on) and see if my primary user ran slow under those conditions. If it does, low on resources is likely and you may be able to add RAM.

I'm just speculating because no one has answered your question yet and it's been around for a few hours, it won't make sense if my initial presumption wasn't correct.

---

### Post by andonato on 2010-07-08
> I presume you mean switch user with fast user switching not log off and log on as another user. 

Actually no, I tend not to use fast user switching. I am logging out and logging back in as the second user. But you bring up an interesting point, I wonder what would happen if I tried fast user switching. It might just make things worse (if that is possible) for the reasons you point out...

---

### Post by QLee on 2010-07-08
Well, another thing you might try would be to add a 3rd user and see if logging on as that user acts the same as user 2nd. That might show if it is somehow related to that 2nd users configuration. Is there anything special that that 2nd user does which the primary doesn't?

Otherwise, the way you are using them, they're using the same resources, I can't think what would cause sluggish on one and not the other.

---

### Post by andonato on 2010-07-08
Thanks for the suggestion. I'll give it a shot.

---

