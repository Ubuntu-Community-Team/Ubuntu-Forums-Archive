---
title: "Removing Window Borders"
date: 2010-06-30
forum: General Help
---

### Post by kolo-01 on 2010-06-30
this should be quite quick and easy.. when i first started with ubuntu i added a blue border that appears on all my windows and my panel and have been trying to remove it for ages but have no idea how i added it, i assumed it was in the appearance tab, but changing window borders in theme->customise has no effect, help for how to get rid of it would be appreciated

[IMG]http://i167.photobucket.com/albums/u152/kolo-01/blue.png[/IMG]

---

### Post by Woody1987 on 2010-06-30
looks like it may be the compiz shadow effect. Install compiz manager, and disable it.

---

### Post by steveneddy on 2010-06-30
> **Woody1987 said:**
> looks like it may be the compiz shadow effect. Install compiz manager, and disable it.

If you haven't installed **compizconfig-settings-manager** - simply do this in terminal:

```
sudo apt-get install compizconfig-settings-manager
```

Or plow through Synaptic or the Ubuntu Software Center and find it that way and install it.

To get rid of the shadow on the panel:

> ## removing gnome panel drop shadow
You can set the Shadow Windows (Windows Decoration)option in CCSM Window Decorations from "any" to "any & !(type=dock)" to remove the shadow from the panel

The Windows Decoration option is under Effects now.

Good Luck

---

### Post by kolo-01 on 2010-06-30
> **steveneddy said:**
> If you haven't installed **compizconfig-settings-manager** - simply do this in terminal:

```
sudo apt-get install compizconfig-settings-manager
```

Or plow through Synaptic or the Ubuntu Software Center and find it that way and install it.

To get rid of the shadow on the panel:



The Windows Decoration option is under Effects now.

Good Luck


hey, thanks for that, it definitely is the compiz window decoration effect as i changed the colour of it, the easiest way would obviously have been to disable window decoration, but i guess you already knew that you can't just do that. the code you gave works for removing the shadow from the panel, but does not have an effect on the window shadows, not sure why. if you have a follow up on why you think this value change has this effect i  would appreciate it, as i am not very clued on them

---

### Post by steveneddy on 2010-06-30
> **kolo-01 said:**
> hey, thanks for that, it definitely is the compiz window decoration effect as i changed the colour of it, the easiest way would obviously have been to disable window decoration, but i guess you already knew that you can't just do that. the code you gave works for removing the shadow from the panel, but does not have an effect on the window shadows, not sure why. if you have a follow up on why you think this value change has this effect i  would appreciate it, as i am not very clued on them

Are you running Emerald? The glow around the windows looks like an Emerald effect.

Some themes in Emerald have a setting for Window Glow I believe.

Or is that part if the shadow? The shadow color is also manipulated in the Window Decoration settings. You could try turning the shadow radius down a little to see if that helps.

Let us know what you tried and what did or didn't help.

I still think this is an Emerald setting.

---

### Post by kolo-01 on 2010-06-30
> **steveneddy said:**
> Are you running Emerald? The glow around the windows looks like an Emerald effect.

Some themes in Emerald have a setting for Window Glow I believe.

Or is that part if the shadow? The shadow color is also manipulated in the Window Decoration settings. You could try turning the shadow radius down a little to see if that helps.

Let us know what you tried and what did or didn't help.

I still think this is an Emerald setting.


i did download and emerald for a while, but it wasn't installed when i looked on synaptic. i messed about with it for a while but decided not to use it so i removed it, if it was emerald then the shadows would with it also? im a bit confused why it was so easy to turn on but i can't turn it off

and also i can reduce the radius to next to zero, which is pretty much the same as off, but would still like to crack it and turn it off completely

---

### Post by steveneddy on 2010-06-30
> **kolo-01 said:**
> i did download and emerald for a while, but it wasn't installed when i looked on synaptic. i messed about with it for a while but decided not to use it so i removed it, if it was emerald then the shadows would with it also? im a bit confused why it was so easy to turn on but i can't turn it off

and also i can reduce the radius to next to zero, which is pretty much the same as off, but would still like to crack it and turn it off completely

The only thing I can think of is to turn off Window Decorations in CCSM.

Maybe someone else has a better answer.

---

### Post by kolo-01 on 2010-07-01
ok, the way ive come up with is just to turn the opaqueness up to full so you can't see it, not sure if this is how it is on the default setting, but it works..

---

### Post by mcduck on 2010-07-01
> **kolo-01 said:**
> i did download and emerald for a while, but it wasn't installed when i looked on synaptic. i messed about with it for a while but decided not to use it so i removed it, if it was emerald then the shadows would with it also? im a bit confused why it was so easy to turn on but i can't turn it off

and also i can reduce the radius to next to zero, which is pretty much the same as off, but would still like to crack it and turn it off completely

The glow effect in your screenshot is just window shadows, with the color set to blue and the offset tweaked a bit to get the glow effect all around the window.

Just set the color back to black and add some offset to get change the blue glow back to normal window shadows (the default setting would be small black shadows with a little bit of offset to make the shadow appear under the window instead of all sides).

Or if you want to disable the shadows completely just set the opacity to zero. (Setting the "Shadow windows"-field to "none" *should* diable the shadows completely without having to just make them invisible, but the current version of Compiz seems to draw shadows to any normal windows regardless of this setting)

Disabling window decorations completely isn't that great idea, no window decorations also means that you aren't able to move the windows any more, apart from using keyboard shortcuts to do it. And no, if you aren't currently running Emerald then Emerald has nothing to do with this. :)

---

### Post by kolo-01 on 2010-07-05
ah ok, i didn't know that the default setting was a small black border, i assumed that i added it from nothing somehow, thanks

---

