---
title: "print a list of all file types in a folder?"
date: 2012-10-11
forum: General Help
---

### Post by sohlinux on 2012-10-11
I want to print to the screen a list of all file types *.ext in a folder and its sub_folders

so the list will be something like this

avi
txt
jpg
doc

---

### Post by foxmulder881 on 2012-10-11
What is wrong with good old ```
~ $ ls
```

You might also find the tree command useful.

```
~ $ sudo apt-get install tree
```
```
~ $ tree
```

---

### Post by sohlinux on 2012-10-11
> **foxmulder881 said:**
> What is wrong with good old ```
~ $ ls
```

You might also find the tree command useful.

```
~ $ sudo apt-get install tree
```
```
~ $ tree
```

yes I know ls and tree but I only want to see the file types not a massive list of everything in the folder and sub_folders as there are 10000s of files

I just want a list like this showing the different file types

avi
txt
jpg
doc

---

### Post by btindie on 2012-10-11
You can get a list of all extensions with the following
```
find . -type f | sed -e 's/^.*\.\([^\.]*$\)/\1/' -e '/^\//d' | sort -u
```
First cd to the top directory, it'll then print every unique extension it finds. If a file doesn't have an extension it'll be excluded from the list.

---

### Post by sohlinux on 2012-10-11
> **btindie said:**
> You can get a list of all extensions with the following
```
find . -type f | sed -e 's/^.*\.\([^\.]*$\)/\1/' -e '/^\//d' | sort -u
```
First cd to the top directory, it'll then print every unique extension it finds. If a file doesn't have an extension it'll be excluded from the list.

thanks
:p:p

---

### Post by foxmulder881 on 2012-10-11
Holy crap, even after 10 years Unix usage, I've never seen a command look like that. Well done. :-)

---

