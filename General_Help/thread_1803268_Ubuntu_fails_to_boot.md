---
title: "Ubuntu fails to boot"
date: 2011-07-13
forum: General Help
---

### Post by inhumangeek on 2011-07-13
*Ubuntu 11.04*

Last night I was in the process of re-installing some drivers (libimobiledevice - which is used to talk to my phone via USB) and my PC crashed (went back out to the command line - no desktop environment). Now when it boots I get a message about my graphics not being detected, and I get several options: To temporarily start Ubuntu in a graphics mode to re-detect the hardware, to restart X, to troubleshoot, to exit to the console. (I think that's it). "Troubleshoot" takes me to another menu which doesn't do anything when I click on its options, so I go with the first one.

This then displays another dialogue box saying words to the effect of "Please wait a minute whilst your hardware is re-detected", which just sits there forever. There is an "OK" button which if I click it, takes me to the usual Ubuntu loading screen, which also just sits there looping. If I then hit escape I can see the boot text - the last action which was taken was to load the "Crashplan" engine (followed by "OK"). Crashplan is an online backup service which I just installed.

So I'm stuck as I don't really know how to fix this error... I could try choosing the console option but I wouldn't know what to do next - similarly with the Live CD - I could boot to it but then what? I suspect graphics is not the issue here - I'm wondering if it's Crashplan... either way is there an equivalent to the Windows "Safe" mode I can boot to, to uninstall Crashplan and perhaps complete the re-installation on libimobiledevice, or restore my system back to how it was? Is there an Ubuntu "repair" mode?

Any suggestions gratefully received &#8211; bearing in mind I&#8217;m a near-beginner with Ubuntu. I really want to use Ubuntu but it's issues like this (which I could easily fix or at least know where to start in Windows) which really put me off and make me want to go back to Windows.

Thanks.

---

### Post by inhumangeek on 2011-07-13
Hmm not sure where all those stars came from. Odd. Now removed

---

### Post by Mark Phelps on 2011-07-13
> **inhumangeek said:**
> *Ubuntu 11.04*... is there an equivalent to the Windows "Safe" mode I can boot to ...

Yes ... when booting, hold down the SHIFT key.  That should force a GRUB menu.  Then select the top-most Recovery Mode option.

That should eventually display a list of options, select the one to repair broken packages.

You can also boot into a command shell.

---

### Post by inhumangeek on 2011-07-13
Thanks.

A this helped me diagnose... had to reinstall gnome.Working now. So happy!!

[http://ubuntuforums.org/showthread.php?t=178720](http://ubuntuforums.org/showthread.php?t=178720)

---

