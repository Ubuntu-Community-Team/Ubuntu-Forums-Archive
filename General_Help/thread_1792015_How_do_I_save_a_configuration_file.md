---
title: "How do I save a configuration file"
date: 2011-06-27
forum: General Help
---

### Post by Noo 2 Ubuntoo on 2011-06-27
in my home folder?

I am trying to follow this advice [1.http://ubuntuforums.org/showpost.php?p=9650052&postcount=6]("http://ubuntuforums.org/showpost.php?p=9650052&postcount=6")

In this advice Stinkeye says "save this config in your home folder as **.conkyrc**" 

As a noobie I am guessing s/he means it should be written at the terminal and then somehow saved to the home folder using the terminal.

But how? Or have I misunderstood the advice? 

Please can someone give me some idiot (Noo2Ubuntoo) proof advice on how to do this?

---

### Post by WorMzy on 2011-06-27
Open a text editor (e.g. gedit), paste the configuration inside, and save the file as ".conkyrc" inside your home folder (/home/username).

You don't need to use a CLI-based text editor, but you can if you want to.

---

### Post by PCNetSpec on 2011-06-27
```
sudo gedit ~/.conkyrc
```

Paste everthing you want into gedit... and SAVE.

You won't be able to see the .conkyrc file in your home directory without hitting **Ctrl+H**, because all files that start with "." are hidden by default.

hth

---

### Post by nothingspecial on 2011-06-27
> **PCNetSpec said:**
> ```
sudo gedit ~/.conkyrc
```




You don't want to be sudoing it. [-X

and even if you did, it should be gksudo rather than sudo

---

### Post by PCNetSpec on 2011-06-27
Oops...

Yup, ignore the sudo... my appologies.

---

### Post by Noo 2 Ubuntoo on 2011-06-27
Thanks all -easy when you know how.

---

