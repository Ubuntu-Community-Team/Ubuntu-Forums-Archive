---
title: "Lugaru will not Install"
date: 2010-05-09
forum: General Help
---

### Post by Joseph Schwenker on 2010-05-09
I am using Ubuntu 10.04, and just bought the Humble Indie Bundle.  Unfortunately, Lugaru will not install.  I changed its permissions to be executable, but double clicking does nothing.  I ran it from the terminal with sh, and that gives this error:
```
joseph@joseph:~/Desktop/Lugaru$ sh lugaru-full-linux-x86-1.0c.bin 
lugaru-full-linux-x86-1.0c.bin: 1: Syntax error: "(" unexpected

```

I also tried sudo sh, but that returns the same error.  I also tried redownloading the Linux binary, but even the new version doesn't work.  Can anyone help?  It'd be nice not to have to run Lugaru under WINE, though it does run rather nicely.

---

### Post by gcmarimon on 2010-05-09
well i waas searching the same...
.bin files are not doubleclicking ones... nor sh comand line...
for .bin files u must :
1 - open terminal
2 - go to your directory with the .bin file ( in my case /home/mandos/download)
3- #chmod +x file.bin
4-nothing will happen... and a new comand line will be available
5- #./file.bin
done!

---

### Post by Joseph Schwenker on 2010-05-09
Thanks!  This solved my problem.

---

