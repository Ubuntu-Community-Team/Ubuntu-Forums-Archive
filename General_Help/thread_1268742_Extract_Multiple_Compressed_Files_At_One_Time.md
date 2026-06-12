---
title: "Extract Multiple Compressed Files At One Time"
date: 2009-09-17
forum: General Help
---

### Post by WalkerInTheWoods on 2009-09-17
My mother-in-law is jumping into Ubuntu full force. I did a complete wipe of windows for her (her request!) after backing up all her personal files with nero (only option I saw available). I install Ubuntu 9.04. Its all good. I go to move her personal files onto her computer. It appears nero made each file its own individual compressed file.

So how can I extract all these files in one go without having to do each one individually? There are a lot of files and it would take forever to do each file.

Thanks

---

### Post by Zeosa on 2009-09-17
Try this (assuming your talking about tar archives)

```

for i in *.tar; do tar -xvf $i; done

```

---

### Post by WalkerInTheWoods on 2009-09-17
Unfortunately they are not .tar files. I was in windows when I backed up the files. I had to use Nero, which created files something like *.nco. I can open these files just fine clicking on them. This opens them with the archive manager where I can extract them just fine, individually.

---

### Post by Zeosa on 2009-09-17
They are probably glorified zip files (just a guess) see if you can open one of the from the command line with unzip.

---

### Post by WalkerInTheWoods on 2009-09-17
I am not sitting at her computer at the moment, but will be later today. Assuming that I can open them with unzip, how would I go about extracting all of them with unzip?

---

### Post by Zeosa on 2009-09-17
same idea...

```

for i in *.zip; do unzip $i; done

```

or *.nco, etc...

---

### Post by Bonster on 2009-09-17
for zip files i highlight all of it and right click and hit extract here

---

### Post by WalkerInTheWoods on 2009-09-17
This works great. Thank you so much!

> **Zeosa said:**
> same idea...

```

for i in *.zip; do unzip $i; done

```

or *.nco, etc...

---

