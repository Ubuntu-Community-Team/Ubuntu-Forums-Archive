---
title: "VLC + Firefox crash? (Not plugin)"
date: 2010-08-01
forum: General Help
---

### Post by Lucky75 on 2010-08-01
Hi!

I've noticed fairly often that sometimes when I'm both using firefox and watching a movie in VLC that my entire system locks up for a few minutes, after which both VLC and Firefox are closed and everything is fine again. Any idea what's causing the problem? I have a feeling it's firefox, but I'd like to prevent this from happening. My system also seems to become more and more laggy the longer firefox is open, although that might just have to do with leaking extensions and might be unrelated.

Thanks!

---

### Post by lovinglinux on 2010-08-02
Could be leaking extensions indeed.

See [http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com) for Firefox Optimization and Troubleshooting tutorials.

---

### Post by Lucky75 on 2010-08-02
But why would it only specifically crash firefox and VLC, even when I don't have any pages watching videos or playing sounds or anything in firefox? I can understand firefox slowing down and even crashing on its own, but not locking up the whole system and taking VLC down with it.

---

### Post by lovinglinux on 2010-08-02
> **Lucky75 said:**
> But why would it only specifically crash firefox and VLC, even when I don't have any pages watching videos or playing sounds or anything in firefox? I can understand firefox slowing down and even crashing on its own, but not locking up the whole system and taking VLC down with it.

I think this problem has nothing to do with Firefox. Most likely that rendering the video on VLC is eating too much CPU cicles, overheating the CPU and then causing the applications to become unresponsive, including Firefox.

Are you watching 720p or 1080p videos?

---

### Post by Lucky75 on 2010-08-03
Nope, and I have a core2duo e6600 with 3 gigs ram....There's no way it should be eating up the cpu cycles that much, even my crappy windows laptop can watch videos and have firefox open at the same time. 

Where would I look for crash logs?

---

### Post by Lucky75 on 2010-08-04
bump

---

### Post by lovinglinux on 2010-08-04
> **Lucky75 said:**
> Nope, and I have a core2duo e6600 with 3 gigs ram....There's no way it should be eating up the cpu cycles that much, even my crappy windows laptop can watch videos and have firefox open at the same time. 

Where would I look for crash logs?

System >> Administration >> Log File Viewer

---

### Post by Lucky75 on 2010-08-04
Thanks, though I was actually more asking if there were logs in particular that I could look at when they crash (would I look at kernel logs, or would there be any logs for FF or VLC?) Guess I should have been clear...at all..instead of the levels of opaque I reached in my last post :)

I never actually realized that the log viewer was even there though haha, I've just been using vi to read them in /var/log

---

### Post by lovinglinux on 2010-08-04
> **Lucky75 said:**
> Thanks, though I was actually more asking if there were logs in particular that I could look at when they crash (would I look at kernel logs, or would there be any logs for FF or VLC?) Guess I should have been clear...at all..instead of the levels of opaque I reached in my last post :)

I never actually realized that the log viewer was even there though haha, I've just been using vi to read them in /var/log

I don't think there would be any logs specifically for Firefox or VLC. Nevertheless, I never needed them here, so I could be wrong. Perhaps would be easier to start both from a terminal and check the errors in the output.

---

### Post by Lucky75 on 2010-08-04
Yeah, unfortunately this happens very randomly and is difficult to duplicate. I suppose I could just continuously loop watching a movie and having firefox open or something.

---

