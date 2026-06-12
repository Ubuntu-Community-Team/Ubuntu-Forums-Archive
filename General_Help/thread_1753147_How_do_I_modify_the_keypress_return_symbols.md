---
title: "How do I modify the keypress return symbols?"
date: 2011-05-08
forum: General Help
---

### Post by kliq on 2011-05-08
Hello.

When I press the keyboard button: (- _)
I would like to see a '_' on the screen instead of a '-'.
How can this be done, please?
{Lucid 10.4}

---

### Post by enimeizoo on 2011-05-08
I'm not sure what you want to do, but if you want to replace the underscore by a minus, you can do :
```
xmodmap -e "keysym underscore = minus"
```Be aware that after that you won't be able to type an underscore until you assign another keysym or keycode to it (or until you reboot). Make sure to check xmodmap manual. 
If you want it to be applied to only one physical key, you will have to find out the keycode and do something like that :
```
xmodmap -e "keycode keyCodeOfTheKeyToModify = minus"
```Those changes are removed on reboot, if you want to make it permanent, add the line to your .profile or create a .xmodmaprc file in your home folder with the xmodmap command you want.

You can find the keycode of a key with xev.

---

### Post by kliq on 2011-05-11
Thank you very much enimeizoo.
I've finally tried it out.

This is so much better.
I was finding it very tedious to keep on having to key: shift & underscore  everytime that I wanted an underscore. 
When I want a minus, I just use the one over on the far right.

---

