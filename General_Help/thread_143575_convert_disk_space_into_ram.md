---
title: "convert disk space into ram?"
date: 2006-03-12
forum: General Help
---

### Post by harty83 on 2006-03-12
Howdy,

I was wondering.  I have a huge amount of disk space that I will never use but limited memory.  Is there a way in linux to isolate a chunk of disk space to be used as RAM?  I know windows has this option which improves the speed of Windows XP tremendously. 

Thanks,
Alan

---

### Post by qamelian on 2006-03-12
This is the swap partition in linux. If you allowed the installer to automatically partition your drive, it will have already created a swap partition of an appropriate size to act as virtual memory. You also have the option of creating a swap partition and choozing the size yourself if you manually partition your drive during the install.

---

### Post by thnogueira on 2006-03-12
Yes, this is called **swap** space in linux. In despite of wind*, this is usually assigned as a partition, but you can make it as a file. In this case you follow the steps:

1 - let's say you want to make a swap file with 1Gb named /swap. The command is:
```

dd if=/dev/zero of=/swap bs=4k count=256k

```

2 - the next step is to prepare this file to be a swap file:
```

mkswap /swap

```

3 - Now you can activate it:
```

swapon /swap

```

4 - to automacally activate it you must add the following line to /etc/fstab, after the / directory line:
```

/swap    none    swap    sw    0    0

```

Just a note: swap files are MUCH SLOWER than the RAM.

---

### Post by harty83 on 2006-03-12
Ah gotcha.  Okay so if I already have a swap partition, then I can assume that it is being utilized as virtual memory and I can't do anything else to improve speed (except tweak programs, kde, etc or buy more memory) right?

---

### Post by Sutekh on 2006-03-12
You can check the usage of your memory and CPU and swap using
```
top
```Try opening a lot of programs and see what your PC uses up.  You could add extra space for swap but it may be completely uneccessary.

---

### Post by dcstar on 2006-03-13
[QUOTE=harty83]Ah gotcha.  Okay so if I already have a swap partition, then I can assume that it is being utilized as virtual memory and I can't do anything else to improve speed (except tweak programs, kde, etc or buy more memory) right?[/QUOTE]
There are various HOWTOs in the forum for altering things to improve performance over the default, if you do a search you might find some worth experimenting with.

---

