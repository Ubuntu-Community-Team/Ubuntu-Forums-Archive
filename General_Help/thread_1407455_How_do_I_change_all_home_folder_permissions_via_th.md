---
title: "How do I change all home folder permissions via the Terminal!"
date: 2010-02-15
forum: General Help
---

### Post by Rytron on 2010-02-15
Hi.
What command would I use to change all permissions on home folder as follows [picture attached]. I'd like the command to be recursive in order to cover all files and folders. I know I can change permissions via Nautilus but I also want a terminal method. I think it goes something like 777?

---

### Post by bluefrog on 2010-02-15
sudo chmod -R 755 folder

---

### Post by night_fox on 2010-02-15
use chmod. For details type > man chmod

press q to exit.

You probably want > chmod -R <more options> *

<more options> could be 777 or 755 but you are better off using things like +X +r +w etc because certain things may need to have different permissions. You can so easily create a mess by chmodding your home directory. I've done it so many times. I suggest backing up your stuff first?

---

### Post by akashiraffee on 2010-02-15
The command is chmod.  Eg:

**chmod 750 dirname**

chmod -R works recursively, but it works on the files inside as well as the directories.  This is a little awkward because you will need the execution bit set on readable directories (ie, directories should be set some combination of 7, 5 and 0), wheres as non-executable files should not have that set.

1 = execute
2 = write
4 = read

So 2+4 (read/write) = 6.  Read/execute = 5.  The first number of the 3 (eg, 750) is you, the second your group, the third everyone else.

---

