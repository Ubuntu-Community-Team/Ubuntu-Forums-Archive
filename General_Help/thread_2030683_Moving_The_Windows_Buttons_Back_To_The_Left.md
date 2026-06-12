---
title: "Moving The Windows Buttons Back To The Left"
date: 2012-07-20
forum: General Help
---

### Post by misterplayb on 2012-07-20
Hi moved the windows buttons to the right using this in the termina: gconftool -s /apps/metacity/general/button_layout -t string menu:minimize,maximize,close

how do i get them back to the left side? Thanks

---

### Post by 3Miro on 2012-07-20
It is one of those 2:
```
gconftool -s /apps/metacity/general/button_layout -t string close,minimize,maximize:
```
or
```
gconftool -s /apps/metacity/general/button_layout -t string close,minimize,maximize:menu
```

This depends on whether or not you want to have a menu button on the right, the default installation doesn't have one, but you can add it with the second command.

Those should be safe, if they don't work, you should get an error and nothing would happen.

---

### Post by BoogeyOfTheMan on 2012-07-21
Its the third one to basically reverse the order. The colon ( : ) seems to signify which side things are on. IE; anything left of the colon shows on the left, everything else is aligned to the right.

---

