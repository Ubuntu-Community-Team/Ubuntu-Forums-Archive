---
title: "arrgh"
date: 2010-10-16
forum: General Help
---

### Post by Kingcheese26 on 2010-10-16
hi people. I really just started using linux a few months ago. everything's been smooth, except for compiling software. I've read how to do it, and tried, but every time it seems to fail. Can someone give me an explanation of every step, every single detail? please?

---

### Post by dtfinch on 2010-10-16
Did you install the build-essential package? What are you trying to compile?

---

### Post by Mike'sHardLinux on 2010-10-16
Probably the most common problem when compiling is satisfying dependencies. What software are you trying to install? Have you checked to make sure you have all the dependencies?

---

### Post by Kingcheese26 on 2010-10-16
i tried to compile EDE (Equinox Desktop environment). when i try to unpack the tar.gz file it says "no such file or directory." How do i get the computer to recognise the file???

---

### Post by Kingcheese26 on 2010-10-16
also, it doesn't recognize the ./configure command

---

### Post by Mike'sHardLinux on 2010-10-16
Well, configure won't do you much good until after you have unpacked the source.

Are you sure you ran the tar command in the proper directory, or if you are not in the same directory as the tar.gz file, did you include the correct path of the file?

---

