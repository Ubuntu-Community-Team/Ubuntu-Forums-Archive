---
title: "Buggy behavior in Kid3 1.2?"
date: 2009-12-13
forum: General Help
---

### Post by dwasifar on 2009-12-13
Kid3 is one of the KDE apps I use under Gnome.  Been using it for years, but version 1.2 that I got from the Karmic repos seems like it's unstable.  

I've noticed periodic problems with redraws, such that if I have multiple tracks selected, and I make a common change to all of them, the specific info for one track appears in fields that should stay blank, or the highlighting goes away (fully or partially) in the track list.

Worse, I have found that sometimes changes are applied to the wrong field.  For example, the other day I selected all tracks in a folder, changed the tag2 "Genre" field from "Other" to "Rock," and saved.  It left Genre set to "Other" for all tracks except one, but changed the *title* of those tracks to "Rock."  I tried the same thing in another folder, and it changed half the *track numbers* (apparently randomly) to "Rock."  

Obviously this makes the app pretty much useless.  I reverted to version 1.1 from the package archives and locked the version in Synaptic to prevent it being updated.  (I like 1.1 better anyway because the fields are scaled better and tab navigation works.)  But these are weird problems for a mature application.  Anyone else?

---

