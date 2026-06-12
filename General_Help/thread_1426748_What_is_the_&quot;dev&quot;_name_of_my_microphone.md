---
title: "What is the &quot;dev&quot; name of my microphone?"
date: 2010-03-10
forum: General Help
---

### Post by lildigiman on 2010-03-10
I have VLC 1.0.2 installed and I want to Stream my microphone, but unlike the Windows version of VLC, there is no drop-down box selection to choose a specific microphone. I have tried "/dev/audio/" and a couple others as well only to get the error 

"Your input can't be opened:
VLC is unable to open the MRL 'v4l2://'. Check the log for details."

I can't find any information on how to figure out the dev name of my devices.

Maybe I'm not setting up the stream properly elsewhere...

Any help is greatly appreciated!

---

### Post by bobcollard on 2010-03-10
> **lildigiman said:**
> I have VLC 1.0.2 installed and I want to Stream my microphone, but unlike the Windows version of VLC, there is no drop-down box selection to choose a specific microphone. I have tried "/dev/audio/" and a couple others as well only to get the error 

"Your input can't be opened:
VLC is unable to open the MRL 'v4l2://'. Check the log for details."

I can't find any information on how to figure out the dev name of my devices.

Maybe I'm not setting up the stream properly elsewhere...

Any help is greatly appreciated!
You might find it under Device Manager, not sure if that is under system menu in Gnome.

---

### Post by lildigiman on 2010-03-10
Thanks! I didn't think of that. I went to Ubuntu's software center and found a device manager, and it does give the dev name. Unfortunately My problems aren't solved... I guess this means that I need to fill in something for the VIDEO capture device in VLC, even though I don't want to stream any video...

Any Ideas?

---

### Post by bobcollard on 2010-03-10
> **lildigiman said:**
> Thanks! I didn't think of that. I went to Ubuntu's software center and found a device manager, and it does give the dev name. Unfortunately My problems aren't solved... I guess this means that I need to fill in something for the VIDEO capture device in VLC, even though I don't want to stream any video...

Any Ideas?
Yes, probably a dependency problem.  Can't help you there.

---

