---
title: "Spell Checker stopped after installing OOo 3.2"
date: 2010-08-13
forum: General Help
---

### Post by BobSongs on 2010-08-13
System: Karmic Koala, 32-bit

1. I downloaded OpenOffice.org 3.2 and unpacked it.

2. I decided to remove OpenOffice.org 3.1 from my system using this command:

 ```
sudo apt-get remove openoffice*.*
```3. I installed OpenOffice.org 3.2.x using:

```
sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/*.deb
```followed by:

```
sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb
```And OOo 3.2 works beautifully.

**However,** I've noticed that spell-checking has stopped completely. Pretty much every application, Firefox, GEdit, etc. would underline my errors with a right-click option to correct.

What did I do wrong?

---

### Post by AlphaLexman on 2010-08-13
I would guess/bet that you have some dependency issues with your spell-checker.

Do you still have 'aspell' or 'ispell' installed?

---

### Post by BobSongs on 2010-08-13
I re-installed **aspell** afterward.

However, I don't have aspell in 

System > Preferences > startup applications

I don't know the parameters. If someone could provide them, I'd be much obliged.

---

### Post by BobSongs on 2010-08-14
*bump*

---

### Post by AlphaLexman on 2010-08-14
Note I have OOo 3.1.

When you go to Tools -> Options -> Language Settings -> Writing Aids -> Available Language Modules, is there a spell-checker, check-marked, I would check that! :biggrin:

---

