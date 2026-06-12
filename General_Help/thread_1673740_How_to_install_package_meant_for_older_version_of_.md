---
title: "How to install package meant for older version of Ubuntu on newer version?"
date: 2011-01-22
forum: General Help
---

### Post by xpaperbackwriterx on 2011-01-22
Specifically, I want Clementine player 0.6, but the guy that installed Ubuntu on my laptop put natty narwhal alpha 1 on it (don't ask me why.  I wanted maverick since its stable but he never really asked.  The whole thing was kinda a surprise), and Clementine only offers downloads for Ubuntu distros up to maverick.  So.  Can I/is there a way I can install it anyway?  Or am I forced to just use Banshee until the official Update comes out and Clementine is updated in....April, isn't it?

---

### Post by Frogs Hair on 2011-01-22
I would not recommend installing on an alpha release because you may end up with missing dependencies and broken packages. On the other hand you may get lucky. I would ask for a reinstall unless you really want to be 11.04 tester. ;)

---

### Post by xpaperbackwriterx on 2011-01-22
UURRGGGGHHH! *headdesk* NOOO!

---

### Post by ivanovnegro on 2011-01-24
> **xpaperbackwriterx said:**
> UURRGGGGHHH! *headdesk* NOOO!

It seems you have to install Ubuntu again but Maverick, the latest stable.
Or you will be a Natty tester, Im not sure if you could compile Clementine from source, but this is maybe not what you want to do.

---

### Post by drewsus on 2011-01-24
There are 3 things you can do here:
1) Reinstall Ubuntu (Maverick)
2) Install Clem from Source
3) Install Clem from the development PPA

We won't address 1 yet as your friend probably didn't even separate the / from the /home to make this option a breeze. And not even 2 quite yet. 

So, 3, as it is the easiest, and you are already bleeding edge.. might as well keep that up. 

Run these commands in terminal: 
```
sudo add-apt-repository ppa:me-davidsansome/clementine-dev
sudo apt-get update
sudo apt-get install clementine
```

Profit (;

dRewsus
ps- as someone who installs and customizes Ubuntu for numerous people, please slap your friend in the face for me. Who installs a version of Ubuntu that is in heavy development, still in alpha **ONE**, on a system for someone that doesn't even know how to install it themselves, nor even build from source (no offense of course; I hope you get my drift). Thats just ignorant and you should show your friend this *ps* and slap him for yourself while you are at it.

---

### Post by mc4man on 2011-01-24
> Clementine only offers downloads for Ubuntu distros up to maverick
If you keep on 11.04 then you can just install clementine, take a look in software center or synaptic. (0.6 version + some updates for natty

(or from terminal
```
sudo apt-get install clementine
```

---

### Post by xpaperbackwriterx on 2011-01-24
@drewsus

Did what you said, it worked, and so far no issues.  Thank you very much :) And also, I can't slap the smart computer guy because then he might not fix my up my next desktop for me ;) and it wasn't installing Ubuntu that was my issue(I was in the process of learning in preparation of doing that last summer, but then my mom, who bought the stupid laptop, was like O.O you will break it!), it was partitioning my hard drive that scared me mostly (I'm dual booting so my mom can feel like I'm having a "learning period").  But yeah I am wondering why he put it on there. Meh, I think I'm just gonna work with being a natty tester until the final release (when hopefully I will convince my mom to let me just get rid of the stupid Vista). :D Again, many thanks to you!

---

