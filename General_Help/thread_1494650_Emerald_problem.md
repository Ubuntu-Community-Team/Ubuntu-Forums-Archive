---
title: "Emerald problem"
date: 2010-05-27
forum: General Help
---

### Post by Cant on 2010-05-27
Emerald is suppoused to be my window manager but now when I log in I see that Compiz has taken over and I have to open Terminal and use the --replace command. But when I close Terminal Emerald suddenly exits and I have no window manager, so I have to go back into Terminal, type the command again and the only way Emerald stays is if I don't close Terminal.

---

### Post by dv3500ea on 2010-05-27
Emerald is not a window manager, just a window decorator.
To fix your problem:
Ensure [compizconfig-settings-manager]("apt:compizconfig-settings-manager") is installed.
Go to System -> Preferences -> CompizConfig Settings Manager.
Under effects click Window Decoration, and ensure it is enabled.
Set the command (text box) to ```
emerald --replace
```

---

### Post by Cant on 2010-05-27
> **dv3500ea said:**
> Emerald is not a window manager, just a window decorator.
To fix your problem:
Ensure [compizconfig-settings-manager]("apt:compizconfig-settings-manager") is installed.
Go to System -> Preferences -> CompizConfig Settings Manager.
Under effects click Window Decoration, and ensure it is enabled.
Set the command (text box) to ```
emerald --replace
```

Got it, thanks.

---

