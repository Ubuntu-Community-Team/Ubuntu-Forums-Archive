---
title: "Youturbe videos, flickr slideshows do not work in Ubuntu 9.0.4 *EXTREMELY FRUSTRATED*"
date: 2009-11-14
forum: General Help
---

### Post by patrickpdk on 2009-11-14
Ubuntu, allegedly "easy" to work with, cannot run video content on the web, and generally doesnt work with many websites. On top of this, finding solutions is far more difficult than any windows issue. If I were on windows, and i couldnt play a youtube video, there would be at least 100 solutions found on a single google search.

Please, i am sick of windows, but I cant figure out why something so basic is so hard in ubuntu. I'm competent with computers since i work with linux/solaris machines but i dont have time to go on a scavenger hunt for a solution to every little issue.

---

### Post by codeking on 2009-11-14
There's a simple fix, you just need to install Flash player.  To do so, go to Applications -> Ubuntu Software Center.  In the search bar type "Adobe Flash Plugin."  Install that, and you should be good to go.

**Edit:** If your having trouble installing it, go to the terminal (Applications -> Accessories -> Terminal) and type in "apt-get update" and press enter.  Let it do its thing, and try installing again.

---

### Post by julianb on 2009-11-15
Use 
```
sudo apt-get update
``` 
rather than apt-get update.
You will have to put in your Ubuntu password (the one you created when you installed Ubuntu)

---

### Post by codeking on 2009-11-15
> **julianb said:**
> Use 
```
sudo apt-get update
``` 
rather than apt-get update.
You will have to put in your Ubuntu password (the one you created when you installed Ubuntu)

Oops, my bad.  Good call.

---

### Post by hal10000 on 2009-11-15
> Please, i am sick of windows, but I cant figure out why something so basic is so hard in ubuntu

70% of all the postings here in this forum would be unnecessary, if only people have one hour to read the basic help pages for beginners.

---

### Post by PRC09 on 2009-11-15
From Google:

Results 1 - 10 of about 2,750,000 for ubuntu wont play youtube. (0.30 seconds)

---

### Post by iNaitvad on 2009-11-15
Doesnt suposse firefox should install flash player, i belive previous versions did this, well of course isnt that hard. Even in Windows you should install flash manually (like in opera, or firefox also)
People just dont read instructions or warning messages, greetings...

---

### Post by patrickpdk on 2009-11-15
Unfortunately I have AMD64 chipset for which there is no ubuntu flash plugin (Now I recall fighting this issue in the past). Does this mean i'm just dead in the water then? I recall searching for a 64 bit version without luck...

---

### Post by patrickpdk on 2009-11-15
Actually, I found the amd64 version but the video performance is pretty bad... audio out of sync with video... thoughts?

---

### Post by hal10000 on 2009-11-15
> I recall searching for a 64 bit version without luck

```
apt-get install flashplugin-installer
```

If you have a 64 bit system (no matter if amd or intel), with this command you will get a 64 bit flashplugin, you don't need to serach anywhere.

Read the basic help topics.

---

### Post by Axess_Denied on 2009-11-15
Original poster must be unaware that all of us become frustrated with *nix at one point in our lives. Typically, though, we can reach out to our resources.

Best bet - ALWAYS - Google.

There are numerous posts in this forum already regarding Flash players in Ubuntu. Do some research and find out what changes you may need to make.

Ensure you have actually installed Flash? Ensure it is actually Adobe product, as others cause a/v problems?

---

