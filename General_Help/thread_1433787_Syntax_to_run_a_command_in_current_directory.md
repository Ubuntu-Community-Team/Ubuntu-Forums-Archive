---
title: "Syntax to run a command in current directory"
date: 2010-03-19
forum: General Help
---

### Post by Pingster on 2010-03-19
Why doesn't bash know that when I type a command it might be in the current directory.  In other words, instead of using
```
./command
```
why can't I use
```
command
```

---

### Post by Chris Musampa on 2010-03-19
I've wondered this myself, it doesn't cause me a problem, it just seems a bit strange not to search the current directory first.

---

### Post by Ancanus on 2010-03-19
You can't just use 'command' because you do not have the current directory ".", in your PATH environment variable. You can see your PATH environment variable by typing: ```
# echo $PATH
```You can add . to your PATH variable by opening ~/.bashrc with your favorite editor and adding a line such as:

```
export PATH=$PATH:.
```Save the file, run ```
# exec bash
```and try again.

---

