---
title: "Flash in x64 Chrome"
date: 2010-09-05
forum: General Help
---

### Post by dheinle2010 on 2010-09-05
I just downloaded and installed the 64-bit version of Chrome and went to try and watch a youtube video but when i do it says i need to upgrade my flash player, so when i click upgrade, adobe tells me it's built into chrome... help?

---

### Post by kerry_s on 2010-09-05
do you have "ubuntu-restricted-extras" installed?

don't install flash in the browser, always use the repo versions there upgraded automatically.

---

### Post by soldier1st on 2010-09-05
> **kerry_s said:**
> do you have "ubuntu-restricted-extras" installed?

don't install flash in the browser, always use the repo versions there upgraded automatically.
i would also do what you would suggest. the ubuntu restricted extras includes flash/java/etc... so it's all you need.

---

### Post by gandaran on 2010-09-05
flash from the repositories wont work in new version 6 chrome, it still works in chromium but not in chrome as it has built in flash so it wont look for system installed flash.
the big problem for 64-bits Ubuntu users is 64-bits flash, adobe doesn't make 64-bits flash, so I wonder how chrome 6 handles 32-bits flash, maybe chrome 64-bits will have the same problem as the rest of system installed flash users in Ubuntu 64-bits, works for some only!

---

### Post by kerry_s on 2010-09-05
> **gandaran said:**
> flash from the repositories wont work in new version 6 chrome, it still works in chromium but not in chrome as it has built in flash so it wont look for system installed flash.
the big problem for 64-bits Ubuntu users is 64-bits flash, adobe doesn't make 64-bits flash, so I wonder how chrome 6 handles 32-bits flash, maybe chrome 64-bits will have the same problem as the rest of system installed flash users in Ubuntu 64-bits, works for some only!

thats bull. i'm running 64bit ubuntu with chrome 6 & flash works fine.

---

### Post by gandaran on 2010-09-05
> **kerry_s said:**
> thats bull. i'm running 64bit ubuntu with chrome 6 & flash works fine.
then you are one of the lucky ones, 32-bits flash works for you!
remove the flashplugin- installer in synaptic and you will see flash will still work in chrome! chrome doesn't use that flash, only works with built in flash, or at least the 32-bits version does so I believe its the same for 64-bits chrome or I could be wrong here, I am using the 32-bits chrome and don't have flash installed in synaptic and flash works!

---

### Post by kerry_s on 2010-09-05
hmm, i don't want to really mess with it, videos work, i can play flash games, watch the youtub movies, etc...
best not to temp it.

it does show in the plugins though.

---

### Post by gandaran on 2010-09-05
> **dheinle2010 said:**
> I just downloaded and installed the 64-bit version of Chrome and went to try and watch a youtube video but when i do it says i need to upgrade my flash player, so when i click upgrade, adobe tells me it's built into chrome... help?
type this code in url bar
```
about:plugins
```
this will show all plugins in use and post a screenshot

---

### Post by kerry_s on 2010-09-05
> **gandaran said:**
> then you are one of the lucky ones, 32-bits flash works for you!
remove the flashplugin- installer in synaptic and you will see flash will still work in chrome! chrome doesn't use that flash, only works with built in flash, or at least the 32-bits version does so I believe its the same for 64-bits chrome or I could be wrong here, I am using the 32-bits chrome and don't have flash installed in synaptic and flash works!

i tried it. see pic

---

### Post by gandaran on 2010-09-05
> **kerry_s said:**
> i tried it. see pic
okay, does the flashplugin still show in chrome plugins? 
if not then it's settled only the 32-bits Chrome uses built in flash!

---

### Post by Jazzy_Jeff on 2010-09-05
> **kerry_s said:**
> thats bull. i'm running 64bit ubuntu with chrome 6 & flash works fine.

+1 on this for me as well.

---

### Post by kerry_s on 2010-09-05
> **gandaran said:**
> okay, does the flashplugin still show in chrome plugins? 
if not then it's settled only the 32-bits Chrome uses built in flash!

my guess is since theres no 64bit flash currently available it was not included. 32bit is native so it can just add it to regular chrome, to run 32bit flash in 64bit chrome you need nspluginwrapper which i don't think they want to do.

---

### Post by PeteLong on 2011-01-31
Try

[http://www.petenetlive.com/KB/Article/0000385.htm]("http://www.petenetlive.com/KB/Article/0000385.htm")

Pete

---

