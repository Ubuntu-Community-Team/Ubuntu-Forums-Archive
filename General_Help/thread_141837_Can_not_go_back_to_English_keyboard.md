---
title: "Can not go back to English keyboard"
date: 2006-03-09
forum: General Help
---

### Post by Yumi on 2006-03-09
I had set my keyboard to German but wanted to reverd to English. In preferences - keyboard I first set the default to English, then deleted German but still German keyboard.

I deleted German and German writing Aids in Languages, still German keyboard.

How to get English back?

Michael

---

### Post by dmizer on 2006-03-09
i assume that because you've posted here, that you're using ubuntu and not kde.

in which case, all you have to do is click on system > preferences > keyboard.

you may have to add english keyboard back onto your list.

---

### Post by Yumi on 2006-03-09
I am on Breezy and Ubuntu. As I said, in System-preferences-keyboard only the uk international keyboard is present and checked as defauld. Result - keyboard writes German äöü
Michael

---

### Post by dmizer on 2006-03-09
terribly sorry, i replied to your post this morning before i had my coffee, and read it incorrectly.

i am using a computer with a japanese keyboard, and when i attempted to switch to an english keyboard, it didn't work ... it only typed japanese katakana.  i'll play with it today a bit and see if i can come up with an answer for you.

---

### Post by bluevoodoo1 on 2006-03-09
I believe there is an option with 

sudo dpkg-reconfigure xserver-xorg 

to change your keyboard preference. Might want to check that out?

(make a backup of your xorg.conf file first...) 

sudo cp /etc/X11/xorg.conf /etc/X11.xorg.conf_backup

---

### Post by Yumi on 2006-03-11
Thank you, editing the xorg.conf file did the trick. I am back on English! But opening the file in a texteditor would make the change easier. The command line editing cycles through a whole process of display and graphics setting as well as configuring the mouse. The file is nicely structured and under the entry keyboard the de has to be changed to uk or us, thats all.

Dmizer how was the coffee. I did not know that there is a special japanese keyboard. The Chinese use a standard keyboard and a software input method.

Michael

---

