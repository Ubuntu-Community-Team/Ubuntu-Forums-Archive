---
title: "vnc4server - keep session running?"
date: 2010-07-03
forum: General Help
---

### Post by DJYoshaBYD on 2010-07-03
**Ive had a post in the network section for a couple days, and no one has responded.. Im hoping i can get an answer here, as i know its an easy fix, and its very annoying.. lol**

ok.. so i got it installed, and it works GREAT.. except one big flaw..

if i stop that session, and come back later, it will have me log on at the login screen, but start a new session, with multiple instances of things..

now, with vino, i could just keep the same session running, and when i VNC in, it just resumes it.. This one starts a new one.. i even tried just locking the screen, and it still starts a new one...

i know there is an easy fix.. lol.. i just cannot find one.. i REALLY like how it shows me the ubuntu login on my server.. that is slick, so id like to keep that, if possible..

by the way, its ubuntu hardy.

thanks!

---

### Post by DJYoshaBYD on 2010-07-03
bump

---

### Post by DJYoshaBYD on 2010-07-03
27 veiws, but no posts? 

bump

---

### Post by DJYoshaBYD on 2010-07-03
nother bump.. bump bump bump

come on people.. someone has to know SOMETHING about this.. anything.. 

NO ONE has ANY CLUE how to just resume sessions in VNC? seriously

---

### Post by Irony on 2010-07-03
Your question is gibberish, hence no answers.

---

### Post by DJYoshaBYD on 2010-07-03
ummm.. no.. its not gibberish at all.. its VERY straightforward..

When i log in using VNC to my server, it gives me a login window.. I log in, and it tells me im already logged in, and if I want to start a new session.. starting a new session is the only way to get in.. 

now, when I do this, and close my VNC session, and i try to log back in, it tells me the same, then when i get into it, it opens a brand new session, like im logging in for the first time, restarting any open programs, and making duplicate services run for every login I do..

Here is the original

> if i stop that session, and come back later, it will have me log on at the login screen, but start a new session, with multiple instances of things..

now, with vino, i could just keep the same session running, and when i VNC in, it just resumes it.. This one starts a new one.. i even tried just locking the screen, and it still starts a new one...

is this really the only thing you can say, dude? If you dont understand the question, then dont answer.. 

I have been trying for 2 days to get an answer on this, and all i got was a snide comment from you.. thanks.. you really helped alot..

now that I have clarified what the issue is, considering some cats consider it nonsensical, anyone have anything CONSTRUCTIVE to suggest??

---

### Post by DJYoshaBYD on 2010-07-03
bumpsies

---

### Post by DJYoshaBYD on 2010-07-03
damn.. any more bumps on this post and it will need to see a Dr.. hahaha

---

### Post by DJYoshaBYD on 2010-07-03
hmmmmmmmmmm.. well, i hope someone helps me out.. lol..

i mean, this would probably help out some other people besides me, if its solved publicly.. haha

just throw some ideas out there... anything you can think of..

---

### Post by DJYoshaBYD on 2010-07-04
**taps feet** :)

Is there a MOD in here that sees this post? do you guys have any better ideas than the one suggested by the last guy? BESIDES locking the thread?

I have been searching over and over.. no one will even step to the plate to try and troubleshoot? 

This could help quite a few people.. lol

ps.. im working the server forums, answering lots of tech questions.. trying to contribute... anyone in this section want to do the same??

---

### Post by HermanAB on 2010-07-04
Hmm, well, you won't get useful answers, because VNC is never used for anything serious.  VNC is mainly a Help Desk tool.

If you want to manage a server, the standard practice is to use SSH.

---

### Post by DJYoshaBYD on 2010-07-04
ummmmmmm.. ok.. i guess thats a way of saying "i dont know how to fix your issue"

i know exactly what VNC is used for, I do have SSH set up on my machine, and this is a home server, just for me.. 

im not asking about workaround to remote access.. i already have it.. what i DONT have, is way for VNC to stop making new sessions, which I guess I am the only person that this has happened to..

i understand standard practice.. but, what i am doing is VERY standard, and people do it all the time.. mine is just causing an issue, that no one IS EVEN WILLING TO TRY AND HELP WITH... which is highly annoying, considering there are alot more complex issues on this forum, that people just take wild guesses at..

no one is even taking a guess.. the only responses i even got on this thread, was one guy who cant read, and another that tells me NOT to do what I am doing (even though this is done all the time)..

