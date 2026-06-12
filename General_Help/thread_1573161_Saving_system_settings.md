---
title: "Saving system settings"
date: 2010-09-12
forum: General Help
---

### Post by smudge12b on 2010-09-12
I am running Lucid with two monitors. I can set the system up so that screen two is 'to the right' of screen one. The problem is, when I turn off and on again the setting is lost and both screen display the same image and I have to go back into System Settings to set it up again. How do I make this change persist?
 
Thanks in advance.

---

### Post by Lukas666 on 2010-09-12
If you have an NVidia card then you should have "Nvidia X server settings" under System->Administration.

Have you tried that?

---

### Post by HermanAB on 2010-09-12
Have a look in xorg.conf.  There is probably a syntax error in there.

---

### Post by Lukas666 on 2010-09-12
> **HermanAB said:**
> Have a look in xorg.conf.  There is probably a syntax error in there.

"Nvidia X server settings" can generate and write to xorg.conf. I would not recommend a newbie to edit it manually.

---

### Post by smudge12b on 2010-09-12
> **Lukas666 said:**
> If you have an NVidia card then you should have "Nvidia X server settings" under System->Administration.

Have you tried that?

I found the problem, for what ever reason the Nvidia xserver wasn't there. After installing the Nvidia driver I got it and managed to set it up properly.

Thanks for your help

---

