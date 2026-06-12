---
title: "How to make Ubuntu to write Hebrew?"
date: 2010-07-01
forum: General Help
---

### Post by avz3 on 2010-07-01
Hi
I've installed Ubuntu 10.04 and is seems great! now I would like to know what do I have to do in order to enable it to write Hebrew? is there any guide that explains how to install other languages as well?
Thanx.

---

### Post by drpjkurian on 2010-07-01
Hi
Please try my [thread]("http://ubuntuforums.org/showthread.php?t=1386985"). Well in my thread the language is a south indian language known as "Malayalam". But the procedure is same. Hope Ubuntu supports Hebrew. If it supports then please follow the instructions mentioned in my thread

---

### Post by artemyv on 2010-07-02
> **drpjkurian said:**
> Hope Ubuntu supports Hebrew. 

Yes it does. So just add language support using Language Selector and add Layout in the Keyboard preferences

---

### Post by avz3 on 2010-07-03
[SIZE=2]Hi people. It's great! I acted according to your instructions and it works like a charm, no multilingual and no b.s.. really great! there are two other questions that I would like to ask.
first, how can I change the fonts (in the firefox, not the fonts that I'm writing)? and the second one - is there a way to navigate between the languages with the keyboard (like alt+shft in windows) or only with the mouse?
Thanx.
[/SIZE]

---

### Post by artemyv on 2010-07-03
> **avz3 said:**
> [SIZE=2]how can I change the fonts (in the firefox, not the fonts that I'm writing)?
[/SIZE]
EDIT -> Preferences -> Content -> Font and Color

You may need to install additional fonts before you can use them 
[SIZE=2]
[/SIZE]> **avz3 said:**
> [SIZE=2]is there a way to navigate between the languages with the keyboard (like alt+shft in windows) or only with the mouse?
[/SIZE]

Right click on language indicator -> Keyboard Preferencies -> Layouts -> Options -> Keys tochange layout

---

### Post by drpjkurian on 2010-07-03
> **avz3 said:**
> [SIZE=2]Hi people. It's great! I acted according to your instructions and it works like a charm, 
[/SIZE]

Hi
Happy to know that it worked for you. Enjoy Linux

---

### Post by simosx on 2010-07-05
Ubuntu 10.04 replaced SCIM with IBus. They both do the same thing, but the proper way to do it is with IBus. 
It would be good to make an attempt to use IBus instead of SCIM.

In general, the way you get support for Hebrew, Malayalam or any other language is to go to System»Administration»Language Support and add the new language.
This should install necessary fonts and activate automatically IBus if required (if no IBus is required, you need to manually go to the Keyboard Preferences»Layouts and add your layout).

If the above does not work for you, then you should consider contributing to Ubuntu so that the language pack of your language enables proper support in the easiest way.

---

