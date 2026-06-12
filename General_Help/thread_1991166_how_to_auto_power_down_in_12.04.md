---
title: "how to auto power down in 12.04?"
date: 2012-05-30
forum: General Help
---

### Post by D0natell0 on 2012-05-30
Hi, I've got a machine newly installed with Ubuntu 12.04 (64bit).

Is there a way to make it automatically power down when I hit the power button?

In Ubuntu 8.04 there was a power option where you could choose what happens when you hit the power button, i.e. suspend, hibernate etc. I can't find that option in this release.
Thanks ;)

---

### Post by kanikilu on 2012-05-30
Even though it's for 11.10, I think this askubuntu thread has a few good suggestions:

[http://askubuntu.com/questions/66723/how-do-i-modify-the-power-options-in-ubuntu-11-10](http://askubuntu.com/questions/66723/how-do-i-modify-the-power-options-in-ubuntu-11-10)

I don't use the power button to shutdown, so I haven't tried these myself...YMMV.

That said, it looks like the suggestion to modify the acpid event for "powerbtn" could be the easiest:

[http://askubuntu.com/a/84984](http://askubuntu.com/a/84984)

---

### Post by D0natell0 on 2012-06-06
Thanks, Yep works for me. Although not a user friendly nice GUI option, I went with your second recommendation and was a piece of cake. Well done and thanks again! :guitar:

---

### Post by majexy033 on 2012-06-06
Thanks for the post. I think I got it and it helped me

---

