---
title: "Lucid -- Profile changes don't persist in Gnome Terminal"
date: 2011-07-10
forum: General Help
---

### Post by bartonski on 2011-07-10
I recently upgraded to Lucid, and the default profile in Gnome Terminal has the background transparency set very high. I try changing the background transparency in the default profile. or using a different profile... I can make the changes, but they aren't saved after I close the terminal.

The version of Gnome Terminal is 2.30.2

---

### Post by matt_symes on 2011-07-10
Hi

That's odd. I don't get that behaviour on my Lucid install.

Try setting the transparency using gconf-tool under /app/gnome-terminal/profiles.

Kind regards

---

### Post by bartonski on 2011-07-11
I changed the background to 'solid' in gconf-editor, I was then able to open a terminal and change the background back to 'transparent' with a very high opacity. I closed the terminal and re-opened it... at that point, it opened with the changes that I had made. I'm guessing that when I upgraded to Lucid, the link was broken to the profile somehow, and changing things in gconf-editor somehow re-established that link.

---

### Post by bartonski on 2011-07-11
PS. The changes that I made were to the default profile.

---

### Post by matt_symes on 2011-07-11
Hi

> **bartonski said:**
> I changed the background to 'solid' in gconf-editor, I was then able to open a terminal and change the background back to 'transparent' with a very high opacity. I closed the terminal and re-opened it... at that point, it opened with the changes that I had made. I'm guessing that when I upgraded to Lucid, the link was broken to the profile somehow, and changing things in gconf-editor somehow re-established that link.

Just another odd Ubuntu quirk :-k I'm glad it's fixed.

Kind regards

---

