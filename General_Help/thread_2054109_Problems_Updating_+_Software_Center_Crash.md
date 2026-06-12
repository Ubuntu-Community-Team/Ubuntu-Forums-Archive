---
title: "Problems Updating + Software Center Crash"
date: 2012-09-06
forum: General Help
---

### Post by Flexography on 2012-09-06
Hi,

After opening the Ubuntu Software Center, the program freezes before getting past the initial loading screen, before crashing.  
Additionally, when attempting to run the Ubuntu updater, the updater returns this error:
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I investigated the specified location (var/lib/apt/lists/) and noticed that the file the error pertains to, as well as many of the other files, include redirect links which should not be there.  
I believe that the cause of this was my school's wireless internet, which requires a username and password before you are allowed access to the internet.  I suspect this because the redirect links are the same as what the internet security thing would provide.  
I logged in as Root, deleted the redirect from the URLs in the deb.opera files, and restarted the computer, logging back into my account.  The same problems occurred, returning the same error message.  I reopened the files I made changes to, to see if they had been saved.  My edits had been preserved, though I noticed other changes I had not noticed before, such as "WEB AUTHENTICATION REDIRECT" between <title> </title>, which is the title of the login page required by my school (it's a CISCO login page, by the way).  
This leads me to conclude that it was definitely something my school's internet did to these files, but without knowing what these files looked like prior to being tampered with, I can't make the appropriate changes to them which would revert them to their undamaged state.

Furthermore, I'm not quite sure how my school's wireless internet has permission on my computer to edit system files, when I as a user lack the same privileges...

Any help would be greatly appreciated.

Shawn.

---

### Post by Flexography on 2012-09-06
-bump-

---

### Post by Bashing-om on 2012-09-06
shawn,  With my poorer knowledge I respond.
I can advise you on how to resolve this situation.
```

sudo apt-get clean
sudo rm /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/partial/*
sudo apt-get clean
sudo apt-get update

``` But I can not tell you why "apt-get update" brings in and restores the scripts that were deleted (the "bad" files").
[INDENT]hth <==BDQ

[/INDENT]

---

### Post by Epodx64 on 2012-09-07
You could try a different mirror as well.

---

