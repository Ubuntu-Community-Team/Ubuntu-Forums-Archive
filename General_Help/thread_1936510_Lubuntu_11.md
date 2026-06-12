---
title: "Lubuntu 11"
date: 2012-03-06
forum: General Help
---

### Post by shlomi_bt on 2012-03-06
HI,
  Can someone help me how to add a second language and keyboard to
  Lubuntu?
  I added hebrew from the language but i can´t find the proper place to add the keyboard...
Thanks
  shlomi.

---

### Post by raja.genupula on 2012-03-06
[http://askubuntu.com/questions/102344/switching-keyboard-layouts-in-lubuntu-11-10](http://askubuntu.com/questions/102344/switching-keyboard-layouts-in-lubuntu-11-10)

---

### Post by shlomi_bt on 2012-03-06
HI,
  Thanks!
  I already installed hebrew from the lanuage support.
  The issue is that i dont have the hebrew query entry in the layout keyboard switch...
Shlomi

---

### Post by mikewhatever on 2012-03-06
Add the following to your .bashrc (gedit .bashrc to open):

```
setxkbmap -option grp:alt_shift_toggle "us,il
```

...then logout/login.

I've assumed that the other language is English US.

---

### Post by shlomi_bt on 2012-03-06
Thank you very much! i works.
how can i learn more about all those settings which seems i need the command to perform?

---

### Post by mikewhatever on 2012-03-06
There is a lot of info on Lubuntu here [http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

---

