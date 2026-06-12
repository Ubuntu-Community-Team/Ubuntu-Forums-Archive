---
title: "GNUCASH Commodities problem - template"
date: 2010-05-12
forum: General Help
---

### Post by Unspeakable Horror on 2010-05-12
I accidentally added a Commodity to the "template" namespace and now I can't see it either on the Price Editor or the Securities Editor to change it's namespace to something else like NASDAQ, etc.
Removing it also isn't possible since I can't see it to select it.

How can I fix this? Any ideas? 

From what I understand now it seems that "template" is some internal thing and it shouldn't be displayed anywhere.

---

### Post by Unspeakable Horror on 2010-05-12
I guess nobody knows :s

---

### Post by Unspeakable Horror on 2010-05-13
I'll answer to myself.

You have to edit the GNUCash file manually. It's compressed as .gz, and the file itself its XML, so any text editor will do.
Once there just search for "template" and delete the commodities that are under that namespace.

---

### Post by r m h on 2010-05-13
Hey Unspeakable Horror -

Thanks for the solution.  I'm just getting started with GNUCash, so this may come in very handy for me in the near future.

---

