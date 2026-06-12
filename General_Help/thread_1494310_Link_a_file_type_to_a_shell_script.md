---
title: "Link a file type to a shell script?"
date: 2010-05-26
forum: General Help
---

### Post by gdanko on 2010-05-26
I'm trying to figure out if it's possible to program the open action (double clicking on a file) for a given file extension in Gnome as:

Pass the file's absolute path to a shell script.

If so, how do I do this and how do I get the path?

---

### Post by kaibob on 2010-05-26
> **gdanko said:**
> I'm trying to figure out if it's possible to program the open action (double clicking on a file) for a given file extension in Gnome as:

Pass the file's absolute path to a shell script.

If so, how do I do this and how do I get the path?

You can define a shell script as the default open-with application for a specific file type. You can use "$1" in the shell script to obtain the path and name of the file you double-clicked on.

---

### Post by gdanko on 2010-05-26
Well it sort of works

test.sh is:

touch "/tmp/$1"
touch /tmp/asdf

When I doubleclick the file, /tmp/asdf is created but /tmp/filename is not.

---

### Post by gdanko on 2010-05-26
okay $0 is the name of the script being run (test.sh) but how do I get the name of the file I doubleclicked to launch it?

Let's say I have file type .abc
I link files of type .abc to test.sh which is a simple bash script

Now I doubleclick file.abc in the GUI, test.sh is launched. How do I get bash/sh to pull the name of the file that I doubleclicked, file.abc?

---

### Post by kaibob on 2010-05-26
> **gdanko said:**
> Well it sort of works

test.sh is:

touch "/tmp/$1"
touch /tmp/asdf

When I doubleclick the file, /tmp/asdf is created but /tmp/filename is not.
I believe that's because "$1" includes a path, which does not exist in the /tmp directory. For example, if "$1" is /home/kaibob/testfile.txt, you are telling touch to create the file /tmp/home/kaibob/testfile.txt. That path does not exist, so touch issues an error message (which you don't see) and does nothing else. 

To see this, you can redirect the error message to a text file by modifying you shell script as follows:

```
touch "/tmp$1" 2> /home/username/error.txt
```

I did this and got the following:

> touch: cannot touch `/tmp/home/kaibob/documents/testfile.txt': No such file or directory

---

### Post by gdanko on 2010-05-27
Again, 
I doubleclick on file.abc
Gnome is configured to open *.abc with test.sh

I dont want to capture the filename test.sh, I want to capture the name of the file I doubleclicked.

Make sense?

---

### Post by gdanko on 2010-05-27
test.sh is now:

echo $0 > /tmp/asdf
echo $1 >> /tmp/asdf
echo $2 >> /tmp/asdf

If I doubleclick file.abc, test.sh is run. The output of /tmp/asdf is

--start--
/home/gdanko/test.sh


--end--

Two blank lines, makes sense.
However, like I stated in the beginning. I want to get the name of the file I doubleclicked somehow.

---

### Post by geirha on 2010-05-27
You can parse out the basename with parameter expansion

```

echo "full path: $1"
echo "basename: ${1##*/}"
echo "dirname: ${1%/*}"

```

See [http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)

---

### Post by gdanko on 2010-05-27
> **geirha said:**
> You can parse out the basename with parameter expansion

```

echo "full path: $1"
echo "basename: ${1##*/}"
echo "dirname: ${1%/*}"

```

See [http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)

I don't care about the name of the shell script. What I want is the name of the file I doubleclicked from within Gnome/Nautilus.

---

### Post by geirha on 2010-05-27
> **gdanko said:**
> I don't care about the name of the shell script. What I want is the name of the file I doubleclicked from within Gnome/Nautilus.

It should be passed on as the first argument to the script ("$1"). Make sure you have set a she-bang (#!/bin/bash as the first line) for the script, and that it's executable.

---

### Post by gdanko on 2010-05-27
> **geirha said:**
> It should be passed on as the first argument to the script ("$1"). Make sure you have set a she-bang (#!/bin/bash as the first line) for the script, and that it's executable.

Bingo thank you much!

---

