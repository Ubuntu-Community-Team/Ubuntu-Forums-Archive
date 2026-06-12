---
title: "Ubuntu 11.04 - Gnome Shell - Gnome-Tweak-Tool. Weirdness."
date: 2011-06-28
forum: General Help
---

### Post by Roasted on 2011-06-28
I'm running Gnome Shell on Ubuntu 11.04 via the Gnome 3 Team PPA. There's a theme I found on gnome-look.org, and I edited some of the hex colors in the gtkrc file.

If I put the theme in /usr/share/themes, I can select the theme, but it shows up as default colors that the theme came packaged with.

If I put the themes in .themes and select them, they work perfectly.

So my question is, why in the world isn't it behaving when I put them in /usr/share/themes? Likewise, what is the PROPER way to install themes in Ubuntu 11.04? Reason I ask is... I really don't know anymore. It sounds like /usr/share/themes is what's to be used, but by default the standard user doesn't have permission to that folder. Sure, you can chmod it real quick, or just carefully run Nautilus as root, but still... sounds counter-productive if Ubuntu is meant to be relatively easy to use.

Any insight?

---

### Post by wolfen69 on 2011-06-28
As far as I know, putting it in .themes is the way to go. That's how I do it anyway.

---

### Post by Roasted on 2011-06-28
> **wolfen69 said:**
> As far as I know, putting it in .themes is the way to go. That's how I do it anyway.

That's what I do, but .themes and .icons doesn't exist by default in 11.04. I just re-created them and it worked. But what caught my eye was the fact WebUpd8 had a spread about Ubuntu 11.04 with Gnome Tweak Tool, etc., and they specified that you need to put themes in /usr/share/themes, and that Gnome Tweak Tool doesn't read .themes. Uh. Yes it does. Otherwise I wouldn't be looking at my theme right now.

But anyway, I wasn't sure why my theme wasn't being read properly in /usr/share/themes as it was in .themes...

---

### Post by collisionystm on 2011-06-28
> **Roasted said:**
> That's what I do, but .themes and .icons doesn't exist by default in 11.04. I just re-created them and it worked. But what caught my eye was the fact WebUpd8 had a spread about Ubuntu 11.04 with Gnome Tweak Tool, etc., and they specified that you need to put themes in /usr/share/themes, and that Gnome Tweak Tool doesn't read .themes. Uh. Yes it does. Otherwise I wouldn't be looking at my theme right now.

But anyway, I wasn't sure why my theme wasn't being read properly in /usr/share/themes as it was in .themes...

Permissions.

You created the .themes folder, therefore it has permissions for you to access it completely.

---

### Post by Roasted on 2011-06-28
> **collisionystm said:**
> Permissions.

You created the .themes folder, therefore it has permissions for you to access it completely.

If this was the case, and if /usr/share/themes is where we should be saving themes for into the future, wouldn't it make sense for it to be user accessible without me having to root nautilus the theme packages over?

I did recursively grant 755 perms to the folders, but perhaps actual ownership is key... *shrug*

EDIT - FYI, nope. jason:jason with recursive 777 permissions yielded the same thing.

Seriously. Why was the theme location changed? .themes is easy. /usr/share/themes requires elevated access to get to.

---

