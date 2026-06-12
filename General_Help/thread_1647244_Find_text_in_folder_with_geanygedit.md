---
title: "Find text in folder with geany/gedit"
date: 2010-12-17
forum: General Help
---

### Post by hotstepperk on 2010-12-17
Hello.

I do alot of programming, and was wondering if there was a way I could search for a certain line of code, for instance, in a folder with many files like with Notepad++

I've seen across the forums that i can use grep, but i would like to be able to find the line in which its located, and display it properly.

Thanks in advance.

---

### Post by daqron on 2010-12-17
Have you tried [gedit-grep]("http://code.google.com/p/gedit-grep/")?

---

### Post by stinkeye on 2010-12-17
There is an add-on for gedit called GMate.
It adds numerous themes and plugins including search in folder.


To install
```
sudo apt-add-repository ppa:ubuntu-on-rails/ppa
sudo apt-get update
sudo apt-get install gedit-gmate
```

Once installed open *gedit > edit > preferences > plugins* and enable the **File Search** plugin.
There will now be a **search in files** entry under the search heading in the menu bar.
If you double click on one of the search results, the file it is contained in
is opened and the line number is shown in bold type.

---

### Post by daqron on 2010-12-17
> **stinkeye said:**
> There is an add-on for gedit called GMate.
Similar functionality to what I posted but seems more robust. I'd go with this one :)

---

