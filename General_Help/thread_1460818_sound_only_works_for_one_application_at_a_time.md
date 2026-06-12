---
title: "sound only works for one application at a time"
date: 2010-04-23
forum: General Help
---

### Post by thegreenblob on 2010-04-23
Hey everyone, I installed Kubuntu 10.04 (RC 1, I believe) yesterday, and I'm having a problem with sound, sound works, so as long as I only have one application open at a time using it, this is very annoying.

I have tried messing with alsamixer to make sure nothing is muted and it is not.

Has anybody had this problem or any idea how to fix it?

If there's anymore information I can provide to help solve this problem, please let me know.

---

### Post by Untitled_No4 on 2010-04-23
I had that issue in Karmic (and so did other people) but never in Lucid.

Anyway, you can try the Karmic method to solve the issue by installing Pulse Audio.

Open konsole and run:
```
sudo aptitude install paman padevchooser paprefs pavucontrol pavumeter
```

After it installs, run ```
paprefs
```

go to Simultaneous Output tab and check the "Add Virtual output for..." checkbox. 

Hope this works.

---

### Post by thegreenblob on 2010-04-23
Thanks. That seemed to work *somewhat*.

Now I can get sound from several things at once however sound in VLC is now very jittery. And I also get this message on boot up now:

[IMG]http://img24.imageshack.us/img24/3108/snapshot1c.png[/IMG]

Any ideas?

---

