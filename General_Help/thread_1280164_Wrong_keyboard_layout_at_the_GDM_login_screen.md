---
title: "Wrong keyboard layout at the GDM login screen"
date: 2009-10-01
forum: General Help
---

### Post by Malfet on 2009-10-01
Please, help. For some reasons keyboard layout at the GDM login screen changed and now I can not login to the system. Xorg.conf is almost empty (I'm running Ubuntu 9.04), I've put there the code to define the correct layout, bud it did not help.
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xfree86"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
EndSection

```
I have found information that in recent versions xorg.conf became almost useless, but how then can I change the keyboard layout for the GDM screen?

---

### Post by StuartN on 2009-10-02
> **Malfet said:**
> ```
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
```

This is a 105-key German keyboard. You can edit the "de" to any other valid country code. You will need to start up in recovery mode to edit the file if you can't log in.

Also, in System->Preferences->Keyboard->Layouts it is a good idea to add another combination (e.g. Both-Shifts) to Layout Switching because the Both-Alts combination does not work, then pressing both shift keys will cycle through the installed layouts.

---

