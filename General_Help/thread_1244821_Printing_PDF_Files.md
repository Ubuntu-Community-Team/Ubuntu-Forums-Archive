---
title: "Printing PDF Files"
date: 2009-08-19
forum: General Help
---

### Post by accooper on 2009-08-19
I am having trouble printing pdf files.  I have tried Adobe and several others with the same problem a 100 page file takes an hour or more before it starts printing to my laser printer.  Any ideas why and how to fix it?

TIA

Andrew From Texas

---

### Post by wojox on 2009-08-19
Try:

```
sudo apt-get install cups-pdf
```

```
sudo chmod +s /usr/lib/cups/backend/cups-pdf
```

Then when you print select PDF printer.

---

### Post by XCan on 2009-08-20
Sounds like your printer waits for everything to come through before printing, instead of spooling. Have you tried enabling the "optimize for speed" and "save printer memory" options in Adobe Reader?

---

