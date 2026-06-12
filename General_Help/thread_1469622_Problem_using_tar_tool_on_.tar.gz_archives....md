---
title: "Problem using tar tool on .tar.gz archives..."
date: 2010-05-02
forum: General Help
---

### Post by j7%&lt;RmUg on 2010-05-02
Hey all, this is actually the first support thread iv posted in over 10 months.

I seem to be having a problem using the tar tool to untar any .tar.gz files i come across. If i go:

```

tar -zxvf example.tar.gz

```

It spits out this error at me:

```
tar: -zxvf: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: example.tar.gz: Not found in archive
tar: Exiting with failure status due to previous errors
```

I am running the Lucid with the latest updates and iv already done a round on irc asking people about this problem. Thanks in advance!

---

### Post by dino99 on 2010-05-02
double-click on the file ?

your file is not found: locate "your file"

---

### Post by j7%&lt;RmUg on 2010-05-02
If i double click on the file in nautilus it opens and i can extract whatever i want. The point is that it doesnt work in the terminal for some strange reason, even though i know perfectly well that the file exists.

---

### Post by j7%&lt;RmUg on 2010-05-02
Ok, its still not working right but if i just use tar with only the archive file as an argument then it works fine, i still have no idea why its throwing that error though.

---

