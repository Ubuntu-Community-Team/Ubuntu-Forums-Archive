---
title: "Help needed in creating a &quot;launcher&quot;"
date: 2011-11-23
forum: General Help
---

### Post by raghav.venky on 2011-11-23
I use Cyberoam to use the Internet. I have to log in every time i start the computer.

It has a client for windows which is a program which i have to double-click and i'll be logged in upto shutdown.

It has a client for linux too. everything is the same except that I have to run the following code in the terminal:
./crclient -u <username>

I tried creating a launcher but it does not work.

---

### Post by lechien73 on 2011-11-23
Hi,

How did you create the launcher, exactly?

Do you normally just drop to a terminal window and run the command? If so, then it's running from the current directory, which would likely be your home directory.

Try changing the command in the launcher to:

```
/home/<my ubuntu username>/crclient -u <username>
```

Replace <my ubuntu username> with the username you use to log on to Ubuntu. It's the bit before the @ sign in the terminal window command prompt.

---

### Post by raghav.venky on 2011-11-23
As soon as I start the terminal, I run the command. It works.
I think it's because i have copied the 'crclient.exe' to my 'Home' folder.

---

### Post by raghav.venky on 2011-11-23
Also should i use 'Application' or 'Application in Terminal'?

---

### Post by raghav.venky on 2011-11-23
I tried the code you gave. It didn't work.

---

### Post by lechien73 on 2011-11-23
I downloaded the crclient and tried it myself.

It appears that the program checks whether it has been executed directly or from a launcher/script. If it hasn't been executed directly, then it fails.

The answer, from my research, appears to be that you can only execute this program from a terminal window and not from a launcher.

---

### Post by raghav.venky on 2011-11-23
Wow that sucks!
Why would they do that??

Anyway, thanks a lot.

Is there any bypass?

---

