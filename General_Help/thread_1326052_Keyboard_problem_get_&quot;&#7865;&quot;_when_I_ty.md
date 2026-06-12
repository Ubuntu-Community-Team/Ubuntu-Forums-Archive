---
title: "Keyboard problem: get &quot;&#7865;&quot; when I type &quot;e&quot; and then &quot;.&quot; Why?"
date: 2009-11-14
forum: General Help
---

### Post by skinkone on 2009-11-14
Upon upgrading to Karmic Koala, I can't get to [www.googl&#7865;com](www.googl&#7865;com) because I get the &#7865; instead of e. Ím (see, it did it also for I'm). To correct this, I have to type a space after the letter, enter the period, and then delete the space . What is going on here ? I have a Hama RF Optical Desktop 3000 keyboard with Italian layout.

---

### Post by skinkone on 2009-11-14
Through Google searching, I found that these additional dots are called "diacritics". I have no idea why they were turned on; something must have happened during the upgrade to Koala.

This solution worked:
System...Preferences...SCIM Input Method Setup

On the left, there is a section called "IMEngine". There I clicked on "Global Setup" and found all of the languages checked. I hit the button "Disable All" to uncheck everything, then "Apply".

Now you have to stop and restart SCIM. Do this in a terminal window:

$ sudo pkill -9 scim
$ scim -d

---

