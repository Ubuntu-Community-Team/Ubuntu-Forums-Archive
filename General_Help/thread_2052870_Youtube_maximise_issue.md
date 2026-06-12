---
title: "Youtube maximise issue"
date: 2012-09-04
forum: General Help
---

### Post by jollyrancher on 2012-09-04
Hi guys,

I am running Ubuntu 12.04 64 bit.  When I maximise a youtube clip, the whole screen goes black and a small version of the video plays in the middle.  But of course I'd like it to cover the whole screen.

Does anyone have any experience with this problem?

Thanks in advance

---

### Post by jollyrancher on 2012-09-05
> **jollyrancher said:**
> Hi guys,

I am running Ubuntu 12.04 64 bit.  When I maximise a youtube clip, the whole screen goes black and a small version of the video plays in the middle.  But of course I'd like it to cover the whole screen.

Does anyone have any experience with this problem?

Thanks in advance

Bump

---

### Post by jollyrancher on 2012-09-05
:-x

---

### Post by jollyrancher on 2012-09-09
Thanks all for your replies.  Nice to have such a helpful community.  For any one else who has this problem, I have found a solution that seems to work in 12.04:

Go to terminal:
> sudo mkdir /etc/adobe/ && cd $_
su
echo "OverrideGPUValidation=True">>mms.cfg

Close terminal and restart your web browser.  Hope this helps someone out there!

---

### Post by newb85 on 2012-09-09
You asked if anyone had experience with that problem.  If no one responded, it probably means that no one does.

I'm glad you found a solution, and it's good that you're posting it.  Two things to make it more helpful to others in the future:

[LIST]
[*]Mark the thread as solved
[*]Give a little more detail about your solution.  What are those commands supposed to do?  If you found them on another website, a link would be really helpful.
[/LIST]

---

