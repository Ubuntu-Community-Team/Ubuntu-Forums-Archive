---
title: "I can't use the mic."
date: 2010-10-24
forum: General Help
---

### Post by 006ruler on 2010-10-24
There is a microphone on my laptop, and it no longer works with Ubuntu. I just installed Lucid Linx, and the mic worked before i started with Lucid.
Is there any way to get the mic back up and working? if so, that would be great. Thanks!

---

### Post by coffee412 on 2010-10-24
> **006ruler said:**
> There is a microphone on my laptop, and it no longer works with Ubuntu. I just installed Lucid Linx, and the mic worked before i started with Lucid.
Is there any way to get the mic back up and working? if so, that would be great. Thanks!


Make sure you have the PulseAudio Device chooser installed, Volume control they will show up in Applications/Sound & Video. Go in and see if your mic is there under inputs. Make sure its selected. If you dont see it then try running alsamixer in the term window and make sure its turned on. If its not there then it might be a driver issue.

My mic is in my webcampro 9000 and I have to select it once on new installs. Selecting it once should do it.

Hope that helps.

---

### Post by 006ruler on 2010-10-24
woohoo!
thank you very much.
i can now screw around again!
it's very important.
thanks!

---

### Post by coffee412 on 2010-10-24
> **006ruler said:**
> woohoo!
thank you very much.
i can now screw around again!
it's very important.
thanks!

NP glad I could help :)

Makes you wonder why they dont install by default when you install Ubuntu. But its the same for Fedora too. :confused:

Have fun!

Be sure to mark your post SOLVED for others

---

