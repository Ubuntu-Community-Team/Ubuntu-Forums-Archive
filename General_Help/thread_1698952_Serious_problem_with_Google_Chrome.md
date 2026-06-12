---
title: "Serious problem with Google Chrome"
date: 2011-03-03
forum: General Help
---

### Post by NexusN on 2011-03-03
Hi everybody, these day I am suffering from an issue where I find quite annoying so I would like to share and see I am alone or not.
 
I have been using Google Chrome Dev on my ubuntu 10.10 x64 for about half a year and it works perfectly fine.........until maybe one week ago.
 
On closing all the windows of Google Chrome, my ubuntu would sometimes auto log me off to the splash screen where I used to log in.
Sometimes it does, in some case after the log off it shows nothing and I have to reboot.:(
I thought it is a dev problem so I switched to standard version of Chrome but I've got no luck. The same happens and repeats everyday.
Therefore, I now think that it could be caused by a recent update of Google Chrome. The only proof is to see if someone shares the same pain with me............I am not gonna reinstall ubuntu just to test it out.
 
Thank you for you kind attention.:popcorn:

---

### Post by kerry_s on 2011-03-03
no, problems here.
if you end up at the log in screen, then i suspect your x is crashing. go into your home folder & press ctrl+h, check your .xsession-errors

---

### Post by NexusN on 2011-03-03
> **kerry_s said:**
> no, problems here.
if you end up at the log in screen, then i suspect your x is crashing. go into your home folder & press ctrl+h, check your .xsession-errors
 
Ok, let me check a bit for that.
If it is so related, is that a simple solution, say reinstalling the x you are talking about?

---

### Post by irie on 2011-03-04
I'm having the exact same problem.  Looking for a solution. I see errors but I have no idea what they mean.

---

### Post by NexusN on 2011-03-04
> **irie said:**
> I'm having the exact same problem.  Looking for a solution. I see errors but I have no idea what they mean.

I thought I have figured out why and the solution.
It is a bug due to the experimental function of Google Chrome, the Graphical acceleration components.
Have you switched on the two graphical acceleration components in the about:flags?
That is the cause.
On disabling, I don't see the problems again.
And Google Chrome Dev the latest built has one of that component on by default, so that maybe what causing you a crush.

If you are suffering from the same, try to turn them off and see if they persist.

---

