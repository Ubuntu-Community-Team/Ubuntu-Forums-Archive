---
title: "unix shells"
date: 2006-03-02
forum: General Help
---

### Post by njzillest on 2006-03-02
how can i get a free unix shell. i dont think optimum provides shells...
 

i want to be able to host my website and tel net others.............................. nothing illegal :) :)

---

### Post by glug101 on 2006-03-02
If it's not blocked by your provider (and I don't think it usually is) your ubuntu box should have ssh available on port 22.  ssh is wonderful stuff.  Just like telnet, but with more capabilities (like tunnelling almost anything you want, including xwindows) and it's encrypted so others aren't listening in.  I use it all the time with my mac.

If the port is blocked, I'm sure there is some way to switch to a different one, I just don't know it off the top of my head. :)

---

### Post by njzillest on 2006-03-02
yeah SSh is great, but i do think telnet and other programs are still blocked by my ISP. I use Optimum.. im able to connect to the server through SSH but not on telnet :(. 


Also im able to port scan at my school (they dont have it blocked) but i cant port scan in my house. i have opened up port 22 for telnet. Does this mean its blocked by my ISP? or does it simply mean im doing something wrong.. do i have to port foreward?


is there a way to get a linux shell with out contacting my ISP.. because my ISP doesnot provide Shells..


thanx

---

### Post by dickohead on 2006-03-02
1. Pick up the phone.
2. Call them.
3. Ask if they block port 22
4. If yes ask about port 21...23...24..25...26... you get the idea.
5. Reconfigure SSH to use the port they DON'T block
6. Change your router to forward that port also.
7. Done.

---

### Post by V4Vendetta on 2006-03-02
Ignore the above, calling your ISP about hosting any kind of server from home is usually a bad idea despite your intentions, also you will want to use a port after 1024 for ssh, something like 1109 is a good idea.

---

### Post by skymt on 2006-03-02
[QUOTE=njzillest]yeah SSh is great, but i do think telnet and other programs are still blocked by my ISP. I use Optimum.. im able to connect to the server through SSH but not on telnet :(. [/QUOTE]

One quick question: what are you trying to do? Sometimes on web forums it's best to say what your goal is, not just what step on the way is going wrong. If all you want is shell access, SSH does that much better than telnet. I can't, off the top of my head, think of any things telnet can do that SSH can't.

In fact, I highly recommend *not* using telnet. It's famously insecure, which is why SSH was invented. At this point, telnet is basically a "legacy" feature, hanging around for compatibility's sake.

---

### Post by dickohead on 2006-03-02
> Ignore the above, calling your ISP about hosting any kind of server from home is usually a bad idea despite your intentions, also you will want to use a port after 1024 for ssh, something like 1109 is a good idea.

Slightly rude, but a good point. But you will still need to find out if they block the port you are going to try and use, you don't have to mention anything about security, just that you would like to know if port 22 is blocked, if they say no - then you know the problem is at your end.

---

### Post by glug101 on 2006-03-03
[QUOTE=skymt]One quick question: what are you trying to do? Sometimes on web forums it's best to say what your goal is, not just what step on the way is going wrong. If all you want is shell access, SSH does that much better than telnet. I can't, off the top of my head, think of any things telnet can do that SSH can't.

In fact, I highly recommend *not* using telnet. It's famously insecure, which is why SSH was invented. At this point, telnet is basically a "legacy" feature, hanging around for compatibility's sake.[/QUOTE]
I'd like to echo the bit about ssh.  If ssh works, there is nothing I can think of that telnet would be good for (with the posible exception of demonstrating how insecure telnet is).  

The only cumbersome thing I can think of with ssh, it the whole key swapping thing.  Mostly it happens automatically, but in some rare instances your ssh key changes and the other computer forgets who you are and refuses to connect.  In that case, I generally delete all stored keys (I think rm -fr $HOME/.ssh will do it) and when ssh asks 'do you want to accept this key' you type 'yes'.

If ssh is working and telnet isn't, are you sure the telnet daemon is running?  I think it's disabled by default with Ubuntu (and most civilized Linux distros for the reasons outlined here).

---

### Post by njzillest on 2006-03-23
ssh is working (i have to specify the port)

it turned out i had to also port foreward on my network 



thanks guys for the responses!

---

