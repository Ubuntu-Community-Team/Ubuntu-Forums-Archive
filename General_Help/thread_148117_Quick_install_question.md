---
title: "Quick install question"
date: 2006-03-21
forum: General Help
---

### Post by baysl on 2006-03-21
I've extracted *.tgz file to a folder.

Now I dont know how to install this program...
Folder contains *.c , *.txt , *.html files.
How do I install?

---

### Post by christhemonkey on 2006-03-21
Have a read of the .txt and .html files to see what they say, but then try running the .c files.
```
./whatever.c
```
might need to do a sudo on that.  What exactly are you trying to install?

---

### Post by taurus on 2006-03-21
[QUOTE=christhemonkey]Have a read of the .txt and .html files to see what they say, but then try running the .c files.
```
./whatever.c
```
might need to do a sudo on that.  What exactly are you trying to install?[/QUOTE]
Don't you have to compile it first before you can run it???
```

gcc filename.c
./a.out

```
However, chances are probably need to run 
```

./configure
make
sudo make install

```
But before you can build anything from source, you need to install build-essential first...
```

sudo apt-get install build-essential

```

---

### Post by christhemonkey on 2006-03-21
haha o yeah, sorry bout that, slipped my mind....!

---

### Post by baysl on 2006-03-21
But there are a couple of *.c files, and a lot of txt and html...
I'm trying to install Exploit...
Do I compile them all?

---

### Post by az on 2006-03-21
[QUOTE=baysl]But there are a couple of *.c files, and a lot of txt and html...
I'm trying to install Exploit...
Do I compile them all?[/QUOTE]
Can you give an URL?

Is there a readme?  Is there a file named install?  They give you the steps to getting the application compiled and running.

---

