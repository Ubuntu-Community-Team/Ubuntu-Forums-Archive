---
title: "how do i search for a folder?"
date: 2011-03-16
forum: General Help
---

### Post by meself on 2011-03-16
[FONT="Arial"]
Embarrassingly elementary question, but I know how to search the filesystem for a file using the file name or part of the file name.  But how do I search the filesystem for a folder using the folder name or part of the folder name?

I am running Ubuntu 10.04.[/FONT]

---

### Post by TeoBigusGeekus on 2011-03-16
```
find /path/to/search -iname "searchpattern" -type d 2>/dev/null
```
Replace searchpattern with a valid... search pattern for your folder.

---

### Post by meself on 2011-03-16
Theo,
Thank you for trying to help.  But I ran that line of code in Terminal, replacing "searchpath" with the foldername, both with and without the quotes.  And all I got was a new prompt on a new blank line.

---

### Post by TeoBigusGeekus on 2011-03-16
Could you please post the command you used, as well as the name (partial or full) of the folder you want to find?

---

### Post by meself on 2011-03-16
find /path/to/search -iname "schemes" -type d 2>/dev/null
and also -
find /path/to/search -iname schemes -type d 2>/dev/null

I am trying to locate the schemes folder in jEdit so I can insert my color scheme that I created in windows.  But anticipate having perhaps a reoccuring need to search for a folder again sometime.

---

### Post by TeoBigusGeekus on 2011-03-16
> **meself said:**
> find /path/to/search -iname "schemes" -type d 2>/dev/null
and also -
find /path/to/search -iname schemes -type d 2>/dev/null


Please don't tell me that you've actually used /path/to/search.
It was meant to be replaced as well...

To search your entire filesystem for a folder named something like schemes, do
```
find / -iname "*schemes*" -type d 2>/dev/null
```
As you can see, I replaced the path to be searched with the root path (/).
If you believe that the folder is in your home partition, replace / with ~/ and so on.

---

### Post by meself on 2011-03-16
TheoBigusGeekus,

That worked.  Thank you!  I'm sure it will be useful on an ongoing basis too.

It was so kind of you to help me out!

---

