---
title: "burg help - won'r remember theme"
date: 2010-03-27
forum: General Help
---

### Post by Shrimply on 2010-03-27
Hi people, please be gentle because as of yet I really not good at this stuff.

Never being happy and having far too much time on my hands, yesterday I installed Burg, I then spent a decent amount of time editing a theme to look like I wanted as shown below.

[IMG]http://i19.photobucket.com/albums/b160/shrimply/burgcapture-1.jpg[/IMG]

Its slightly glitcy but I pretty pleased

However burg is refufing to save my choice of theme

The configuration file looks like this, I've tried changing the theme to = the specific theme i want but that doesn't work, neither does changing the folding options to = yes.  Any help please, at the minute it seems like my time yesterday was a bigger waste of time than even I thought.

# Use the previous selected theme, you can also specify a theme to be used
# In the boot menu, use hotkey 't' to popup a theme selection menu
GRUB_THEME=saved

# Use the previous folding option, its value can be 'yes', 'no' or 'saved'
# In the boot menu, use hotkey 'F7' to show the full list, 'f' to toggle
# between folding modes.
GRUB_FOLD=saved with it.

---

### Post by Shrimply on 2010-03-27
OK well by trial and error, I managed to get it booting using the theme I want.

Instead of 
GRUB_THEME= the full location of the relevant theme.txt as suggested in the guides I could fine, just the name of the theme seems to work.

And changing the folding option to yes also seems to have worked.

Be nice though if anyone had any idea why the "saved" options aren't working.

---

### Post by wojox on 2010-03-27
Couldn't answer your question Shrimply, but it's a Great grub theme. :D

---

### Post by Shrimply on 2010-03-27
Thank you, as I say its slightly glitchy but I'm happy with it.

Anyone got any thoughts?

---

### Post by Shrimply on 2010-03-28
Oh well presume no one is able to give me any advice, nevermind.

---

