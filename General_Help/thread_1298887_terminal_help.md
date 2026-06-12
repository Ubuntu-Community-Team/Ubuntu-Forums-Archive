---
title: "terminal help"
date: 2009-10-23
forum: General Help
---

### Post by eldutcho on 2009-10-23
Hello, im trying to install a plugin for pidgin.It wants me to navigate to a folder in my home directory and use the make command to compile it, however I have no idea how to open this folder in the terminal. now matter what i try to type, it always give me a bash:no such file or command.
obviously I'm making some simple mistake, but its frustrating

web page for what im trying to do:
[http://code.google.com/p/pidgin-personalbar/wiki/PluginGet](http://code.google.com/p/pidgin-personalbar/wiki/PluginGet)

any help with be rewarded with my undying gratitude

If this isn't clear enough ill try to make more sense

---

### Post by P4man on 2009-10-23
to change directory in a terminal just type

```
cd nameofdirectory
```

But keep in mind commands and names are CASE sensitive!

BTW, you dont need to type the entire name, you can type the first few letters and then hit the TAB key. If there is only 1 possible match, it will fill it out for you, if there are many, press tab again to see all possibilities

---

### Post by golanbatrac on 2009-10-23
To check if the .purple directory exists, open terminal and type the following:

```

ls -a $HOME | less

```If .purple is in your home directory, type:

```

mv $HOME/pidgin-personalbar/pidgin-personalbar.so $HOME/.purple

```If .purple is not in your home directory, type:

```

mkdir $HOME/.purple

```to create the .purple directory, and then move the .so file to the new directory

```

mv $HOME/pidgin-personalbar/pidgin-personalbar.so $HOME/.purple

```

---

