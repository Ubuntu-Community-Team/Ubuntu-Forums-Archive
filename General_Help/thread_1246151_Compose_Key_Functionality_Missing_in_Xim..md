---
title: "Compose Key Functionality Missing in Xim."
date: 2009-08-21
forum: General Help
---

### Post by hlewagastir on 2009-08-21
I am currently trying to use Ubuntu 9.04 on an acer laptop I own. However, I was having problems accessing some of the characters I use on a daily basis, including superscript h and w, and various multilingual characters.
I looked up the supposed combinations for these characters in the compose lists, but was unable to make them work, perhaps because of the keyboard limitations of the laptop.
I then followed the instructions at
[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)
to attempt to create a custom sequence.
However, since adding the line:

export GTK_IM_MODULE="xim"

as stated on those pages, I no longer have any compose key functionality at all.
Is anyone able to explain this, or preferably, offer a solution?

Thanks

---

### Post by aldimond on 2009-08-21
It sounds like before you changed GTK_IM_MODULE to xim it was probably using Gnome's hard-coded compose settings.  My guess is that there's something wrong with your ~/.XCompose.  I could take a look at it if you want.  I can't find a way to do a syntax check on that file, though, so I may be stumbling in the dark.

---

