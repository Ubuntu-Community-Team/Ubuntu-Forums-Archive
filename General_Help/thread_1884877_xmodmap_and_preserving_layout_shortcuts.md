---
title: "xmodmap and preserving layout shortcuts"
date: 2011-11-22
forum: General Help
---

### Post by sidowaty on 2011-11-22
Hi all,

I found how to remap keys and use L_Alt+ijkl as arrows. I'm using following file for xmodmap:

```
keycode 64 = Mode_switch
keysym j = j J Left 
keysym l = l L Right
keysym i = i I Up
keysym k = k K Down
```
(66 = L_Alt)

Everything works fine, but... I'm using polish programmers keyboard layout and normally R_Alt + l stands for '&#322;' letter. When I'm applying xmodmap with above file shortcut R_Alt+l doesn't work. 

So I have question - how to preserve R_Alt+l behaviour while using xmodmap file for L_Alt+ijkl as arrows?

---

### Post by sidowaty on 2011-11-24
Spent some time on xmodmap manual & few web pages and... I've got this working ;)

If someone is looking for above - try this xmodmap file:

```
keycode 64 = Mode_switch
keysym j = j J Left 
keysym i = i I Up
keysym k = k K Down
keysym l = l L Right Right lstroke Lstroke

```

Just 3rd and 4th symbol stands for right Alt I think, and next two for right. 

Now everything works fine.

---

