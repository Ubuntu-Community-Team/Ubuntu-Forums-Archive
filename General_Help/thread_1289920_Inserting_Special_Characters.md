---
title: "Inserting Special Characters"
date: 2009-10-12
forum: General Help
---

### Post by socool274 on 2009-10-12
How would I go about inserting special characters? Mac does it by holding a key, and pressing another key, then pressing another key. Windows works by holding alt + a number. How would I do this on Ubuntu Jaunty (latest version)?

---

### Post by eric3_14159 on 2009-11-09
There are a few ways.

My favorite is the Compose key. Activate it by choosing, on Gnome, System -> Preferences -> Keyboard, and in the Layouts tab clicking "Layout Options". From there you expand the "Compose Key Position" option, and choose whichever of the keys it offers that you would like to use. Then, when typing in a program which understands special characters, you can hold the Compose key (also sometimes called the Multi key), and type a combination which signifies the character you want. For example, holding Compose and then pressing (but not holding) e and then ' gets you é.

The main problem with this method is that you have to learn all the key combinations. There are standards, of course, such as that a letter plus ' gets you the letter with an acute accent, ` is grave, and so on, but it still can be a lot to learn. The main list is here: [https://help.ubuntu.com/community/GtkComposeTable](https://help.ubuntu.com/community/GtkComposeTable)

Another method is to add the Character Palette to your Gnome panel, which allows you to make a set of common special characters as buttons you can click to insert them in whatever you are typing.

A third way is to enter the Unicode directly, though it must be the hex value and not the decimal, by holding Control and Shift at the same time, typing the letter u, and then typing the Unicode hex value you want. So Control+Shift u41 causes A to appear, while Control+Shift u123 causes &#291;.

---

### Post by coffeecat on 2009-11-09
..... a fourth way would be to install the app kcharselect.

The main disadvantage for gnome users is that it is a KDE app and will bring in a load of KDE libraries (unless you've already installed KDE stuff).

Æ¼¢¥þ&#42792;èéêë  :wink:

---

### Post by NoonienSoong97 on 2009-11-21
The only problem I have with the special characters is that there isn't a complete list of latin letters. I would like to know where I can type the latin alphabet in gimp?

---

