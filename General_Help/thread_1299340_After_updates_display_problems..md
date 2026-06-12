---
title: "After updates display problems."
date: 2009-10-23
forum: General Help
---

### Post by koopman on 2009-10-23
So the updater came up a couple days ago, so I installed the prompted updates w/o bothering to see what was beeing updated, and after restarting, I had some serious display issues.  I got an error saying that the display driver could not load.  I had to load in low res mode to get anything working again.  I reinstalled the Nvidia drivers via Envy (previously I used the Nvidia installer to get to 185.18.36) and got Ubuntu to load normally again.  Everything seems fine now accept I can't enable the "Extra" visual effects to turn on and when I try to run the awn dock I get a "Warning: Screen isn't composited.  Please run compiz (-fusion) or another compositing manager" error message.  I've done a bit of searching around and can't find anyone who has had simillar probles that seems to relate to this at all.  

System specs
Ubuntu 9.04
Comapl FL 90 notebook
Nvidia 8600GTm

---

### Post by ptrinder64 on 2009-10-24
Yep - I've got similar problems.

I didn't get the initial driver errors that you did, but I can no longer enable desktop effects at the 'extra' level. This was after an update last week.

Have you tried loading up as a different user? For some reason my wife's account seems to work fine with Compiz running as it should do, but my account doesn't. 

When I run compiz in the terminal on my account I get the following error:

```
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

When I do the same in my wife's account it seems to run perfectly, although the following entry in the terminal looks suspect to me:

```
*** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x09b21868 ***
```

Does anyone have any ideas? I'm running Ubuntu 9.04 with an Nvidia GeForce 8400 GS and NVIDIA Driver 180...

---

### Post by koopman on 2009-10-25
Come to think of it, what update to any linux distrib requires reboot?  I thought no down time to an update was one of the many perks.

---

### Post by slamMaster on 2009-10-26
The update you ran was probably the same one I did, that installed the new linux kernel.  I got it to work if I booted up into the old kernel, but that screwed with my virtual machines.

I guess the nVidia driver doesn't update automatically with the new kernel, while my vmware and some other programs do.  It should be fixable by re-building the linux kernel, but we shall see.

Could you post how exactly you reinstalled nvidia?

---

### Post by ptrinder64 on 2009-10-27
I may have stumbled across the solution to getting desktop effects working again. I noticed that when I logged into the user for whom Compiz was working, the backend preference was set to **GConf Configuration Backend**. When I logged into the user for which Compiz was not working, this was set to **Flat-file Configuration Backend**. This is located in **System > Preferences > CompizConfig Settings Manager** and then click on **Preferences** which is located just above **Advanced Search** which in turn is above the close button. Change the backend configuration to GConf.

With this changed, I then came across this thread [http://ubuntuforums.org/showthread.php?t=1232865]("http://ubuntuforums.org/showthread.php?t=1232865") which basically states to go into gconf (**Applications > System Tools > Configuration Editor**) then select **Apps > Metacity > General** and unticking the **Compositing_Manager** box.

Now go back to the **Appearances** option and click on **Extra**.

This fixed it for me. Let me know if it works for you, or if you need further explanation.

---

### Post by ptrinder64 on 2009-10-29
By the way Koopman - when downloading system components like the Linux headers it is common to have a restart.

---

