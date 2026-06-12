---
title: "Problem with European keyboard layout"
date: 2012-05-13
forum: General Help
---

### Post by anopows on 2012-05-13
Before Ubuntu I used Windows. Windows managed the Alt and Ctr key otherwise. If I clicked "Alt Gr" (the right Alt) then I could use 3rd level keys. That works fine with Ubuntu too. 

But with Windows I also could use *Ctr left* + *Alt left* to get *Alt Gr* (so I could use 3rd level keys), Ubuntu doesn't allow this. 

Is there any possible solution for my problem?
Already thank you for every response 

(Keyboard layout at the moment: 
[IMG]http://i.imgur.com/H3YMZ.png[/IMG])

---

### Post by dino99 on 2012-05-13
You can find comprehensive list of keyboard shortcuts of various Ubuntu 12.04 default applications here:

[https://docs.google.com/document/d/1MYNyM2E7E40jsQ0Sxw0MOjLPox4CGpSQEgc5WK4DM8M/edit](https://docs.google.com/document/d/1MYNyM2E7E40jsQ0Sxw0MOjLPox4CGpSQEgc5WK4DM8M/edit)

---

### Post by Carborundum on 2012-05-13
You can change which key controls the 3rd level from Settings>Keyboard>Layout settings>Options. Unfortunately, there does not appear to be an option to have [Left ctrl]+[Left alt] choose the 3rd level.

---

### Post by forestG on 2012-05-13
Hi!

Ubuntu 12.04 has a serious bug in keyboard layout selection. I was using the norwegian and the greek layouts but after upgrading to 12.04 from 11.10 the only layout working was the english one which I had removed in 11.10. If you want a quick fix until the bug is fixed you can type this command 

sudo setxkbmap -option grp:alt_shift_toggle no,gr

Unofortunately you have to run this command each time you login to your computer. You can put any other lanugage ofcourse instead of norwegian(no) and greek (gr). With this command the change of the language follows the windows style (alt-shift).

More information can be found here: [https://bugs.launchpad.net/bugs/995401](https://bugs.launchpad.net/bugs/995401)

---

