---
title: "Custom keymap for wireless keyboard doesn't work"
date: 2012-01-13
forum: General Help
---

### Post by josvanr on 2012-01-13
hi

I bought a wireless key board which works fine (rapoo), only the function keys F1-12 are only accessible after pressing an extra orange key. The default behaviour of the keys is multimedia keys. 

Now in my regular setup (no wireless keyboard) I have several programs and shortcuts mapped on the function keys in kde settings (zoom etc). So when using the wireless I want to map the multimedia keys to the F1-12 so i can use the latter without pressing an extra key.

So I run xev and see what key codes are pressed for the multimedia keys on my wireless keyboard. Eg the key I want to point to F1, shows keycode 179. So I edit .Xmodmap and enter

keycode 179 = F1

and then I run 

xmodmap .Xmodmap

It seems to work: when I now press the key on my wireless keyboard, keycode 67 appears, same one as with F1. BUTTTTT, I mapped F1 to a custom command in kde : so on my normal keyboard, pressing F1 starts an editor. But pressing F1 on my wireless keyboard does *nothing*.?!?!

It no worke. 

suggestions?........


josvanr

---

### Post by Rebelli0us on 2012-01-13
How do you make custom keymaps? I'm trying to get the [keyboard Power Button to work]("http://ubuntuforums.org/showthread.php?t=1905686").

---

### Post by josvanr on 2012-01-13
well i'm not an expert.. maybe run 'xev' and the press the button and see what key code it sends... then use xmodmap to do the mapping...

---

