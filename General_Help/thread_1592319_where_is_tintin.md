---
title: "where is tintin?"
date: 2010-10-10
forum: General Help
---

### Post by musendrophilus on 2010-10-10
I did apt-get for tintin++ but I can't find the program under usr/bin or my personal home directory.

What command do I enter in terminal to find it? After I did apt-get it wasn't added to my Applications menu. I'm using 9.04 in case that has any bearing upon the help.

---

### Post by WorMzy on 2010-10-10
The executable is installed to /usr/games/

If that directory is not in your PATH variable, then you can launch the game by opening a terminal and running ```
/usr/games/tt++
```

You can add the directory to your PATH variable if you want, just add
```
PATH=$PATH:/usr/games/
export PATH
``` to /etc/environment.


EDIT: Don't forget the "export PATH".

---

### Post by Rubi1200 on 2010-10-10
You can use the locate command:

```
locate -i tintin
```

the -i switch will ignore case sensitivity.

Also, according to their website you need to run it with the following command:
```
./tt++
``` from within the directory where you downloaded it to and installed it.

I am also going to assume it is a CLI application, which is why there is no menu entry.

---

### Post by musendrophilus on 2010-10-10
Thanks, I was trying typing out tintin++ to no avail.

---

### Post by Rubi1200 on 2010-10-10
You are welcome :)

But, just out of curiosity, which solution worked for you; mine or WorMzy's? (good to know for future reference, not because there is a competition to see whose solution works. We are all here to help).

---

