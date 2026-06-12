---
title: "Email Notification?"
date: 2006-05-10
forum: General Help
---

### Post by LadyDoor on 2006-05-10
Hi!

Ok, here's the thing. My latest crazy question. 'K. Does anybody know what program it is that, on non-X console, tells you whenever you have mail? It also does it in terminals when you do startx (I have a slow computer and also my mouse doesn't work too well, so I just startx into ratpoison from CLI; I can still get done the stuff that computers are useful for like word processing for classes and such). If anybody does know what program this is, does anybody know how to tell it to look in more than one mailbox when it does this? I ask because soon  I'm going to be receiving a LOT of email of two very different sorts and I don't want it to get lost all mixing together and such. And in X, does anybody know how to take a terminal bell and have it send a message to ratpoison WM instead of to screen?

Finally, does anybody know of a program that would run in the background, without a window or anything, that can be configured to run some program of your choice when you get new mail? I'm not talking about GKRELLM or anything--something that doesn't really have to be visible except when something happens, and then only because it's doing a command that you want.

Yeah, weird questions, I know, but I do have a slow, bad-mouse computer and so I've got to make do, don'chaknow...so I've actually been figuring out more than I actually EVER wanted to know about computers recently. Go figure.

Thanks in advance, with a bounty of kudos for respondants,
Door

---

### Post by realgenius on 2006-05-10
on a linux shell "mail" is the command/client... alternatively you could install pine

---

### Post by LadyDoor on 2006-05-10
Thank you for your reply; however, I'm not asking about a mail reader--I already use Mutt and like it fine. I'm asking about the command that seems to be invoked automatically in the background upon login to a CLI, and which continues to function after startx and which notifies the user (me) when there is new mail in the mailbox that matches my login name; based on the manual page, "mail" didn't seem to be it, and I'm fairly sure that Pine is a mail user agent of some kind.

So if anybody has any idea what this is, or knows of a mail notification program that can run entirely in the background, do multiple mailboxes, and execute a command when it finds new mail, it would be much appreciated. And if anybody knows how to take a terminal bell in X and reroute it to some command of my choice, that would also be much appreciated.

Thanks again in advance,
Door

---

### Post by LadyDoor on 2006-05-14
"Bump?" I think that that's what doing this is called...

---

### Post by LadyDoor on 2006-05-25
UPDATE!

So...I didn't actually find anything that could do this easily on my computer, but for anyone interested I learned a little about BASH scripting and wrote a BASH script that functions as an X email notifier and which runs in the background. However, unfortunately, at present it only works in the Ratpoison window manager (because this is what I use, and because it has a useful little "echo" function that can display stuff for a few seconds in the message bar). So anyone interested should feel free to check it out at [http://ratpoison.elektrubadur.se/Ratmail](http://ratpoison.elektrubadur.se/Ratmail) . Oh, and don't worry, English-speakers, the site's all in English (my native language, perhaps explaining the Englishcentricity of this comment), despite the non-.com/org/edu/etc. ending.

--Door

---

