---
title: "Startup Applications list locked"
date: 2010-02-24
forum: General Help
---

### Post by Dasani on 2010-02-24
About a month ago, I had something go very wrong in my Karmic and my account (with an encrypted home dir) was essentially inaccessible. But I was eventually able to create a new account, and retrieve all my data, but now, for some reason, I cannot edit the 'Startup Applications'.

I open its window and make any changes (which the window seems to accept), but then when I hit close, and restart it, it has been reset to everything I had set from my other account. Which makes little sense.

After that problem, I did have some trouble with permissions of certain files, and am afraid that I inadvertently gave up permissions on my startup applications, but can't imagine what I'd have to do to fix it.

Could I get some guidance?

thnx

---

### Post by drdanielfc on 2010-02-24
> **Dasani said:**
> About a month ago, I had something go very wrong in my Karmic and my account (with an encrypted home dir) was essentially inaccessible. But I was eventually able to create a new account, and retrieve all my data, but now, for some reason, I cannot edit the 'Startup Applications'.

I open its window and make any changes (which the window seems to accept), but then when I hit close, and restart it, it has been reset to everything I had set from my other account. Which makes little sense.

After that problem, I did have some trouble with permissions of certain files, and am afraid that I inadvertently gave up permissions on my startup applications, but can't imagine what I'd have to do to fix it.

Could I get some guidance?

thnx

can you login as root (i know its not recommended but can you? like from the login screen)

---

### Post by Dasani on 2010-02-24
You mean through the gdm?
I don't see root as a user there...so I'm not sure how.

But is your intention of finding out if it works though root?

Let me try from the terminal, I'll post the results back.

> **drdanielfc said:**
> can you login as root (i know its not recommended but can you? like from the login screen)

---

### Post by drdanielfc on 2010-02-24
> **Dasani said:**
> You mean through the gdm?
I don't see root as a user there...so I'm not sure how.

But is your intention of finding out if it works though root?

Let me try from the terminal, I'll post the results back.

Yes, from gdm (click "other user" the type root, and your root pass :D)

my intentions are to see if you skrewed up your root login up alltogether

---

### Post by gmargo on 2010-02-25
The startup applications are stored in $HOME/.config/autostart so you can check permissions there.  Most likely there's something that's owned by your old user id or by root.  

From the command line, find all the files under your home directory that don't belong to you with the following (replace username with your login name):
```

find $HOME \! -user username -print

```

---

### Post by Dasani on 2010-02-25
It was indeed an owner problem gmargo. Thanks very much!

I just chmoded it, and it works fine now...I'm not sure how those permissions changed, but they did somehow.

drdanielfc, I could log in from root, so I guess it wasn't that. Thanks for your support as well.

tc guys

> **gmargo said:**
> The startup applications are stored in $HOME/.config/autostart so you can check permissions there.  Most likely there's something that's owned by your old user id or by root.  

From the command line, find all the files under your home directory that don't belong to you with the following (replace username with your login name):
```

find $HOME \! -user username -print

```

---

