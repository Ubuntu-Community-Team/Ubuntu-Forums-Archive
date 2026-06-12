---
title: "kazam wont start"
date: 2012-08-03
forum: General Help
---

### Post by sdpagent on 2012-08-03
Dear all, I get the feeling this is probably an error on my part, because kazam was working just this morning, but won't anymore, even after restarts, and trying to uninstall it and re-install.
Error output:
```
stuart@stuart-H61M-S2PV:~$ kazam
Traceback (most recent call last):
  File "/usr/bin/kazam", line 74, in <module>
    appWindow = KazamApp(datadir, args.debug)
  File "/usr/lib/python2.7/dist-packages/kazam/app.py", line 238, in __init__
    self.restore_state()
  File "/usr/lib/python2.7/dist-packages/kazam/app.py", line 578, in restore_state
    self.volumebutton_audio2.set_value(audio2_vol)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
ValueError: %f not in range %f to %f

```

I cant really understand that, but it looks like there is an error with a value somewhere?
If i run kazam -d I get the same error after a bunch of  pulseaudio text.

Any help appreciated.
Stu

---

### Post by sdpagent on 2012-08-03
I 'fixed'the issue by going to my volume controller, switching output device to headphones, starting kazam, worked, then tried back on analogue output again, and it works? Is this worth reporting to their launchpad? Has anyone else had such issues?

Printscreen of sound controller options:
[http://img1.uploadscreenshot.com/images/orig/8/21501153158-orig.png](http://img1.uploadscreenshot.com/images/orig/8/21501153158-orig.png)

---

### Post by udatatec on 2012-10-31
its a bug:

[https://bugs.launchpad.net/ubuntu/+source/kazam/+bug/983827](https://bugs.launchpad.net/ubuntu/+source/kazam/+bug/983827)


simple fix is to go to your audio input settings and make sure all the inputs are at a low level NOT 0 or mute.

Then restart Kazam

---

