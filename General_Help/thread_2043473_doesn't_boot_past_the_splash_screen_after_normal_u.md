---
title: "doesn't boot past the splash screen after normal update."
date: 2012-08-16
forum: General Help
---

### Post by S_p_or_t_o on 2012-08-16
howdy

ubuntu studio 12.04 precise x64
ati raedon hd 5700 graphics card.

after the last update i did, it won't boot past the studio splash screen. the spinning circle disappears and never got to a login screen (i let it run for an hour like that before calling it dead).

i saw it was an xorg update, but nothing in /var/logs tip me off to anything wrong.

i'm able to mount my encrypted home folder via the recovery root prompt and have tried some apt-get and dpkg tricks with no change.

i tried startx and ctrl-alt-f7, but the screen goes black. i'm able to crtl-c and crtl-alt-f1 back to the prompt.

any ideas would be appreciated.

i'm not sure if i have a session, gui or other problem.


edit 1: i'll have to try this [http://ubuntuforums.org/showthread.php?t=1743966](http://ubuntuforums.org/showthread.php?t=1743966) when i get home from work lol

---

### Post by S_p_or_t_o on 2012-08-16
so sudo X -configure gave me an error, so i tried fglrxinfo and got some null error.

null? as in not there? i think to update borked my video driver - the fix for me taken from [https://help.ubuntu.com/community/BinaryDriverHowto/ATI/](https://help.ubuntu.com/community/BinaryDriverHowto/ATI/)

```
sudo apt-get install fglrx fglrx-amdcccle

sudo aticonfig --initial
```

NOW, it boots fine except the pc goes to stand by after a minute :(


edit: running memtest

---

