---
title: "compiz proces hangs on any file action in nautilus"
date: 2011-06-12
forum: General Help
---

### Post by Matglas on 2011-06-12
Hello,

When I try to to do something like creating a new folder in nautilus the screen freezes. i'm still able to move my mouse but clicking has no effect. it also happens when renaming a file or deleting a file or folder. 
I can access the commandline when the screen is frozen and i found out that the compiz process was taking 100% of my cpu, after killing the process the system works fine again.
I also noticed that the file action wich coused the freeze was done, so i try to create a folder the system freezes i stop the compiz process and the folder is there.
The  problem doesn't occour When is start the session using ubuntu classic with no effects.
I tried reistalling compiz and the video driver but whitout any luck... :(

I would really appreciate it if someone has a solution for this because its very frustrating.

Specs:
Ubuntu 11.04 64bit (clean install)

HP Touchsmart TX2
AMD Turion X2 Ultra Dual-Core Mobile Processor ZM-86 (2.4 GHz)
ATI Radeon HD 3200 Graphics with 64MB Display Cache Memory
4GB DDR2 System Memory (2 Dimm)

Please help me!!

---

### Post by Matglas on 2011-06-13
Any ideas?

---

### Post by FormatSeize on 2011-06-13
Do you absolutely have to have Compiz running? I have never had a good experience with Compiz ever since Ubuntu 9.04. It eats up a bunch of CPU, destroys window borders, and all sorts of other havoc. Even over the weekend when I tried out a very lightweight distro, it acted like a spoiled child.
 
But, if you prefer to have it running, then I would try installing the latest version compiz-plugins. According to [this bug report](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/419264), compiz-plugins has been patched so that it doesn't do what you are experiencing. See if that helps.

---

### Post by hawthornso23 on 2011-06-13
It is probably just one plugin that is causing the issue, and if you can figure out which one that could help. Install the compiz config settings manager and try disabling (then reenabling) compiz plugins one at a time. 

Are you using unity or ubuntu classic? Unity isn't very tolerant of changes to compiz settings. Suggest you not disable the unity plugin in a unity session. To check if the unity plugin is the one acting up, login into a classic session instead.

Any time there is a compiz problem video driver issues could be involved, so check that all of that is working OK.

If you are running unity then the all purpose unity fix 
```

unity --repair
```
might do the trick. Good luck.

---

### Post by Matglas on 2011-06-15
Thank you two very much for reacting.

Turning off the file watcher plugin solved my problem!

Cheers,
Thijs

---

### Post by hawthornso23 on 2011-06-16
Ahah! And yes, I see there is a reported bug with the file watcher plugin which causes this issue.
[URL="https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/773564"]
https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/773564[/URL]

Good sleuthing.

---

