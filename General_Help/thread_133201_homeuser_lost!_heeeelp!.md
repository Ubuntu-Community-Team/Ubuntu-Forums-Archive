---
title: "/home/user lost! heeeelp!"
date: 2006-02-19
forum: General Help
---

### Post by branco on 2006-02-19
I was messing around with chroot tutorial, and I decided it didn't work the way I wanted to. So I tried to remove the /var/chroot directory. If only I had not forgotten that /home was mounted in /var/chroot/home.... :cry: 

Anyways, I did a

```
sudo /var/chroot -rd 
```

After a while, the response was something to the effect that /home is on a busy device so it couldn't be removed. (I don't know if it makes any difference, but /home is on another HDD in case I needed to reinstall and still keep my prefs...)

So, the contents of the home folder along with all my precious photos (I was gonna backup, I swear!) is gone... I've just got a baby girl, and I already had like 400+ photos of her in there.

I tried 'recover' to see if it helps, but the partition is ext3, and 'recover' can do nothing about it. I also tried a demo version of an commercial Windoze app (I can boot into WinXP at any time), but it yielded no results.

Now, I've seen threads like this before, but none of them were answered. Should I just 'learn my lesson' and go on, or there is a way?

BTW, please don't be hard on me for not having been thorough with searching and googling. I already feel like I'm gonna cry and I just barely managed to pull myself together and post this one after all those failed attempts.

---

