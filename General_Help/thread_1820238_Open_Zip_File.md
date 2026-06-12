---
title: "Open Zip File"
date: 2011-08-07
forum: General Help
---

### Post by borgward on 2011-08-07
Hi

I need to download a service manual for a friends Dell Laptop from Dell. It is a .zip file. What do I use to open it. I am running Ubuntu 10.04, or what can I download to read it?

Tom

---

### Post by AlphaLexman on 2011-08-07
Go to 'Applications -> Accessories -> Archive Manager -> File -> Open' and select your zip file and click the extract button.

Good Luck!

---

### Post by borgward on 2011-08-07
No "Archive Manager" at Applications -> Accessories. Could it have another name? * am running 10.04*

---

### Post by Spyderkid on 2011-08-07
right click on the file instead and choose open with... archive manager


or.... right click and choose extract here

---

### Post by Spyderkid on 2011-08-07
btw, i preffer 10.10 to 10.04 have you tryed it?

---

### Post by Dave_L on 2011-08-07
You can also launch it from the shell with the command:
```
file-roller
```

---

### Post by AlphaLexman on 2011-08-07
You can also [s]launch[/s] extract it from the shell with the command:
```
unzip /path/to/file.zip
```

---

### Post by Dave_L on 2011-08-07
For clarification, that unzip command doesn't open Archive Manager / File Roller. It will (try to) extract the entire contents of the .zip file into the current directory, which could be a problem if you're not expecting that.

---

