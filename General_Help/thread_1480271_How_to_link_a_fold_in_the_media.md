---
title: "How to link a fold in the media"
date: 2010-05-11
forum: General Help
---

### Post by ganzheng on 2010-05-11
Hi,

I use ln -s to create a symbolic folder in /home/ to direct a folder in the media.

But it appeared the link is broken. It also said "This link cannot be used, because its target "./media/StudyResearch/" doesn't exist."

Thanks for help!

---

### Post by gmargo on 2010-05-11
> **ganzheng said:**
> "This link cannot be used, because its target "./media/StudyResearch/" doesn't exist."

Did you copy the error correctly?  There's a leading dot in the path, so you probably made a mistake typing the link command.

---

### Post by ganzheng on 2010-05-11
Thanks, I wrote the wrong location, so now it works.

But, there is still another problem. When I start up my computer again, that symbolic folder seems to be broken again.

I guess maybe the target disk hasn't been mounted yet. So how do I make that disk mount automatically after turning on the computer?

I am a really novice for Ubuntu

---

### Post by nopain_nogain_e on 2011-06-20
> **ganzheng said:**
> 
But, there is still another problem. When I start up my computer again, that symbolic folder seems to be broken again.


I'm having the same problem.
Anyone can help, please?

---

### Post by muteXe on 2011-06-20
You need to add it to your fstab file. Google fstab and mounting.

---

