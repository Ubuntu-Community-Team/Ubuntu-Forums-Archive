---
title: "Low disc space, cache-&gt; open failed"
date: 2011-06-22
forum: General Help
---

### Post by mokshus on 2011-06-22
Hello, thanks for the time to read and try to help.
I am running Ubuntu 8.04 Hardy Heron on a dell n series laptop. When it came into my possession I attempted to update it using the update manager, but there was not enough disc space for all of the updates. I attempted to clean space by using the autoclean, sudo apt-get autoclean, and now when I try to open either the Synaptic package Manager or the update manager I get the following error report:

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any assistance on this matter would be greatly appreciated. Thanks again for your time.

---

### Post by e79 on 2011-06-22
Have you tried the suggestion that came from that message ?

```
sudo dpkg --configure -a
```

---

### Post by mokshus on 2011-06-22
I entered the command and it entered the setup for localepurge, which I was going to use also but decided against because I did not want to do it incorrectly. I apologize for my ignorance, I am trying to learn more about the system.

---

### Post by mokshus on 2011-06-22
Ok, so I had run localepurge without editing any of the material and now the systems seem to be running again normally. Thanks for the prompt, I'll mark it solved

---

### Post by e79 on 2011-06-23
>  I apologize for my ignorance, I am trying to learn more about the system.     Fear not and do not apologize as there is no shame to have because you are learning, we are all learning at some point and will never stop to  :P

> Ok, so I had run localepurge without editing any of the material and now  the systems seem to be running again normally. Thanks for the prompt,  I'll mark it solved     I'm glad the issue is now resolved, do not hesitate if you encounted other problems, the community is here for that !

Regards

e79

---

