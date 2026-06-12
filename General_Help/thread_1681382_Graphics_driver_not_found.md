---
title: "Graphics driver not found?"
date: 2011-02-04
forum: General Help
---

### Post by JezzaFromAUS on 2011-02-04
Basically when I first got Ubuntu I could go into Additional Drivers and enable the graphics, which would help alot with everything.

However, just recently I think I accedently removed something in the system and now it's not in the list and i have no graphics enabled. Are there a few things I can do to try fix this? Thanks.

(PS: I've updated Ubuntu)

---

### Post by ronnielsen1 on 2011-02-04
Enter [COLOR=Red]jockey-gtk[/COLOR] in a terminal

---

### Post by JezzaFromAUS on 2011-02-04
Thanks but as I stated, it doesn't see it anymore on the list, it's empty, but it used to show it.

EDIT: Oh I see what you mean, I meant that the driver in the list dissapeared, thanks.

---

### Post by JezzaFromAUS on 2011-02-07
bump

EDIT: Starting to think that it was caused due to me installing something on **Synaptic Package Manager** and I had to remove some lib thing or 2 (i remember now i think) and yeah...

---

### Post by Perfect Storm on 2011-02-07
You can check Synaptic's History

File ---> History

---

### Post by JezzaFromAUS on 2011-02-07
I checked the history, I no longer think it's that. :/

---

### Post by Perfect Storm on 2011-02-08
Make sure these are installed or try re-install:

jockey-common
jockey-gtk
nvidia-173-modaliases
nvidia-96-modaliases
nvidia-common
nvidia-current
nvidia-current-modaliases
nvidia-settings

---

### Post by JezzaFromAUS on 2011-02-10
Thanks, but the jockeys didn't work and I don't have an NVidia card, it's for a netbook, some Intel card.

---

### Post by Perfect Storm on 2011-02-11
Intel cards use its open source driver, so you don't have to install anything.

There's no restricted driver for intel video cards.

---

