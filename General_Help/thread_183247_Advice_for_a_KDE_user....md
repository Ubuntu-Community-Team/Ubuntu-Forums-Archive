---
title: "Advice for a KDE user..."
date: 2006-05-27
forum: General Help
---

### Post by gingermark on 2006-05-27
Hey there,

I started with Linux with Warty, using GNOME obviously, and then after upgrading to Hoary I switched to Kubuntu, which I've used ever since.

It's not that I didn't like GNOME, but I found it lacking in configuration options. That said, now I am more proficient with (K)Ubuntu, I'd like to give GNOME another try, and figure as I was going to do a fresh Dapper install of Kubuntu anyway, now is a good time to give the RC for Ubuntu Dapper a go.

So, as I wait for the iso to torrent down to me, I was wondering if there were any other ex-KDE users about who knew of any references or who had any advise that might help. I don't mind learning how to edit text files if there is a certain config option I can't get via a GUI, but I currently have no idea how this is done.

I know that is sorta vague, but I like to be able to change settings easily. This was one of the problems for me with GNOME last time out, and so I'd like to be prepared so I don't give up on GNOME this time without giving it a decent chance.

Best regards,
gingermark.

---

### Post by aysiu on 2006-05-27
Alt-F2 ```
gconf-editor
``` will become your best friend.

---

### Post by gingermark on 2006-05-28
Thanks aysiu.

Well, I'm now in GNOME, and I have to say, it looks great. Unfortunately, I feel like the stereotypical newbie ex-Windows user now, except I'm used to doing things the "KDE way".

Could anyone help with the following:

1. How do I change what icons appear on the desktop? I could only find an option to change the desktop background.

2. How do I get rid of the shortened menus (with the vertical arrows that truncate the menu height). I'd prefer to see the whole menu in one go. I don't think it'll be flying off the screen anytime soon! :)

3. How do I control elements of the panel, and move them around? Again, I've found the panel settings menu, but it only seems to control a few things. I'd like to move the section next to the clock (where active program icons appear) next to the pager.

Those three are all I have for now, but I'm guessing if I understand how to do stuff like that I'll hopefully then be able to figure out how to do other stuff I need as I go along. I understand that simplicity is GNOME's "thing", which is why each configuration menu seems very limited to me. I'm sure I'll get used to it once I learn how configuration outside those menus' scope is done.

Sorry for sounding like such a n00b,
best regards,

gingermark.

EDIT: Oh, and I remember reading there was a GNOME version of YuKuake. Could anyone tell me the name of it please?
EDIT AGAIN: OK, I figured out question 3, it was actually the same as KDE, but I had to click to the left of the area I wanted. Maybe there is hope :)
EDIT ONE MORE TIME: *And I resolved question two by removing the old .gnome2 folder (I think, I was cleaning up the hidden folders in general), and now the truncation (is that a word?) in the menus is gone!* - **scratch that** - they came back! There has to be an easy GUI option to turn them off!

---

### Post by Super King on 2006-05-28
[QUOTE=gingermark]2. How do I get rid of the shortened menus (with the vertical arrows that truncate the menu height). I'd prefer to see the whole menu in one go. I don't think it'll be flying off the screen anytime soon![/QUOTE]

Unfortunately I think that's simply a bug with Gnome in Breezy. It's definitely annoying as the menus are always shortened even when there is plenty of screen space and it is completely unnecessary. There was another thread around here concerning the same issue; I haven't noticed it in my time playing with Dapper.

---

### Post by aysiu on 2006-05-28
[QUOTE=gingermark]1. How do I change what icons appear on the desktop? I could only find an option to change the desktop background.[/QUOTE] It's in *gconf-editor* somewhere... I think it's Apps > Metacity or Apps > Nautilus...

---

