---
title: "Force Quitted Docky It wont start!"
date: 2010-02-07
forum: General Help
---

### Post by MichealH on 2010-02-07
Hello,
Docky is my favourite dock and It wasnt responding so I force Quitted it and Now It wont start  I have tried removing it and install it again by:

```
sudo apt-get remove docky & sudo apt-get install docky
```

But no luck :(

What should I do 

-Micheal

---

### Post by llawwehttam on 2010-02-07
You could always try purging it.

```
sudo apt-get purge docky ; sudo apt-get autoremove ; sudo apt-get install docky
```

That may help. If not you may have to find the docky config folder in your /home/username and remove it manually.

---

### Post by MichealH on 2010-02-07
Sorry No luck Where would the config folder/file be?

---

### Post by MichealH on 2010-02-07
:/ Bump

---

