---
title: "Problem with smooth image scaling in FF3"
date: 2010-10-24
forum: General Help
---

### Post by Arno Nühm on 2010-10-24
Hallo,

i face problem with Firefox 3.6.11: smooth image scaling doesn't work. When i zoom in websites (ctrl +), images are not anti aliased, but appear pixelated, which is very ugly.

What I found out about so far, this seems not to be a FF problem (FF3 should support smooth image scaling), but a problem with the video driver, who tells X it could do smooth image scaling automatically but it cant. There is also a "bug" fix for the FF:

launchpad.net/~firefox-smooth-scaling/+archive/ppa

I putted this to my package sources and made a system update. But smooth image scaling still doesn't work :(

Could someone help please?

My configuration:

Sony Vaio Notebook
ATI Mobility Radeon HD 5000 Series 
Ubuntu 10.04 (AMD64)

kind regards

---

### Post by P4man on 2010-10-24
Did you update your repository with 

```
sudo apt-get update
``` after adding that ppa?

After that, you could just try 

```
sudo apt-get upgrade firefox
```

But before you do; which drivers are you using, proprietary or opensource?

---

### Post by Arno Nühm on 2010-10-24
Thanks for your reply!

I tried what you suggested, but it didnt help :(

I use the proprietary driver (fglrx)

---

### Post by Mike_tn on 2010-10-25
Same problem here
The smooth scaling PPA was working fine until FireFox 3.6.11 showed up
My guess is the PPA is behind on its updating.

One idea:
Probably need to make sure Firefox asks before it updates
Tell it no, then do it manually in a month.

Unless there is a place to find the updated PPA,
I found references about 3.6.11 but no handy repository code to paste in.

Then again Im a noobie so there may be other answers
I found nothing about it online anywhere

---

### Post by Morientes on 2010-10-26
It's pretty amazing that this is still a problem in Ubuntu!
It's been like this for ages and it really is a pretty big deal when using Firefox...

---

### Post by P4man on 2010-10-26
its not an ubuntu thing: Its a firefox thing (/cairo thing); But yeah its weird they havent solved it yet. There is always chrome or opera though :)

---

### Post by Mike_tn on 2010-10-26
> **P4man said:**
> its not an ubuntu thing: Its a firefox thing (/cairo thing)

Yep, good point, trying an Un-buntu based live distro today proved that.

---

### Post by Morientes on 2010-10-28
Hm, they should get their act together on Firefox then.
They are loosing customers. I just switched to Chrome where it's working just fine.
I don't really understand: do they think it's not a big deal or what? For me it's a HUGE deal. I can't really live without being able to zoom - the text is too small. And text-only zoom messes up the pages and the pixelated images just look soo bad. Untill now I have used that repository where it's fixed but that causes some other problems. So I think it's just Chrome for me now.:)

---

