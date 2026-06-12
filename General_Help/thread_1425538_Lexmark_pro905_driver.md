---
title: "Lexmark pro905 driver"
date: 2010-03-09
forum: General Help
---

### Post by wilminet on 2010-03-09
I am new to Ubuntu. I have downloaded and tried to install the printer driver for lexmark pro905 but after extraction when I run it it wants a root or administrator password. i have only used one password on whatever wanted a password and tell me its the incorrect password when I use that password, I have also tried blank, no go! How do i rectify this?

---

### Post by gitfiddler on 2010-03-12
wilminet,

Please see my post here: [http://ubuntuforums.org/showthread.php?t=1419642&highlight=lexmark+root]("http://ubuntuforums.org/showthread.php?t=1419642&highlight=lexmark+root")

gitfiddler

---

### Post by EnsignR on 2011-10-17
I've just setup 11.10 and couldn't follow gitfiddler's guide to setting the root password.

I think what I did instead is simpler anyway and should work for everyone. It seems to be for me as the script [here]("http://support.lexmark.com/index?page=product&locale=EN&productCode=LEXMARK_PLATINUM_PRO905&segment=SUPPORT&userlocale=EN#1") ran for me.

Open terminal and enter
```
sudo passwd
```

Then enter your own password followed by the new password for root (twice) which you can then enter in the dialog when the script asks for it.

HTH someone.

---

