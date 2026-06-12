---
title: "Compiz title bar problem"
date: 2009-08-12
forum: General Help
---

### Post by Balagast on 2009-08-12
I tried searching around and trying a few different things, but I am still having the same issue.

I have a 8.04 installed on a t43p with a ATI Mobility v3200 graphics card.  I have Compiz and Emerald installed and it has been working fine for awhile now, with no issues, until recently.

Basically what happens is, what seems like random, when I open an app the title bar disappears and the window is snapped to the top of the desktop. I can't move the windows or close them which makes this very aggrivating.

Everything else seems to be OK, and it all seems for work for a little while if I restart the computer, but then it shortly gets defunct again.

I've tried using 'emerald --replace' in the terminal, and that doesn't fix the issue.  In fact, when I do that the terminal becomes useless and I lose the prompt.

Any suggestions?

---

### Post by Balagast on 2009-08-13
Oh yeah, btw, I used envyng to install the graphics card drivers a little over a week ago (and it was working fine).  is this a bad idea?  It worked great on my desktop PC which has an nvidia card.

---

### Post by CatKiller on 2009-08-13
> **Balagast said:**
>  I've tried using 'emerald --replace' in the terminal, and that doesn't fix the issue.  In fact, when I do that the terminal becomes useless and I lose the prompt.

I don't know how to fix your Emerald problem, but the reason you "lose the prompt" is because that Terminal is still running the emerald process, in case you wanted to give it more input. You could either background the process in the Terminal, which would take you back to the prompt, by appending the & character, like so

```
emerald --replace &
``` or you could use the Run dialogue instead by pressing Alt-F2 and running emerald --replace.

---

### Post by Balagast on 2009-08-13
Thanks for that advice.

I have noticed that it is only now having this issue with Firefox.  If I open a terminal, VLC, Amarok, Azereus etc they all work just fine.  The issue only seems to be occurring with firefox.

I'm thinking it could be an Ati graphics driver issue.  How do I check to see which one my computer is using?  What would be the best to use with a mobility v3200 (essentially the workstation version of a x600)?  I'm thinking the fglrx driver would be the best.

---

### Post by CatKiller on 2009-08-13
I have no idea, I'm afraid. I've not used Ati graphics. The Hardware Drivers tool is usually the easiest, though. I don't know if Envy will conflict with that.

---

### Post by VastOne on 2009-08-13
> **Balagast said:**
> Thanks for that advice.

I have noticed that it is only now having this issue with Firefox.  If I open a terminal, VLC, Amarok, Azereus etc they all work just fine.  The issue only seems to be occurring with firefox.

I'm thinking it could be an Ati graphics driver issue.  How do I check to see which one my computer is using?  What would be the best to use with a mobility v3200 (essentially the workstation version of a x600)?  I'm thinking the fglrx driver would be the best.

I had this same issue before where out of the blue it began without rhyme or reason.  My fix was to go to System/Preference/Appearance/Visual affects and click the last one (what I use, option 2 will work too) to restart the effects. After I did that everything returned to normal. It never made any sense to me why it happened and I am a nVidia user so the ATI question may be moot.

---

### Post by Balagast on 2009-08-13
Well I figured I post this because I have seemed to have fixed the issue.  I uninstalled the drivers I was using, and installed the flgrx drivers and that seems to have fixed the issue completely.

Perhaps just reinstalling the drivers did it, but either way this is working now, so I'm happy.

Thanks for all the input guys.

---

