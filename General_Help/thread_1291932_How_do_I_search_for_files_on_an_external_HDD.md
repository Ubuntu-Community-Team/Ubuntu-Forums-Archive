---
title: "How do I search for files on an external HDD?"
date: 2009-10-15
forum: General Help
---

### Post by Steve Francis on 2009-10-15
I want to do two types of searches of data files which are stored on an external HDD:

(a) Find any text file (*.txt) where the string "supplier" appears in the body of the text file

(b) Find any text file starting with the letter K (K*.txt) created within the last two months

What's the easiest way to do this?

It's easy in Windows Explorer but I can't for the life of me find an application that might do it in Ubuntu (except Tracker, which is reported as buggy and CPU-intensive)

---

### Post by HNS-I on 2009-10-15
for A)
find /path/to/basedir/ -name *.txt -exec -l supplier {} \;

---

### Post by StuartN on 2009-10-15
> **Steve Francis said:**
> It's easy in Windows Explorer

I like Krusader and others like Gnome Commander. If you install one of these then you get some really good search and file management tools. Either of them is added as a regular application and does not replace or interfere with anything you have.

---

### Post by lloyd_b on 2009-10-15
> **HNS-I said:**
> for A)
find /path/to/basedir/ -name *.txt -exec -l supplier {} \;

You forgot something :)
```
find /path/to/basedir/ -name *.txt -exec **grep** -l supplier {} \;
```

Lloyd B.

---

### Post by HNS-I on 2009-10-15
oh dear! :KS
Well I guess it's not what the OP is looking for either.

---

### Post by justleen on 2009-10-15
for b)
```
find /path/to/find/dir -ctime -60 -name K*.txt 
```

Mind, ctime will actually look for when a file was changed. 60 in this case is 60*24hours.  -60 means within that period, +60 would give files outside that period (changed more then 60 days ago)

---

### Post by Steve Francis on 2009-10-21
Thanks for your suggestions.

I am going to experiment first off with Gnome Commander.

All the best
Steve

---

### Post by Steve Francis on 2009-11-12
> **Steve Francis said:**
> I want to do two types of searches of data files which are stored on an external HDD:

(a) Find any text file (*.txt) where the string "supplier" appears in the body of the text file

(b) Find any text file starting with the letter K (K*.txt) created within the last two months

What's the easiest way to do this?

It's easy in Windows Explorer but I can't for the life of me find an application that might do it in Ubuntu (except Tracker, which is reported as buggy and CPU-intensive)

Doh! The perfect search tool was already installed by default...

Go to the Places menu and click on Search for Files... and choose "Select more options..."

I can apply search filters I want using the above. Wonder why nobody suggested that?

---

