---
title: "disable update to Natty, for public computer"
date: 2011-04-29
forum: General Help
---

### Post by An Sanct on 2011-04-29
Hello all!

Well, I have to manage a publicly accessible computer, and people know the password and are willing to click just anything, that pops up and has a "yes"/"ok"/"i agree" button on it, just to make the message disappear. (yes, I hate their ignorance ...) As long as they can use the net, that is all they care about...

My question is, can I still get updates for Maverick without being prompted for upgrade to Natty? Also I would like to remove the button from Update Manager. Is there a simple way to do that?

---

### Post by plucky on 2011-04-29
> **An Sanct said:**
> Hello all!

Well, I have to manage a publicly accessible computer, and people know the password and are willing to click just anything, that pops up and has a "yes"/"ok"/"i agree" button on it, just to make the message disappear. (yes, I hate their ignorance ...) As long as they can use the net, that is all they care about...

My question is, can I still get updates for Maverick without being prompted for upgrade to Natty? Also I would like to remove the button from Update Manager. Is there a simple way to do that?

Open Software Sources through Synaptic or Software Centre and navigate to the "Updates" tag and at the bottom of the page for "Release Upgrades", select **Never**.

---

### Post by Bucky Ball on 2011-04-29
Publicly accessible computer? It should be running 10.04 LTS. ;)

(I'm assuming it's 10.10)

---

### Post by An Sanct on 2011-04-29
Thank you plucky!

Yes, it runs 10.10, seemed to be the best around right now (yesterday, when I installed).

Why is 10.04 better for public computers? (I know it is LTS)

---

### Post by Bucky Ball on 2011-04-29
Yes, LTS and those releases are invariably more stable than the rolling releases (and intended to be; for servers and production machines that need to be stable and reliable ... a public machine would definitely be regarded as a production machine). Generally only updates to the next LTS release, when it's released, NOT the rolling releases, and only then when you ask nicely. :) 

Less chance of updates breaking anything. You are right to stay well away from 11.04 on a machine like that, especially right now. ;)

---

### Post by dino99 on 2011-04-29
As some of your future users may known of linux commands, and be able to bypass the previous config settings, i think you need better protection:

- apt-get redirect to null
- same for: software-manager, update-manager, synaptic, ...

well there is lot to do

---

### Post by An Sanct on 2011-04-29
> **dino99 said:**
> As some of your future users may known of linux commands, and be able to bypass the previous config settings, i think you need better protection:

- apt-get redirect to null
- same for: software-manager, update-manager, synaptic, ...

well there is lot to do

Thanks dino99!

Believe me, they don't know any commands and sudo is a name of a sausage factory for most of them, basically they don't know anything (firefox is the same everywhere). The ones, that *know* won't click wildly, just to get back to their Facebook accounts.

I've seen people installing software under windows and just hitting enter or next all the time, while tens, maybe hundreds of lines of text and options passed them on the fly ... EULAs, warnings, samples, how-tos, choices *not to* install that dreaded search panel in every browser, "bonzie buddie", ... etc... 

Its *that* kind of users, I am afraid of...

---

### Post by dniMretsaM on 2011-04-29
> **An Sanct said:**
> Thanks dino99!

Believe me, they don't know any commands and sudo is a name of a sausage factory for most of them, basically they don't know anything (firefox is the same everywhere). The ones, that *know* won't click wildly, just to get back to their Facebook accounts.

I've seen people installing software under windows and just hitting enter or next all the time, while tens, maybe hundreds of lines of text and options passed them on the fly ... EULAs, warnings, samples, how-tos, choices *not to* install that dreaded search panel in every browser, "bonzie buddie", ... etc... 

Its *that* kind of users, I am afraid of...


Lol, those kinds of user are the kind that slow down PCs. Randomly install anything and everything is never a good idea...

---

