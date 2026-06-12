---
title: "Issue creating a menu item with arguments"
date: 2012-06-10
forum: General Help
---

### Post by raptir on 2012-06-10
I'm trying to create menu items for my dosbox games. To launch one of the games from the terminal, I need to run the following command:

```
dosbox -conf ~/.dosbox/c/Ultima1/dosboxULTIMA1.conf
```

Running that command at the terminal works fine, but when I use Alacarte to create a menu item and enter that text as the command, I just get dosbox without loading that config file. I've also tried creating a .desktop file by hand and entering the above text as the Exec=, but I get the same result. Is there something else I need to do to add arguments to a menu item?

---

### Post by Nytram on 2012-06-10
It could be that the home character isn't getting expanded, try using the absolute path, for ex:

> dosbox -conf /home/yourusername/.dosbox/c/Ultima1/dosboxULTIMA1.conf

Edit: I've just tested it on my setup and the above command should work.

---

