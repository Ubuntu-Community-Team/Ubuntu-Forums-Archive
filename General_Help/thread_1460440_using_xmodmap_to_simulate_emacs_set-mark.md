---
title: "using xmodmap to simulate emacs set-mark"
date: 2010-04-22
forum: General Help
---

### Post by nispio on 2010-04-22
I have remapped my keyboard using xmodmap so that when I hold down  capslock, the i-j-k-l keys become my arrow keys, h and colon become Home  and End, and n and m become PageUp and PageDown, etc.

Now I want  to achieve something very similar to the emacs set-mark function, in  that if I press Capslock-Space, and then navigate using the navigation  keys mentioned above, I will begin highlighting a region.

In  windows, I achieve this through a program called autohotkey.  When I  press capslock-space, I set a variable called 'markset', and then for  each of the navigation keys, I say (in pseudocode)
```
function keypressed(key)
    if (markset)
        send Shift+key
     else
        send key
```It is crude, but it gets the job  done.  I am hoping that someone might have a suggestion on how to  implement this using xmodmap.  I thought that ISO_NEXT_GROUP looked  promising, but I have no idea how to use it.  Besides that, I didn't  know if it would ever be possible using xmodmap to map a key to a key  combo like key=Shift+Up.

Any suggestions would be greatly  appreciated.

---

