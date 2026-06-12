---
title: "Terminator delete key binding"
date: 2010-01-31
forum: General Help
---

### Post by mobilediesel on 2010-01-31
I've recently started using [terminator]("https://launchpad.net/terminator"). When using terminator, the delete key acts like backspace. in the ~/.config/terminator/config file I've tried:
```
delete_binding = ascii-del
```
and
```
delete_binding = delete-sequence
```
and
```
delete_binding = escape-sequence
```

Now that I looked at it a bit, it seems to only affect nano. It works properly when I use xfce4-terminal but not when I use terminator. I've even tried ```
set rebinddelete
``` in the .nanorc file.

---

### Post by Sector11 on 2010-02-18
> **mobilediesel said:**
> I've recently started using [terminator]("https://launchpad.net/terminator"). When using terminator, the delete key acts like backspace. in the ~/.config/terminator/config file I've tried:

I don't see that sequence in that file:

```
# Terminator config, see "man terminator_config" for more options
# ---------------------------------------------------------------
scrollbar_position=disabled
force_no_bell=true
background_color=#000000
foreground_color=#FFFFFF
font=Mono bold 9
allow_bold=true
palette=#2E2E34343636:#CCCC00000000:#4E4E9A9A0606:#C4C4A0A00000:#34346565A4A4:#757550507B7B:#060698209A9A:#D3D3D7D7CFCF:#555557575353:#EFEF29292929:#8A8AE2E23434:#FCFCE9E94F4F:#72729F9FCFCF:#ADAD7F7FA8A8:#3434E2E2E2E2:#EEEEEEEEECEC

# Uncomment below to enable transparency
# --------------------------------------
background_type=transparent
enable_real_transparency=true
background_darkness=0.3
```

Maybe you are using a different version than I am: terminator 0.12

s11

---

### Post by mobilediesel on 2010-02-19
> **Sector11 said:**
> I don't see that sequence in that file:


Maybe you are using a different version than I am: terminator 0.12

s11

Yeah I'm using version 0.14. Maybe I should try a previous version and see if that makes a difference.

Gah. I had to use ```
unset rebinddelete
``` in the .nanorc file. It wasn't a problem with Terminator at all!

---

