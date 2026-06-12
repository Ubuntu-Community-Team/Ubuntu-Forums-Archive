---
title: "Make Nautilus Always Launch with --no-desktop option"
date: 2010-11-05
forum: General Help
---

### Post by beastrace91 on 2010-11-05
If I am using LXDE or another non-Gnome desktop and want to use Nautilus as the file viewer it needs to be launched with the --no-desktop option (so nautilus does not load it's desktop image under the other DE).

I know there is a way to make it so whenever nautilus is launched it will not load the desktop (even if you do not pass the --no-desktop argument) but I do not recall how I did this last time! I believe it was a gconf value...

Anyone know what this setting is/how I can accomplish what I am looking to do?

Regards,
~Jeff

---

### Post by J V on 2010-11-05
theres a gconf varible for that... /apps/nautilus/preferences/show_desktop

---

### Post by beastrace91 on 2010-11-05
> **J V said:**
> theres a gconf varible for that... /apps/nautilus/preferences/show_desktop

Ahh yes, thank you for that. For those wondering you can set this value from the CLI with the gconftool-2 command. Setting it to "false" makes it not show the desktop anymore when running *nautilus* :)

Cheers,
~Jeff

---

