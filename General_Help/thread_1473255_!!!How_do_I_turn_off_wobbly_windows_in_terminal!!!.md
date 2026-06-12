---
title: "!!!How do I turn off wobbly windows in terminal?!!!"
date: 2010-05-05
forum: General Help
---

### Post by wwwolf on 2010-05-05
OMG! I was tweakng the desktop effects in kubuntu and adjusted the stiffness slidder to max out wabbly windows so I could compare it to more stiffer option. It is only supposed to wobble when the window is moved but as soon as I hit the apply button the window started wobbling all over the place!:mad: So fast, that I can barely tell what window it is! It is impossible for me to open any windows without them flickering all over the place. I will not be able to fix this inside KDE.

Does anyone know of a command-line option to turn desktop effects off?
Is there a desktop configuration file somewere I can edit w/ nano?

PLEASE help! I am having to write this on windows7 because I can't use any windows in linux.:mad:

---

### Post by darolu on 2010-05-05
You can always kill compiz; press Control + Alt + F1, it will get you a terminal mode, there you can kill compiz with "sudo killall compiz", it may not work though so run a "ps -u <username>" look for compiz and use its ID number to kill it with "sudo kill -kill <idnumber>", go back to your desktop with Ctrl+Alt+F7

---

### Post by wwwolf on 2010-05-05
I don't have compiz installed so I am not sure which program is running my desktop effects.

I also can't find the configuration file to edit. It seems like little bits of configurable text are in all sorts of files and one can get easily lost in the file system.

Would be great if there was a desktop.config file you could edit or something.

I can't believe that a simple effect could render your OS useless without a count-down timer to accept the changes or not. Maybe something like that could be included in the future.

I'M STILL STUCK!

Please help :(

---

### Post by wwwolf on 2010-05-05
Thank you for the suggestion. I found a solution although it took a while to find. I'm not the only one.

While it is not a command-line quick fix, you can turn off rendering for each active window by clicking shift/left-Alt/F12 at the same time.

That's a neat trick and from looking at a lot of other post it is not that well-known. ):P

---

