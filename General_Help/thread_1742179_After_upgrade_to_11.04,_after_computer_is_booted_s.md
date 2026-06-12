---
title: "After upgrade to 11.04, after computer is booted speakers emit high pitched noise"
date: 2011-04-28
forum: General Help
---

### Post by ejn114 on 2011-04-28
Hi,

I upgraded to 11.04 today, and ever since the upgrade my speakers (and headphones; any audio device) emit a high-pitched shriek when connected to the computer.  This only happens after I enter my password on the login screen, and only in Ubuntu.  There's no problem when I boot Windows.

The sound is very high pitched and my speakers play no other generated sounds while emitting this static.  Obviously, I'd like to be able to have sound and listen to my music, so this needs to be fixed.  Does anyone have any suggestions?

Thanks,

ejn

---

### Post by ejn114 on 2011-04-29
Does anyone have any ideas?

---

### Post by sdowney717 on 2011-04-29
remove all the sound pulse alsa etc... with their configuration files.
Then reinstall the sound files.

---

### Post by ejn114 on 2011-04-29
What's the best way to do that?  Sorry, I'm not very good at this.

---

### Post by TheLocust830 on 2011-04-29
I was just having the same problem. I opened a terminal and started alsamixer. The front mic boost was for some reason set to 100%. I turned it all the way down, the hissing stopped, and sounds now sound right. The front mic should still work, I didn't turn down the volume, just the boost, but I haven't yet tested that. Hopefully that solves it for you.

---

### Post by KegHead on 2011-04-29
Hi!

system...preferences...sound..lots of parameters.

KegHead

---

