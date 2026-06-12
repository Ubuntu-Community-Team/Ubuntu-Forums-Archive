---
title: "Software not working anymore"
date: 2011-04-27
forum: General Help
---

### Post by mattiav on 2011-04-27
Hi everyone!

I have a big problem with my Ubuntu 10.10: part of the software I installed isn't working anymore and I cannot un-install it because Ubuntu says the software doesn't exist, but using  the command which Ubuntu can find the executable file.

For example: with smongo (a program I use to make plots) 

```

mattia@mattia-ubuntu:~$ smongo
bash: /usr/local/bin/sm: File o directory non esistente

```but using the command which I have:

```

mattia@mattia-ubuntu:~$ which sm
/usr/local/bin/sm

```the same thing happens with foxit. 

What can I do?

---

### Post by user1397 on 2011-04-27
try to remove any remaining config files and the sort: ```
sudo apt-get purge smongo
``` and then try re-installing it

---

### Post by mattiav on 2011-04-27
It says "impossible to find the package smongo"

---

