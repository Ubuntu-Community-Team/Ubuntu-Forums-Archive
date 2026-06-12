---
title: "Help! - Unity interface disappears on logout/restart"
date: 2011-05-23
forum: General Help
---

### Post by sarahlizz3 on 2011-05-23
If this is somewhere else, I apologize - I've searched for days and can't find a fix (or even someone with the same issue), but I may just not be using the right keywords in my search.

Here's my problem.  I upgraded to 11.04, and I like the Unity interface.  But every time I logout and back in (or restart) it starts in Classic mode.  
- If I go to Compiz, it shows that Unity is enabled.
- When I login, it shows that the Unity interface is selected.
- If I run ```
unity --replace
```in the terminal Unity will run, but then if I close the terminal, it will (sometimes)shut Unity back down.  

I would really like to use the Unity interface, and would appreciate any advice on how to resolve this issue.  Thanks!

---

### Post by sarahlizz3 on 2011-05-23
I should also add that I also tried logging in with a user defined session.  When I did that, the Unity plugin was not enabled in compiz.  I enabled it, then it asked me to resolve conflicts which I did.  Which were:
[LIST]
[*]The new value for the edge binding for the action Reveal Mode in plugin Ubuntu Unity Plugin conflicts with the action Flip Left of the Desktop Wall plugin.
[*]The new value for the key binding for the action Key to put keyboard-focus on launcher in plugin Ubuntu Unity Plugin conflicts with the action Show Main Menu of the Gnome Compatibility plugin.
[/LIST]
Then nothing happened. My desktop did not change to Unity, even though it says it is enabled.  Not sure if that info will help, but thought I'd include it.

Update:  I installed Unity 2d and that will load without a problem (even after a restart).  
Also, I found in another post on an unrelated issue, to use ```
unity --reset
``` as a run command.  That works, but still when I logout and log back in, it doesn't stick.  Now when I log back in (and select Ubuntu, not Unity 2d) it puts me into Unity 2d.  I can reset it using the above command, but I would rather not have to run it every time I log in.  (I realize I can set it to run automatically, so I will probably do that for the time being, but I am wondering if anyone knows what is causing this).

---

### Post by wamooo on 2011-08-11
I'm having the same problem and would absolutely LOVE to hear if you or anyone else found a solution. If not, then would someone help me out and let me know how I can make the command *unity --reset* run automatically every time I log in?
Cheers!

---

### Post by sarahlizz3 on 2011-08-11
> **wamooo said:**
> I'm having the same problem and would absolutely LOVE to hear if you or anyone else found a solution. If not, then would someone help me out and let me know how I can make the command *unity --reset* run automatically every time I log in?
Cheers!

You can set it to run automatically by going to Startup Applications.  Click "Add" and then put *unity --reset* in the command line and name it something.

I finally just decided to reload Ubuntu and now Unity 3D is working fine.  But, obviously, that's an annoying fix.

---

