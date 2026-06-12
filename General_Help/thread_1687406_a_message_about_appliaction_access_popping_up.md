---
title: "a message about appliaction access popping up"
date: 2011-02-13
forum: General Help
---

### Post by robtheartistman on 2011-02-13
Hello there. Hopefully I've put this posting in the right spot. I'm new to ubuntu, and not that familiar with how updates and such work sometimes. 

I've had it running for a couple of days, and, unfortunately, I accidentally unclicked a pop up blocker when I was looking at permission settings. I think looking at the settings let the pop up through in the mean time. I got one of those "you have won this" pop ups, and my comp locked up. I did a manual shut down, then turned comp off.

  When I turned off then turned my comptuer back on, and I tried to access my net connection, I got this message:

"an application wants access to the keyring default but it is locked" 

then the screen for my username/password for dsl shows up and disappears"

I am thinking that I got a hack from the site I had visited? I am thinking there is a vague possibility that its an update thing from ubuntu, but I very much doubt it. 

I am usually overly vigilant or too lax LOL I worry about what I shouldn't and don't worry about what I should. Hopefully its nothing.

What's the best course of action? I have the ubuntu load disc, so if I really need to, I can re-install or boot from first hard disk

---

### Post by Habitual on 2011-02-13
DSL requires User/Password, yes?

"What's the best course of action" - enter the requested password.

Paranoid? 
It doesn't mean they are NOT out to get you and me. :) (j/k)

Run this in terminal to "see" what's connected in real-time.
```
watch -n 0 'netstat -pant | grep ESTABLISHED'
```

Hope that Helps.

---

### Post by robtheartistman on 2011-02-13
Well, the thing is that when I turn the comp on, the setup I had before let me just click on my connection and it went, but this time, that message popped up, it was diff than usual procedure. It happened after my glitch with the website, so that made me wonder

---

### Post by Habitual on 2011-02-13
Alt+F2 
```
seahorse
```

Right mouse click on "Passwords:Login" and choose unlock.
Enter your password.
Expand it using the + sign.
You see your DSL account there?

What 'glitch' with what website?

Let us know...

---

### Post by HiImTye on 2011-02-14
if you have empathy or most google/website services on most docks (i.e. docky/cairo) set to launch on boot you will receive that message (as they need to unlock the keyring to retreive your account passwords)

also, wireless passwords require the keyring

---

### Post by williamts99 on 2011-02-14
Which is why I always 'use unsafe storage' for my keyring :)

---

