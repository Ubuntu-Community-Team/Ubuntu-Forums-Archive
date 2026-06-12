---
title: "Where can I access a list of all installed packages?"
date: 2009-08-17
forum: General Help
---

### Post by rogueleader12345 on 2009-08-17
I have a computer with Intrepid on it that my only way to get new programs, etc is through packages.ubuntu.com. Of course, if I don't have one of the dependencies, it won't work, and I have to go download that package too. I was wondering if there was an alphabetical list of all packages installed on a computer that I could save and pull up as a reference whenever I'm downloading new packages. I know I can look up all installed packages in Synaptic, but does it have a way to make a printable list? Thanks!

---

### Post by bowens44 on 2009-08-17
In a terminal issue the following command:

dpkg -l

---

### Post by apparle on 2009-08-17
You can use the command ```
dpkg --get-selections >> list.txt

```
A list.txt file will be created at the location wherever you are.
but make sure that the file is not already present. If it is already present then the new data will be added to end of the file.

If you are going open the list in windows then use Wordpad as notepad will not recognize the newline

If you don't have net and are installing packages then give this a try [http://keryxproject.org/](http://keryxproject.org/)

---

