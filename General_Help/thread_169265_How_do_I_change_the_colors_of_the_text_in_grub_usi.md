---
title: "How do I change the colors of the text in grub using menu.lst or Konsole?"
date: 2006-05-02
forum: General Help
---

### Post by tsb on 2006-05-02
I can change the splash screen from Konsole, but I can't change the text from white to something else.

Thanks.

---

### Post by aysiu on 2006-05-02
My guess is that you'd uncomment this line: ```
# Pretty colours
**#color cyan/blue white/blue**
``` and choose your own "pretty colors." "Uncomment" means "remove the # sign from in front of it."

---

### Post by tsb on 2006-05-02
I tried that but nothing changed, perhaps because the white in that line is for the text.  I will change "white" to another color and try.  Thanks.

---

### Post by tsb on 2006-05-02
Doesn't work.

Any other ideas?

---

### Post by aysiu on 2006-05-02
Maybe this'll help? I'm not sure.

[http://www.gnu.org/software/grub/manual/html_node/color.html](http://www.gnu.org/software/grub/manual/html_node/color.html)

By the way, this is what Mepis' Grub's relevant entry looks like: ```
color cyan/blue white/blue
foreground ffffff
background 0639a1
```

---