now, does anyone have any ACTUAL troubleshooting steps?

I have done my part helping with some server threads, trying to better the community, and provide the community support this distro needs.. But its seems the few times i have posted a thread asking for help, its like my thread just gets skipped over.. 

coooooooommmmmmmeeeeeeeee oooooooonnnnnnnnnnnnnnnnnn... someone try something, cause ill bump this thread forever until someone steps in to help.. hahahahahaha

bump :popcorn:

---

### Post by DJYoshaBYD on 2010-07-04
> **HermanAB said:**
> Hmm, well, you won't get useful answers, because VNC is never used for anything serious.  VNC is mainly a Help Desk tool.

If you want to manage a server, the standard practice is to use SSH.

I never said i was using it for anything serious.. i dont know where you got that from.. its just for my server.. that is it..

and i dont really use VNC for management.. i mainly use it for browsing at work to sites where they dont allow us to go (yahoo mail, gmail, etc etc)..

so yeah.. alllllll im asking for, is how to fix this problem.. not dump my setup and go a different route.. there should be an easy fix for this.. someone has to have some idea..

---

### Post by DJYoshaBYD on 2010-07-05
bumppppppppppppppppppppppppp

---

### Post by DJYoshaBYD on 2010-07-06
bumpybumpybumpybumpybumpybumpybumpy

Original Post:

[QUOTE]ok.. so i got it installed, and it works GREAT.. except one big flaw..

if i stop that session, and come back later, it will have me log on at the login screen, but start a new session, with multiple instances of things..

now, with vino, i could just keep the same session running, and when i VNC in, it just resumes it.. This one starts a new one.. i even tried just locking the screen, and it still starts a new one...

i know there is an easy fix.. lol.. i just cannot find one.. i REALLY like how it shows me the ubuntu login on my server.. that is slick, so id like to keep that, if possible..

by the way, its ubuntu hardy.

thanks!

---

### Post by DJYoshaBYD on 2010-07-07
bump.. still scratching my head on this.. i cannot get it to just keep on one session using xdmcp and vnc4server.. it just keeps starting new sessions for every time I log in, also creating duplicate processes of everything.. GNOME panel, clock, power manager, etc.. 

any ideas?

---

### Post by HermanAB on 2010-07-07
Well, you have discovered almost all the reasons why nobody uses VNC for anything serious.

If you are still hell bent on using it, then you'll have to join the developers of VNC and try to fix it.

---

### Post by DJYoshaBYD on 2010-07-07
well, again.. like i said.. its NOT for anything serious.. 

and from what I am seeing, its an issue with XDMCP running with vnc4server..

> Well, you have discovered almost all the reasons why nobody uses VNC for anything serious.

If you are still hell bent on using it, then you'll have to join the developers of VNC and try to fix it. 

^^^^^ what that tells me, is that you have probably never used it, or have used it very little, and have no clue how to fix anything with it.. 

if you dont have any advice on how to fix THIS issue, then please dont respond with "well, maybe you should not do it"..

and yes.. I am hellbent on getting it to work, and post up the solution, to show that a n00b had to figure something out that this whole part of the forum will not even attempt to figure out.. 

its not a development issue.. its a combo of VNC, and the way its logging into my server.. 

any other actual suggestions?

---

### Post by Irony on 2010-07-07
Try tightvncserver.

---

### Post by DJYoshaBYD on 2010-07-07
i actually was using that one, and it worked fine for a while, but I could never get the resolution higher than 640x320, which did not work.. lol.. i tried all the different fixes to get it to work, and nothing did..

then i uninstalled that, and put vnc4server, as per the instructions i found on quite a few different sites, and it worked fine, and a resolution of 1280x1024, which is perfect for what i need..

but yeah.. the reason i dont use tightvncserver is because it has low res, and i could never get it higher.. 

thanks dude :) glad someone had a good idea.. haha

---

### Post by DJYoshaBYD on 2010-07-07
ok.. well, i figured out a real simple fix..

first of all, i have my main username set to autologin on boot.. this was creating dual sessions with the local one, when logging in via XDMCP.. :)

so, I set up a session with all the progies i need running, and let that one boot.. then, i created another username, that I use just for logging in to VNC and doing remote work, and it has the same rights as my other user..

problem solved.. 

glad I figured it out, and i hope this helps someone else in the future, cause you will be screwed if you ask in a thread.. lol

---

