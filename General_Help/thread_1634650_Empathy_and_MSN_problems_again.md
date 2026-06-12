---
title: "Empathy and MSN problems again"
date: 2010-11-30
forum: General Help
---

### Post by yakinikku on 2010-11-30
using 2 different systems.  system 1 running 10.04, system 2 running 10.10

system 1 cannot connect to MSN no matter what, i have searched the forums and tried the advice listed in this thread

[http://ubuntuforums.org/showthread.php?t=1583570&highlight=empathy+msn&page=5](http://ubuntuforums.org/showthread.php?t=1583570&highlight=empathy+msn&page=5)

but it does not work.  killing the butterfly process doesn't change anything, i get an endless connection attempt.

system 2 appears to be connected but whenever i send a message via MSN, a notification pops up with my own message.  and then with the reply from my friend.  also, the MSN contacts are all showing as "ungrouped" and I would like to get that fixed if possible.



any idea how to solve these issues? TIA

---

### Post by yakinikku on 2010-11-30
also, switching to pidgin is not an option.  pidgin does not support video chat for MSN, which is one of the reasons getting this working is so critical for me.

---

### Post by tigrita on 2010-11-30
I installed Ubuntu today and is the first time I use it. I am also having issues connecting to the msn messenger network by using pidgin, emesene, emphathy, kmess. I don't know what is wrong. Is it my computer??? my connection? everything is fine except that.

---

### Post by tigrita on 2010-11-30
Now for some weird reason I could connect to Pidgin. I still don't know if I can connect to the other messengers.

---

### Post by aust_paul on 2010-11-30
I also am having the same issues (I'm using 10.04 and Empathy 2.30.3). I hope somebody who knows a lot more than me has some ideas of a fix! I will hunt around in the mean time and post back here if I find anything.

Thanks!

---

### Post by Wired_boy on 2010-11-30
I am having trouble signing into the msn network as well. I'm using Lucid 10.04, and I"ve tried Emesene, aMSN and Empathy. I will try on my netbook next, and then I'll boot up my roomates windows 7 computer

I wonder if someone has changed a protocol or something. Has there been an update recently?

The conspiracy side of me thinks that someone at MS is trying to kick 3rd party programs off the network....

---

### Post by Wired_boy on 2010-11-30
Alright, I just checked my netbook (Ubuntu netbook 10.04) and my room mate's computer.

The netbook does not connect using aMSN, it gives an "Internal server error"

The Windows 7 computer does connect.

---

### Post by jpmelos on 2010-11-30
Seems like every client is having issues to connect to MSN... I guess Microsoft changed the protocol or something like that, so I guess we have to wait until developers catch up and update the clients... Just a guess.

---

### Post by gerowen on 2010-12-01
I switched over to emesene about a month ago because of not being able to permanently reject requests to add me from spammers.  I haven't touched Empathy since.  It's working just fine for me.

---

### Post by gandaran on 2010-12-01
you have to update Empathy and libpurple libs to the new versions then it will work again with msn.
if those updates aren't available from the ubuntu 10.04 repositories  (no problem  on ubuntu 10.10) you can still get them from getdeb.

---

### Post by yakinikku on 2010-12-01
> **gandaran said:**
> you have to update Empathy and libpurple libs to the new versions then it will work again with msn.
if those updates aren't available from the ubuntu 10.04 repositories  (no problem  on ubuntu 10.10) you can still get them from getdeb.

links?

also, any ideas about the issue i am having with 10.10 and having my own messages (only MSN messages BTW) get displayed via the ubuntu notification system?

---

### Post by yakinikku on 2010-12-03
> **gandaran said:**
> you have to update Empathy and libpurple libs to the new versions then it will work again with msn.
if those updates aren't available from the ubuntu 10.04 repositories  (no problem  on ubuntu 10.10) you can still get them from getdeb.

just checked getdeb.  both libpurple and empathy are nowhere to be found on the page.  empathy version is 2.30.3 and libpurple version is 1:2.6.6.1.

just checked the msn on the 10.04 computer now, it says its connected but it shows all users offline, even though i am online on another computer.

---

### Post by JaredNJames on 2010-12-04
I've got a similar problem.

Empathy signs in to msn, but I can't send/receive messages.  Not a clue why not.

---

### Post by ELD on 2010-12-06
I also have the same problem with 10.10, msn support is buggered.

---

### Post by gsiliceo on 2010-12-10
Same problem here, emesene doesnt work, emesene2 doesnt work either, what do i do?

---

### Post by Vermilion Sparrow on 2010-12-12
> **gandaran said:**
> you have to update Empathy and libpurple libs to the new versions then it will work again with msn.
if those updates aren't available from the ubuntu 10.04 repositories  (no problem  on ubuntu 10.10) you can still get them from getdeb.

Nope. I'm running 10.10, and since I last updated Empathy a couple days ago I can't connect to MSN. Everything is showing the latest version, so it's not a simple case of "just update it and it'll work."

The previous Empathy update a few weeks before that had caused MSN to behave erratically: it would connect, but initial messages to contacts would cause a new window to open as if I had sent the message to myself, and about 50% of the time any message sent to me would appear twice. This was annoying, but I'd take this back over not being able to connect at all (and I'm not about to download a bunch more IM clients in the hope MSN might possibly work with one of them).

---

### Post by yakinikku on 2010-12-17
i just updated the 10.04 computer with the most recent updates and now empathy has been removed from the system, when i try to reinstall it i get an error that the package is unreadable or something like that (i forgot the exact message).  what should i do now?

---

