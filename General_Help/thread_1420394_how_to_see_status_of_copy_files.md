---
title: "how to see status of copy files?"
date: 2010-03-03
forum: General Help
---

### Post by vksingh on 2010-03-03
Hi,

While copying big folders in ubuntu using cp command, it takes a long time to copy in which no status comes on the console while copying.

Is there any way to see the status of copying big file while the system is copying the files?

Thanks,

Vivek

---

### Post by iponeverything on 2010-03-03
```
ls -lh file
```

Will show how much has been copied so far, from rerunning the command at a set interval you can deduce the rate.

---

### Post by Hellkeepa on 2010-03-03
HELLo!

In cases like these I like to use rsync, like this:
```
rsync -h --progress <big file> /new/target/
```

Happy copyin'!

---

### Post by rosant on 2010-03-03
Sorry, I am new to Linux and trying to get Windows out of my life, however, when I was trying to copy some files from Documents folder to a flash drive, I received a error message because the files I was trying to transfer had a total of 3.8 GB (122 .doc, .pdf and audio files) and the space available on the flash drive was 3.1GB, so no file was copied. That's weird to me because when I used to do this in Windows, the OS just started copying files until I run out of space, but Ubuntu did not copy a single file.
Is it the way the OS is or I need to setup something else?

---

