---
title: "Firefox: new windows take TOO long to appear. Reinstalling doesn't solve it"
date: 2010-03-20
forum: General Help
---

### Post by gadolinio on 2010-03-20
Well, this is some weird thing happening to firefox 3.0.18.
 I think it has something to do with an update, because it started yesterday afternoon after having accepted some updates offered by the update manager.
 

 Every time i want to open a new firefox window, after having a fisrt one, the program takes about five to twenty minutes to obey. Not kidding...
  If i right click a link and select open in a new window, or just click the firefox's launcher on the panel or menu, it doesn't do it until 5 to 20 minutes have passed. By that time i'm doing something else, and the same quantity of windows i told it to open suddenly appear. Weird.
 

 >>These things do not fix the problem:
 reinstalling firefox, upgrading to 3.6, installing swiftfox. As in those three cases it's still using the same related/dependencies/etc packages, the problem mustn't be the main package nor the ones that i uninstall from synaptic when i look for &#8220;firefox&#8221;.
 I also replaced my /home/user/.mozilla folder (of which i have a backup previous to this problem). Bookmarks and preferences went back to their previous state, but the problem persists.
 

 >>Things that are always true:
·this happens ONLY WITH FIREFOX (both opera and epiphany work ok)
 ·this is the ONLY SYMPTOM. Everything else in the system and the browser is perfectly normal.
 ·this happens ONLY WITH NEW WINDOWS. New tabs are opened perfectly well. That's actually the only way to surf several pages simultaneously now.
 ·this happens ONLY WHEN FIREFOX IS RUNNING. This means that i can always open it for a first time, as fast as usual; but i can't, once it's running, open it again nor open a link in another firefox window, unless i wait for those minutes.
 And if once opened, i tell it to open a new window, it doesn't appear immediately. Now suppose i close the first window with the cross of the title bar... The program is still being executed. I mean, the order of openning a new window is delayed but... &#8220;alive&#8221;, let's say. SO IN THAT CASE: i would have no windows opened (because i closed the only one with the cross), but i can't open another one  anyway, as long as firefox is running even with no window open. I have to shut it down with the system monitor. FIREFOX IS STILL WANTING TO OPEN THE WINDOW!
 ·After killing the process with the system monitor, i can open firefox again perfectly.
 

 So this is in the end a complete matter of TIME DELAY, once the application is being executed.
 

 If you have read all this, i hope i haven't bored you :P  And if you know how to fix this, better!
 Thanks in advance...

---

### Post by dcstar on 2010-03-20
> **gadolinio said:**
> Well, this is some weird thing happening to firefox 3.0.18.
 I think it has something to do with an update, because it started yesterday afternoon after having accepted some updates offered by the update manager.
 

 Every time i want to open a new firefox window, after having a fisrt one, the program takes about five to twenty minutes to obey. Not kidding...
........
 If you have read all this, i hope i haven't bored you :P  And if you know how to fix this, better!
 Thanks in advance...

Try the IPv6 solutions.

---

### Post by gadolinio on 2010-03-21
> **dcstar said:**
> Try the IPv6 solutions.

Sorry... i don't even know what that is :S
Can you please provide some step-by-step guide?
Thanks!

---

### Post by lovinglinux on 2010-03-21
Have you tried to create a new Ubuntu user and check if the problem persists with the new account?

Do you have Prism installed?

---

### Post by gadolinio on 2010-03-21
> **lovinglinux said:**
> Have you tried to create a new Ubuntu user and check if the problem persists with the new account?

Do you have Prism installed?

Well, it's working OK now... I don't get it. I didn't try anything else after creating this thread. I didn't have any updates, installed nor uninstalled anything... and it's suddenly working normally now.
Did i say that i found this somewhat weird??

Didn't try firefox with another user; that would've been an interesting test. But after reading your post FF was ok.
I don't have Prism. Read about it on  the website,but don't understand why you ask about it.

Well, i won't mark the thread as solved because i didn't actually find a solution. I don't even know what happened, in the first place.

Thanks for your replies!

---

### Post by gadolinio on 2010-05-05
> **lovinglinux said:**
> Have you tried to create a new Ubuntu user and check if the problem persists with the new account?


Good idea! Same thing happened again, so I tried using firefox with another account, in which it works OK. So I replaced my .mozilla folder with the other user's and FF is now working perfectly. So it must be some account-related issue. Still don't know why a backup of my own user folder didn't solve the problem the first time; maybe the problem was already there when the backup was done.
Thanks!

---

### Post by gersonZaragocin on 2010-06-05
Hi everybody

This happened to me after upgrade my Ubuntu version from 9.10 to 10.04. Of course it didn't take minutes but at least 20 seconds in opening a new window. So I just went to my home folder and under

.mozilla/firefox

I deleted the "profiles.ini" file

This solves the problem, but of course all your profile information has to be set again after the visit to your prefered sites

Hope this helps.

---

### Post by lovinglinux on 2010-06-05
> **gersonZaragocin said:**
> Hi everybody

This happened to me after upgrade my Ubuntu version from 9.10 to 10.04. Of course it didn't take minutes but at least 20 seconds in opening a new window. So I just went to my home folder and under

.mozilla/firefox

I deleted the "profiles.ini" file

This solves the problem, but of course all your profile information has to be set again after the visit to your prefered sites

Hope this helps.

The safest method of deleting profiles is through the profile manager. Deleting the profiles.ini file will leave you with a dead profile folder and a new will be created. 

I only recommend deleting profile as the last solution. Next time see [URL="http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html"]Fixing a problematic or corrupted profile
[/URL]

---

### Post by gersonZaragocin on 2010-06-06
> **lovinglinux said:**
> The safest method of deleting profiles is through the profile manager. Deleting the profiles.ini file will leave you with a dead profile folder and a new will be created. 

I only recommend deleting profile as the last solution. Next time see [URL="http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html"]Fixing a problematic or corrupted profile
[/URL]

Thanks. I'll keep it on mind next time,

---

