---
title: "Turn off external HDD automatic"
date: 2010-12-28
forum: General Help
---

### Post by axept on 2010-12-28
Hello,

Is the a way to turn off my external HDD automaticly when I shut down my computer ? 

Its a HTPC running Ubuntu 10.10, the HDD is a WD 1TB disk in a IcyBox. There is a on/off button, but the HDD is not easy to get to, if you understand. It would be great if I could turn it off. It has been on for a LONG time now...

:???:

---

### Post by tredegar on 2010-12-28
If it is "not easy to get to" how are you sure it is not already turned off?

When I have an external USB HDD mounted, there's an icon on my desktop for the HDD.

If I r-click it, and choose "Safely remove" it is both unmounted and powered down.

Previous versions of linux (currently I have ubuntu 10.04) just used to unmount it, but not power it down. I could power it down from the CL with **eject /path/to/device** though.

Some of this functionality comes from linux, and some from the HDD, maybe it cannot be powered down from a USB command.

You will have to make some experiments, and see what works for you.

---

### Post by axept on 2010-12-28
It have a power on light... I can see that :)

Well, the computer is only a HTPC, I mean, I turn it on with this computer (WOL), and it has auto login, XBMC auto starts... And I turn it off with the the Android app XBMC Remote. I dont have mouse/keyboard connected to it. Well, I have if I HAVE to use it, but I dont want to plug it in to right-click on that unmount option everytime I turn it off.

I want a script that e.x runs on shutdown to turn it off (IF possible) and turn it ON on start-up...

---

### Post by tredegar on 2010-12-28
Listen carefully, because I am old, and I will say this only once.

I have been working with computers since the 60's (last century), but you are not able to communicate with me:
> Well, the computer is only a HTPC, I mean, I turn it on with this computer (WOL)
HTPC? What is it that that "you mean"?
WOL = "Way Out of Luck" or "Wake On LAN", perhaps. OK. Maybe.
> XBMC auto starts.
What is XBMC and why do you think I should know?
> And I turn it off with the the Android app XBMC Remote.
OK, "Android" is for mobile phones and stuff like that, no?
> but I dont want to plug it in to right-click on that unmount option everytime I turn it off.

"I don't waaaaaaant .... ". Oh. Forget it.

So just set up a script so when you turn "it" off "it" runs the script to power down your external HDD. The command you need is **eject /path/to/device**
May I remind you that your question was:
> Is the a way to turn off my external HDD automaticly when I shut down my computer ? 

The answer is "Yes", providing your external hardware supports this option.

Let us know how you get on.

---

### Post by axept on 2010-12-28
Well, thanks for the answear, it was VERY kindly of you..

Since youre so kind, can you PLEASE tell me HOW to make that script, and HOW to make it executable ?

Im NOT from the 60's and I've NOT used computers that long. I'm NEW to Linux.
So if you DON'T want to tell me, can you PLEASE post a link if there is another thread about it ? I have tried to google...

BTW, sorry for my BAD english..

---

### Post by tredegar on 2010-12-28
I am tired at this time of night, but would like to help you further.

You haven't told me what this HTPC thing _is_. So I do not fully understand how to make it work for you, in the manner you would prefer.

Please provide a link to its (HTPC) internet site (NOT "buy one here" but "How it it works" and the documentation about that).

Your english is fine. I speak no norwegian at all, so I understand your difficulty. We will perhaps manage somehow.

Best wishes

---

### Post by axept on 2010-12-28
Now we're talking :P

My HTPC is a ASrock 330HT-ION with blueray (well, that sucks in Linux or? :P), and thats _it_

Nothing more or less...


[ASrock ION 330HT-BD]("http://www.asrock.com/nettop/overview.asp?Model=ION%20330HT-BD")

---

