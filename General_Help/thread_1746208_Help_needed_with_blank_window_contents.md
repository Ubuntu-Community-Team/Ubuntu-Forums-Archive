---
title: "Help needed with blank window contents"
date: 2011-05-01
forum: General Help
---

### Post by LandR on 2011-05-01
I have a problem. I can't maximise windows or make them larger than a certain size.  When windows are small, it's fine there contents show OK. When I either maximise them or drag the resize corner in the bottom right they go blank.  Here's a couple of screenshots to show what I mean:  

Trying to open a spreadsheet: [IMG]http://www.speed-shot.co.uk/images/openspreadsheet.png[/IMG]  
Trying to have a larger firefox window: [IMG]http://www.speed-shot.co.uk/images/blankmoz.png[/IMG]  
Trying to open FileZilla (it starts up as a large window so the contents disappear) [IMG]http://www.speed-shot.co.uk/images/blankfilez.png[/IMG]  
How can I fix this ?  

Until I can fix this the OS is unusable.

Thanks,

---

### Post by LandR on 2011-05-01
Anyone ?

---

### Post by marvmen21 on 2011-05-01
> **LandR said:**
> Anyone ?

Exactly same issue here, Any ideas?

---

### Post by LandR on 2011-05-01
From some googling I found that the problem MAY be resolved by changing the version of the nVidia drivers from current [Recommended] to 173.  You can do this by going into System > Available Drivers.  I don't know if this works or not though. I'm going to try it now.

---

### Post by r-senior on 2011-05-01
Do you both have Nvidia video cards? If so, probably this bug:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445)

Workarounds are to use the Nouveau free driver for Nvidia cards, or downgrade to v173 of the Nvidia driver.

Check what you have in the "Additional Drivers" app. You may be able to fix it from there, or you may need to do it in Synaptic. If you aren't sure what you are doing, please post for advice.

---

### Post by LandR on 2011-05-01
Switching back to v173 seems to have fixed this issue for me.  Thanks.

---

