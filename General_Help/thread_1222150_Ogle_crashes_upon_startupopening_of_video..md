---
title: "Ogle crashes upon startup/opening of video."
date: 2009-07-24
forum: General Help
---

### Post by gksudo on 2009-07-24
I'm running in ubuntu 9.04, and after I installed the Ogle video player, I decided to watch a video. I went to the directory where the video was at, and right click, open with.. "ogle."
For a split second the ogle window pops up and then closes. I then try to go into the terminal to use ogle to see the error message. Same thing, immediately the window opens then closes. But since I'm in the terminal, it came with this output.

xscreensaver-command not found.
SNDCTL_DSP_GETCHANNELMASK: Invalid argument
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  57
  Current serial number in output stream:  57

Any help would be much appreciated. 
Side note:I never had this problem in ubuntu versions:8.04, and 8.10
Thanks.

---

### Post by gksudo on 2009-07-24
> **gksudo said:**
> I'm running in ubuntu 9.04, and after I installed the Ogle video player, I decided to watch a video. I went to the directory where the video was at, and right click, open with.. "ogle."
For a split second the ogle window pops up and then closes. I then try to go into the terminal to use ogle to see the error message. Same thing, immediately the window opens then closes. But since I'm in the terminal, it came with this output.

[COLOR=Red]xscreensaver-command not found[/COLOR]
SNDCTL_DSP_GETCHANNELMASK: Invalid argument
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  57
  Current serial number in output stream:  57

Any help would be much appreciated. 
Side note:I never had this problem in ubuntu versions:8.04, and 8.10
Thanks.
[COLOR=Black]I fixed the xscreensaver issue by going to the synaptic package manager, and installing xscreensaver. I still get the rest of the error though. And the window closes as soon as I open it.So, It's paritaly fixed. but still, it's crashing.
[/COLOR]

---

