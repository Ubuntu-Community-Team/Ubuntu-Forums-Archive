---
title: "Starting Rhythmbox on top"
date: 2010-09-02
forum: General Help
---

### Post by change_mode on 2010-09-02
Rhythmbox has the stupid default behaviour of starting hidden to tray, so you have to bring it up to select a playlist.

This can be changed by setting "/apps/rhythmbox/plugins/status-icon/window-visible" to true in gconf, but it automatically unsets the value when you close Rhythmbox while it's hidden.

What can I do to make Rhythmbox start on top every time?

---

### Post by change_mode on 2010-09-02
What I tried:

- setting the entry to true as default in gconf
- setting the entry to true as mandatory in gconf
- setting the config file to read only

In all these cases, the setting changes to "false" anyway when I close Rhythmbox.

- changing the owner of the config file to root
- making the file immutable

In these cases, gconf creates a new config file.

- making folder immutable

Setting stays "true", but Rhythmbox starts hidden anyway. What is this, a bad joke?

---

### Post by partsdale on 2010-09-02
I've been wondering about this for a while. Can't wait to see if there's a guru with an answer.

Thanks for asking the question.
Dale

---

### Post by change_mode on 2010-09-04
I somehow got it working, but not exactly sure how. My best guess is that the "set as mandatory" option in gconf-editor only takes effect after a restart.

---

### Post by Saprissa on 2010-09-04
> **change_mode said:**
> What I tried:

- setting the entry to true as default in gconf
- setting the entry to true as mandatory in gconf
- setting the config file to read only

In all these cases, the setting changes to "false" anyway when I close Rhythmbox.

- changing the owner of the config file to root
- making the file immutable

In these cases, gconf creates a new config file.

- making folder immutable

Setting stays "true", but Rhythmbox starts hidden anyway. What is this, a bad joke?

I'm with you 100%.

I know we're all different and we all work differently, but I really struggle to understand for whom this is a GOOD default behavior.

A media player is not the type of application I start and don't want to interact with immediately.

No answers, only sympathy.

---

