---
title: "Need terminal help for rooting my evo, stuck in the middle."
date: 2010-09-14
forum: General Help
---

### Post by hortstu on 2010-09-14
So I'm not fluent in the linux terminal. I'm basically illiterate, deaf and dumb. So here I am trying to root using this tutorial, How To Root The HTC EVO ~ Part-1 \0/

[http://forum.xda-developers.com/showthread.php?t=690762](http://forum.xda-developers.com/showthread.php?t=690762)

Anyway I'm at this step,

    - At this point it will boot into a rooted rom.
    - YOU ARE NOW ROOT!!!
    - rename the PC36IMG.zip on your sdcard:
    - plug your phone into a usb port on your desktop and do:

```
adb shell mv /sdcard/PC36IMG.zip /sdcard/root-PC36IMG.zip
```

I may be root but I had a problem and had to redo this step... my sdcard was not being recognized. After reflashing/ updating I was able to access it again.  S is still off on the boot screen.

Now this rename the zip file step... I'm thinking if I rename it the code I'm supposed to enter isn't going to work. What should I rename it to?

How should I enter this code? first off my sd card isn't called sdcard it's called an 8 digit number.

I tried this without changing the name of the zip file. I'm thinking I don't have the locations right because I know the file is in there.

```
mike@mike-laptop:~/AndroidSDK/tools$ ./adb shell mv /####-####/PC36IMG.zip /####-####/root-PC36IMG.zip
failed on '/####-####/PC36IMG.zip' - No such file or directory
mike@mike-laptop:~/AndroidSDK/tools$
```

I need some direction to get to the next step.
Thanks

---

### Post by hortstu on 2010-09-14
Is there a more appropriate place for this question.  I'm really stuck.

---

