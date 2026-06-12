---
title: "&quot;Open with&quot; with custom command"
date: 2010-01-16
forum: General Help
---

### Post by Aculaniveus on 2010-01-16
Hi guys. How can I make a program I wrote in C be used to open a specific file type? I am using Gnome and I tried right clicking on the file and then "Properties > Open With > Add > Use a custom command" and then adding my program's path but when I double click the file nothing happens.

Thanks in advance.

---

### Post by jamesisin on 2010-01-16
Open With --> Open with Other Application --> Use a custom command ?

Because this is a one-shot event.  This doesn't change the file-type association, for instance.

---

### Post by Simian Man on 2010-01-16
Does your program accept the name of the file from the argc/argc parameters?  Does it open a window at all or is it cli?  Does your program expect absolute file names?  Because that's how Gnome passes them.

---

### Post by Aculaniveus on 2010-01-16
> Does your program accept the name of the file from the argc/argc parameters? Does it open a window at all or is it cli? Does your program expect absolute file names? Because that's how Gnome passes them.  My program has a window, and it doesn't handle arguments yet, but I thought that it would at least open, ignoring the the arguments (files), when I double clicked the specified file type, but nothing happens.

---

### Post by slashpoke on 2010-01-19
> **Simian Man said:**
> Does your program accept the name of the file from the argc/argc parameters?  Does it open a window at all or is it cli?  Does your program expect absolute file names?  Because that's how Gnome passes them.

Hi, I am also making a program (in java) that I would like to open a file with. I am getting the program to run when double-clicking the file, so now all I need is to have it get the absolute filename in some way. I am using the custom command "java rar", but I would like to use something like "java rar <filename>". So I am wondering if this is possible, if so, how would I write it? If not, is there another way?

Edit: I found out what to do with some more google-ing, I used %f to use the filename as a parameter in my program. It is explained on: [http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html)

---

### Post by fishexe on 2010-05-24
> **Aculaniveus said:**
> My program has a window, and it doesn't handle arguments yet, but I thought that it would at least open, ignoring the the arguments (files), when I double clicked the specified file type, but nothing happens.

What happens when you type the filename, exactly as you entered it into the box, but on the command-line instead?  Does the window come up then?

---

