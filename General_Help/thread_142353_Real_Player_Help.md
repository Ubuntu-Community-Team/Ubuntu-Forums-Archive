---
title: "Real Player Help"
date: 2006-03-10
forum: General Help
---

### Post by khalidmian on 2006-03-10
I have been able to download Real Player 10 bin file on my desktop but when i try to install it using command suggested in Real.com my terminal window refuses to acknowledge presence of the bin file please help

---

### Post by Stealth on 2006-03-10
What do you mean fails to acknowledge?

You download the bin into your *home* dir right (I believe Firefox's default is to desktop)?
If you **ls** inside a terminal its not listed?

---

### Post by cjazz on 2006-03-10
Excuse me if the question is obvious, but are you typing

./RealPlayer10GOLD.bin

or whatever the name of the file is? If you don't include the slash-dot at the beginning, the shell checks your PATH for the name of the file, and that path does not, by default, include your home directory.

Also, before you run the file, be sure it's executable (chmod u+x filename).

---

### Post by bluevoodoo1 on 2006-03-10
[QUOTE=khalidmian]I have been able to download Real Player 10 bin file on my desktop but when i try to install it using command suggested in Real.com my terminal window refuses to acknowledge presence of the bin file please help[/QUOTE]

If you want to execute it from your Desktop you have to directories to Desktop.

```

cd ~/Desktop
```

---

