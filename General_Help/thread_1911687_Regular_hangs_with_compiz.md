---
title: "Regular hangs with compiz"
date: 2012-01-19
forum: General Help
---

### Post by schveiguy on 2012-01-19
I have a Dell Inspiron E1705, with the builtin i915 chipset video controller.

Ever since I upgraded to 11.10, I daily experience hangs in compiz (sometimes 3-4 times a day).  The most common time it happens is when utilizing the launcher bar.

The solution I have found is to switch to a virtual terminal, and kill compiz with -9.  Then compiz restarts and all my windows are usable again.  This *sometimes* simply logs me out which is nerve-wracking :)

Has anyone had similar issues and solved them?  From searching these forums, it seems that people who have had this issue (though I couldn't figure out whether they had the same video hardware) use the same solution (switch to terminal kill compiz), but nobody seems to have found a solution to the issue.

Thanks.

---

### Post by cogier on 2012-01-19
As you said there seems to be an issue with Compiz and Unity. I suggest you don't use Compiz or revert to 10.04LTS which runs it well or try Zorin OS which is based on Ubuntu, Compiz is very nicely set up on install.

---

### Post by schveiguy on 2012-01-19
Well, thanks for the suggestion, but that's not really an option for me.  I want to get this thing working, and I have too much based on the current OS to downgrade.

---

### Post by Dreamer Fithp Apprentice on 2012-01-19
> **schveiguy said:**
>  . . .
The solution I have found is to switch to a virtual terminal, and kill compiz with -9. . . . 

Would you mind elaborating on that, giving explicit instructions? It might be helpful with the slowdowns/hangs/freezes I'm having as described in my as yet unanswered thread here:
 [http://ubuntuforums.org/showthread.php?t=1911599](http://ubuntuforums.org/showthread.php?t=1911599)
Thanks and good luck.

---

### Post by schveiguy on 2012-01-19
I responded in that thread, i don't think it's the same issue.  I *never* get control back once it hangs, until I kill compiz.

However, I coincidentally had the same issue as that a while back :)

For reference, the sequence I use is ctrl-alt-f1, log in, do:

ps auxw | grep compiz

determine pid for compiz, then

kill -9 <PID>

Then alt-f7 to get back to x windows

-Steve

---

### Post by Dreamer Fithp Apprentice on 2012-02-18
Thanks. Always useful to have this sort of tool to pull out of the desperation box.

---

### Post by Benzjaminz on 2012-02-19
I've just started having a similar problem with compiz freezing my desktop at random times. Since compiz update this week I think. 

This is not a solution but until I can find a fix, I've been logging into Ubuntu 2D. Just select it at login. This at least provides an adequate experience and no crashes while I'm waiting for a fix.

---

### Post by schveiguy on 2012-02-29
Don't know if it's coincidence or something has been fixed, but I have not had a hang in several weeks.  I have had compiz crash, but that's way more manageable than a hang, and that doesn't happen very often.

If I go a month without a hang, I'm likely to mark this as "solved" via divine intervention :)

---

### Post by schveiguy on 2012-03-19
Well, I guess it was coincidence.  Had several hangs last week.  grrrr....

---

