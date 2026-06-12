---
title: "Fade Timer"
date: 2009-07-24
forum: General Help
---

### Post by Tteddo on 2009-07-24
This is a small thing, but I can't find where to set it. I frequently put Ubuntu on older computers and when the OS is doing something frequently the window will fade like it is frozen (but it's not) before it gets done (seems like it is set for 500ms or so). I want to change the time to fade (so to speak) so it is longer and won't confuse the user. These do have Compiz on it so I can use the settings manager to set it. I just can't find what it is called.

---

### Post by CatKiller on 2009-07-24
They fade when the application that created the window is no longer responding to input from the window manager (usually because the application is busy with something else). The way to stop this happening is to use a better computer.

However, you can stop this indication that the application is not currently responding to input with the Fading Windows plugin. Simply uncheck the Dim Unresponsive Windows setting.

---

### Post by Tteddo on 2009-07-24
Well, the idea here is that by putting Ubuntu on it they don't need another computer:D

In Compiz Config there isn't a setting for that under the Fading Windows Plugin. Where can I find that? I also searched for Dim Unresponsive Windows in gconf editor?

This is on Hardy if that matters

---

### Post by CatKiller on 2009-07-24
> **Tteddo said:**
>  This is on Hardy if that matters

It means that I can't really help you find it. Both the computers here are on Jaunty now.

Don't forget that you'll need to check "Search also in key names" if you're trying to find a particular key in gconf-editor. And a search for "dim" is more likely to find results than "Dim Unresponsive Windows," since that's in the description.

If it helps at all, the Jaunty key is /apps/compiz/plugins/fade/screen0/options/dim_unresponsive.

---

### Post by Tteddo on 2009-07-25
Thanks! That's where it was in Hardy too.

---

