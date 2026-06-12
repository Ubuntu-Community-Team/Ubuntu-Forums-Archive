---
title: "Need Firefox Help With Dumb Website"
date: 2010-04-05
forum: General Help
---

### Post by sting547 on 2010-04-05
Hi, my friend sent me a link called bouncecup.com DO NOT GO THERE. Whenever I try to close it it says "HELLO" and when I close that little window or okay is pops up again. I logged out and then logged in and opened firefox and it went back to the tabs that I had before and that website doing the same thing. When I press anything in firefox with that website it does the hello thing and will not stop. Please help I really cannot reinstall my computer and need firefox.

---

### Post by mickObrian on 2010-04-05
Open Firefox and go to the terminal and type 'sudo killall firefox', restart Firefox and see if it comes back.

---

### Post by akakingess on 2010-04-05
Even though that Okay window is popping up, is there a way for you to get into the preferences for FF and make sure that under the General tab, you make sure it has selected to "Go To My Homepages" when it starts, rather than "Show My Windows and Tabs From Last Time" or something like that? I am just throwing out some suggestions, but will keep brainstorming, also, you can start firefox from the terminal and just add a " -p " on the end to open the profile manager and start with a new profile. Then maybe reimport your bookmarks, etc. after creating a new profile, after which you could trash the old one. Just throwing out some ideas to get the engines moving :)

---

### Post by sting547 on 2010-04-05
THANKYOU THANKYOU THANKYOU!!! I put the "-p" in the terminal while putting in the firefox command and just removed the old default user and started over with bookmarks but that's alright. That thing was incredibly annoying thankyou, thankyou, thankyou, THANKYOU

---

### Post by marshmallow1304 on 2010-04-05
According to [this page]("http://kb.mozillazine.org/Sessionstore.js"), you can simply delete /home/*username*/.mozilla/firefox/*someprofile.default*/sessionstore.js .

---

### Post by sting547 on 2010-04-05
Yeah I was looking for .firefox I didn't even think about .mozilla

---

### Post by mechro on 2010-04-05
> **akakingess said:**
> Even though that Okay window is popping up, is there a way for you to get into the preferences for FF and make sure that under the General tab, you make sure it has selected to "Go To My Homepages" when it starts, rather than "Show My Windows and Tabs From Last Time" or something like that? I am just throwing out some suggestions, but will keep brainstorming, also, you can start firefox from the terminal and just add a " -p " on the end to open the profile manager and start with a new profile. Then maybe reimport your bookmarks, etc. after creating a new profile, after which you could trash the old one. Just throwing out some ideas to get the engines moving :)

Cool! 

You could also start with command **firefox [http://www.ubuntu.com](http://www.ubuntu.com)** and then edit your preferences/start page while keeping your profile.

---

### Post by lovinglinux on 2010-04-05
> **marshmallow1304 said:**
> According to [this page]("http://kb.mozillazine.org/Sessionstore.js"), you can simply delete /home/*username*/.mozilla/firefox/*someprofile.default*/sessionstore.js .

Yes, that's the best solution. Deleting the entire profile solves many problems, but is not the best solution if you don't keep regular backups.

---

### Post by akakingess on 2010-04-05
Yeah, like I said, I knew there were other/better options, but off of the top of my head, just trying to get the OP up and running. The only reason I didn't want to outright delete the profile was that the OP may have wanted to refer to it's settings, bookmarks, or something of that nature, but didn't want to go into so much detail as far as backing it up, deleting it, etc. Anyways, thanks to all that helped out on this one. 
@ Sting457, do you mind marking this thread as SOLVED, it is under the Thread Tools located at the top of the thread? Thank you, and have fun!

---

