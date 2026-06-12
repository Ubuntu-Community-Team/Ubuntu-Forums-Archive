---
title: "No Sound"
date: 2012-03-11
forum: General Help
---

### Post by Kissell on 2012-03-11
I have always had sound on this machine...  but the X server wouldn't start after I rebooted, and I had to completely uninstall and reinstall the graphics drivers...  

Ever since then, I get to my Unity GUI just fine...  but I have no sound...  when I click on the sound icon in the top bar, anytime I try to increase the volume from nothing, the app closes.

I think this might be a file permissions issue...  but I'm not sure where.  I had a script that had some fat fingers typing in it, and it resulted in some permissions changes that were unintended.  My guess is that's causing this, sound always worked fine before, after a fresh reformat it always works...  but I'd like to not have to do that.

---

### Post by Kissell on 2012-03-11
> lspci|grep Audio
```

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
05:00.1 Audio device: ATI Technologies Inc RV710/730
```

---

### Post by raja.genupula on 2012-03-11
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

they are good guides

---

