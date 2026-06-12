---
title: "Multi-file, multi-folder text search?"
date: 2012-07-06
forum: General Help
---

### Post by Rallg on 2012-07-06
Not a newbie, not a problem. Just a question:

Sometimes, I compile source code written by other people (I am not a programmer). Once in a while, I need to hunt through the source code so that I can change "SomeExpression" to "SomeOtherExpression" in text. But I do not know which of the numerous code files has what I need.

What I would like to do is use an application that lets me select a folder, then searches through all plain-text files (and subfolders), for a particular text string. Then it will tell me which files have the string.

Understand that I am NOT looking for a global search-and-replace command. That would be useful in other circumstances. Here, I need to open the file and look inside, to be sure that the change is appropriate. Then I can make the change myself.

Can anyone suggest a package that does this?

---

### Post by SeijiSensei on 2012-07-06
I just use grep from the command line for this:

```
grep 'string to search' *
```

If I need to search in subdirectories, I just change "*" to "*/*" then "*/*/*" until I get the "no such file or directory".  Actually if someone knows how tell grep to recurse through the directory tree, I'd like to know.  I've looked through the man page a number of times and don't see anything equivalent to a "-r" switch to recurse.

---

### Post by steeldriver on 2012-07-06
I've resorted to something like this in the past

```
find -name "*.cs" -exec grep -Hnw "mytext" {} \;

```or if you want ONLY the files (not the matching strings)

```
find -name "*.cs" -exec grep -l "mytext" {} \;

```

---

### Post by Rallg on 2012-07-06
Thanks. I'll try that. I was afriad to use grep (or anything like it) because I didn't actually want to replace any text directly, just find the files.

Incidentally: Since I first posted my question, I located a free program for Windows that will work under WINE (with added dll). It's probably just a GUI for something like grep.

---

### Post by SeijiSensei on 2012-07-06
Grep just searches.  The corresponding command for replacing text is sed.

```
sed 's/string to find/string to replace/g' < file
```

The first entry can be a regular expression as well as an ordinary string.  The delimiter can actually be any character not in the string.  So if I wanted to replace "you/me" I'd use something like

```
sed 's%you/me%me/you%g' < file
```

---

### Post by Vaphell on 2012-07-06
> If I need to search in subdirectories, I just change "*" to "*/*" then "*/*/*" until I get the "no such file or directory". Actually if someone knows how tell grep to recurse through the directory tree, I'd like to know. I've looked through the man page a number of times and don't see anything equivalent to a "-r" switch to recurse.

i don't even... ;-)

```
$ grep --help
...
-R, -r, --recursive
...
```

```
grep -r word .
```

---

### Post by SeijiSensei on 2012-07-06
I don't know how I've missed that.  I even looked at the man page before writing my earlier comment.  

Well, thanks, even if you made me feel foolish!

---

