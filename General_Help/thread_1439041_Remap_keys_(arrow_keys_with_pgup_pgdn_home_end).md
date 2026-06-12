---
title: "Remap keys (arrow keys with pgup pgdn home end)"
date: 2010-03-25
forum: General Help
---

### Post by Aphoxema on 2010-03-25
I'm trying to figure out how to exchange my arrow keys with my PgUp, PgDn, Home and End keys. Presently, I have to hold Fn to use these keys, but I find that I use Page Up and Page Down far more often and since my Fn key is on the other side of the keyboard I have to use both hands to use it.

How do I alter my keymap to do this?

---

### Post by Aphoxema on 2010-03-25
Wasn't as hard as I thought it would be, I just had to use Xmodmap with this config...

keycode 112 = Up
keycode 117 = Down
keycode 115 = Right
keycode 110 = Left
keycode 111 = Prior
keycode 116 = Next
keycode 114 = End
keycode 113 = Home

---

