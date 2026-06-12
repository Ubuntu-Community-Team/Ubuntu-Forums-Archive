---
title: "hotkey assignment.. simple question"
date: 2009-06-30
forum: General Help
---

### Post by heyyy on 2009-06-30
i was playing around with keyboard shortcuts and changed some of them by mistake...
could someone tell me the default shortcut key for : "show the panel's main menu"

just go to the System->Preferences->Keyboard Shortcuts->Desktop->show the panel's main menu and post the shortcut

thanks in advance

---

### Post by drs305 on 2009-06-30
ALT-F1 ? Is that the menu you are looking for?

OK, I see what you are asking: Yes, it shows ALT+1

You can also find it by going to:
```

gconf-editor /apps/metacity/global_keybindings/panel_main_menu

```

If you mess up the command and want to restore the default, right click the value and select "Unset key".

---

### Post by heyyy on 2009-06-30
> **drs305 said:**
> ALT-F1 ? Is that the menu you are looking for?

OK, I see what you are asking: Yes, it shows ALT+1

You can also find it by going to:
```

gconf-editor /apps/metacity/global_keybindings/panel_main_menu

```

If you mess up the command and want to restore the default, right click the value and select "Unset key".

many thanks
worked fine

---

