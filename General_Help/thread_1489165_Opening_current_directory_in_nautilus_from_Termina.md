---
title: "Opening current directory in nautilus from Terminal"
date: 2010-05-20
forum: General Help
---

### Post by Darkness Des on 2010-05-20
Like the title says, I want to be able to open the directory I'm browsing in nautilus. To clarify this, as I barely understand what I said, I'll give an example.


```
cd ~/what/ever/this/is/complex/path
```Hmmm.... A lot of files in here with long complex names and I only want to move certain ones..... Better open it in nautilus with my handy dandy script/alias!


And so on.

---

### Post by oldos2er on 2010-05-20
```
sudo apt-get install nautilus-open-terminal
```

---

### Post by Darkness Des on 2010-05-20
It says I already have it. Is that the script to open a terminal with current location as the working directory? I have that one installed. I want the opposite of it though.

---

### Post by Ozymandias_117 on 2010-05-20
You should be able to just type ```
nautilus .
``` I'm not on my GNU/Linux box to test it for sure right now though.

---

### Post by Darkness Des on 2010-05-20
It does work! Thank you very much, now all I have to do is add an Alias to it.

---

