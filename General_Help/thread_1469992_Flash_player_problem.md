---
title: "Flash player problem"
date: 2010-05-02
forum: General Help
---

### Post by RedSingularity on 2010-05-02
Has anyone noticed with the new 10.4 release and firefox 3.6.3, that flash is not working correctly?  Videos do play fine but I have noticed that pausing the video, replaying the video, or even skipping around in the video does not work.  Am I alone or is someone else having this problem?  I may try downgrading firefox and see if it helps.

---

### Post by lovinglinux on 2010-05-02
If you are on 64bit system, install 64bit flash.

See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Lanser on 2010-05-02
Similar problem here. Karmic 9.1 Updated to latest version of flash listed in synaptic and Firefox 3.5.9 won't run flash content at all. Been toggling between two ubuntu builds to identify the problem. No luck so far.

---

### Post by lavinog on 2010-05-03
> **Lanser said:**
> Similar problem here. Karmic 9.1 Updated to latest version of flash listed in synaptic and Firefox 3.5.9 won't run flash content at all. Been toggling between two ubuntu builds to identify the problem. No luck so far.

This is considered thread hijacking...your problem has nothing to do with the original poster's problem.  The OP is running 10.04 and claims that flash works but has issues, you are running 9.10 and claim that it doesn't work at all.  I am not trying to be rude, but thread hijacking causes confusion and can complicate the issue further.

It is always a good idea to start a new thread for your own issues.
Also it is a good idea to specify if you are using 32bit ubuntu or 64bit when dealing with flash issues.  To expand on what lovinglinux mentioned:
64bit flash is in alpha stage.  Therefore it isn't in the repositories...instead the 32 bit flash gets installed with a 32bit wrapper...this wrapper has many stability issues.  So if you have a 64bit install you should manually install the 64bit alpha version (it is much better)
There are a couple of how to's on the forum for installing it.

---

### Post by RedSingularity on 2010-05-03
That makes sense, I will try it now.  Thanks guys.

---

### Post by RedSingularity on 2010-05-03
Installing 64bit plugin solved the problem.

---

