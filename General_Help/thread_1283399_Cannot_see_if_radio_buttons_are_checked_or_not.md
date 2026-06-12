---
title: "Cannot see if radio buttons are checked or not"
date: 2009-10-05
forum: General Help
---

### Post by sopadeajo on 2009-10-05
Trying to understand how CompizConfig Setting Manager works, checking and unchecking Desktop capabilities and effects i suddenly lost the marks and do not know now if an option has been checked or not. This happen everywhere: i cannot now mark the mails i want to delete in yahoo mail.
The questions are: 
What happenend ? (i did not change any setting)
How to fix this?

Thanks for the answers.

Edited:

I do not know if i explained myself sufficiently.
In fact i can mark and unmark the radio buttons (if i look carefully) just because they appear to be deeper when marked, but the black x mark is no longer here.
 Strange problem, we need an expert her.

---

### Post by sedawk on 2009-10-05
Have you already rebooted once?

You can try to create a new user, login to his/her desktop
and see if it still works for the new user!

---

### Post by CatKiller on 2009-10-05
Those widgets are handled by the GTK+ theme you're using. You could try switching to a different one (and potentially switching back) to see if that helps.

---

### Post by sopadeajo on 2009-10-05
> **CatKiller said:**
> Those widgets are handled by the GTK+ theme you're using. You could try switching to a different one (and potentially switching back) to see if that helps.

But i am a beginner (a newbie) and do not know what a widget is; and yes i rebooted and no i did not create a new user cause i do not know very well how to do it and less how to fix the problem once i did it if i did.

I do not know if i explained myself sufficiently.
In fact i can mark and unmark the radio buttons just because they appear to be deeper when marked, but the black x mark is no longer here. Strange problem.

---

### Post by CatKiller on 2009-10-05
> **sopadeajo said:**
> But i am a beginner (a newbie) and do not know what a widget is;

[Widget]("http://en.wikipedia.org/wiki/Widget_%28computing%29") is just a general term to refer to all the little interface elements. Radio buttons are widgets. Checkboxes are widgets. Scrollbars are widgets. That sort of thing.

You can change theme generally with the System &#8594; Preferences &#8594; Appearance &#8594; Theme tool, or specifically change the GTK+ theme by selecting Customise... from that screen and changing the Controls theme to something else. That should hopefully get you into a position where your widgets work again, and switching the theme back again should help you to isolate where the problem is.

The suggestion to create and check a new user is to isolate whether the problem is a user-specific one or whether it's a system-wide problem. It's a standard troubleshooting step to track down where a problem may lie. It's simple enough to do - just use the Users and Groups tool to add another user, and then log in as that new user and have a play. You only really need to do this if you don't have any luck with changing the theme as your existing user.

You may be struggling with the fact that you're inexperienced (and you don't need to feel apologetic about that; we all were once) but we're struggling with the fact that we're half-way round the world from you which leaves us limited in what we can do unless we already know the solution. Hence the general troubleshooting steps to try to isolate the cause of your problem.

---

### Post by sopadeajo on 2009-10-05
> **CatKiller said:**
> [Widget]("http://en.wikipedia.org/wiki/Widget_%28computing%29") is just a general term to refer to all the little interface elements. Radio buttons are widgets. Checkboxes are widgets. Scrollbars are widgets. That sort of thing.

You can change theme generally with the System &#8594; Preferences &#8594; Appearance &#8594; Theme tool, or specifically change the GTK+ theme by selecting Customise... from that screen and changing the Controls theme to something else. That should hopefully get you into a position where your widgets work again, and switching the theme back again should help you to isolate where the problem is.

The suggestion to create and check a new user is to isolate whether the problem is a user-specific one or whether it's a system-wide problem. It's a standard troubleshooting step to track down where a problem may lie. It's simple enough to do - just use the Users and Groups tool to add another user, and then log in as that new user and have a play. You only really need to do this if you don't have any luck with changing the theme as your existing user.

You may be struggling with the fact that you're inexperienced (and you don't need to feel apologetic about that; we all were once) but we're struggling with the fact that we're half-way round the world from you which leaves us limited in what we can do unless we already know the solution. Hence the general troubleshooting steps to try to isolate the cause of your problem.



Thanks CatKiller (hope you're not one since i love cats).

I had understood the suggestion of creating a new user to see where is the problem, but i did not know how to do it, so i decided to wait.

Changing the theme has worked.I can see now the black marks in the radio buttons (widgets). Yet i do not understand what happened and why is it specifically related to the theme i was using.I'll get into it again now, (though it was a customized theme and not sure i'll remember its name) to see if the problem remains with this theme.
Thanks and sorry for my bad English.

---

### Post by sopadeajo on 2009-10-05
I went back to the them called Thinice and again the black widget marks couldn't be seen.

---

### Post by CatKiller on 2009-10-05
I don't think ThinIce uses marks for those widgets. So it's not a problem so much as an ugly theme.

---

