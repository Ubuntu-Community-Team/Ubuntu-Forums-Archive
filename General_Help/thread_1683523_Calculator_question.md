---
title: "Calculator question"
date: 2011-02-07
forum: General Help
---

### Post by Aleksandar_B on 2011-02-07
I'm currently working with trigonometric functions, and I'm having trouble figuring out how to insert degrees, minutes and seconds. 

For example I need to insert 35° 10' and I don't know how to get these symbols on my keyboard, I just cp them from Write after using Insert -> Special Character option. 

Is there an easier way of doing this?

---

### Post by cipherboy_loc on 2011-02-07
In theory, you could use xmodmap to remap the keys. For instance, if every time you wanted the "°" symbol, you could press F12, but other than that, you almost need to do it manually every time. I used to have a broken 'L' key, and I remapped the right shift key to the l character. You would have to use `xev` to show the character code for your F12 key and then something like:

```
xmodmap -e 'keycode 96=°'
```




Cipherboy

---

### Post by Aleksandar_B on 2011-02-08
Well, that sucks, but thanks for the tip ):P

---

