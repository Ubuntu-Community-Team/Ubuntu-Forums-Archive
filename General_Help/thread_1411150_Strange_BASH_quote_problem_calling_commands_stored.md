---
title: "Strange BASH quote problem calling commands stored in a variable"
date: 2010-02-19
forum: General Help
---

### Post by dumb_question on 2010-02-19
I am having some weird problems with calling commands stored in a variable (I need to do this to assemble a command with a bunch of parameters automatically and then execute it).

Example code that will replicate the weirdness:

$ echo "hello world" > "test file.txt"
$ cat "test file.txt"
hello world
$bob='cat "test file.txt"'
$ echo $bob
cat "test file.txt"
$ $bob
cat: "test: No such file or directory
cat: file.txt": No such file or directory


I would expect the output to be:

hello world

What happens to the quotes? I have tried various combinations of single quotes, escaped quotes, etc, but it seems like quotes in a variable are not evaluated as quotes when that variable is executed. Any idea how I can get around this?

Thanks

---

### Post by d3v1150m471c on 2010-02-19
```

bob="hello world"
echo "$bob"

```

or...

```

echo "hello world" > test.txt
bob="cat test.txt"
$bob

```

---

### Post by dumb_question on 2010-02-19
> **d3v1150m471c said:**
> ```

bob="hello world"
echo "$bob"

```

or...

```

echo "hello world" > test.txt
bob="cat test.txt"
$bob

```

well, technically, I suppose so, but...

...what I'm actually trying to do with this is take a list of pdf files with arbitrary names (may include spaces), and string together a call to pdftk to stick them all together into one file. Unfortunately your examples do not generalize to that application (although I like the elegant simplicity of the first one...)

---

### Post by d3v1150m471c on 2010-02-19
cat file1.pdf file2.pdf file3.pdf > file4.pdf

---

### Post by d3v1150m471c on 2010-02-19
This should do the trick...

```

#!/bin/bash
#
# Merges multiple  documents as one
echo "1.Enter the documents to be merged"
echo "2.Seperate multiple files with a space"
                          echo " "
echo -n " "
      read docs
echo -n "Enter the new document name w/ path: "
      read newdoc
cat "$docs" > "$newdoc"
clear
exit 0

```

---

### Post by falconindy on 2010-02-19
> **d3v1150m471c said:**
> This should do the trick...
PDF files have a proper header and footer. You can't just cat them together, hence the need for software like pdftk.

OP: Given that some of your filenames may have spaces,  you may need to read the files into an array and then use the "${array[@]}" syntax to ensure that they're quoted when they're echoed out. I'm having trouble visualizing this without seeing what you're trying to combine. Are the files sorted in the order to be joined? Do they need to be combined N at a time? etc. etc.

---

### Post by rnerwein on 2010-02-19
> **dumb_question said:**
> I am having some weird problems with calling commands stored in a variable (I need to do this to assemble a command with a bunch of parameters automatically and then execute it).

Example code that will replicate the weirdness:

$ echo "hello world" > "test file.txt"
$ cat "test file.txt"
hello world
$bob='cat "test file.txt"'
$ echo $bob
cat "test file.txt"
$ $bob
cat: "test: No such file or directory
cat: file.txt": No such file or directory

I would expect the output to be:

hello world

What happens to the quotes? I have tried various combinations of single quotes, escaped quotes, etc, but it seems like quotes in a variable are not evaluated as quotes when that variable is executed. Any idea how I can get around this?

Thanks
hi
here is the trick ( "man eval" )
[COLOR=Red]eval $bob[/COLOR]  ==> hello world
the shell qoutes are a never ending story !

ciao

---

### Post by d3v1150m471c on 2010-02-19
Makes sense. This works, just tried it.

```

#!/bin/bash
#
# Merges multiple pdf documents as one
echo "1.Enter the documents to be merged"
echo "2.Seperate multiple files with a space"
echo
echo "Example: file.pdf file2.pdf"
echo
echo -n ": "
      read docs
echo -n "Enter the new document name w/ path: "
      read newdoc
pdftk "$docs" cat output "$newdoc"
clear
exit 0 

```

---

### Post by d3v1150m471c on 2010-02-19
bah, disregard this post please.

---

### Post by dumb_question on 2010-02-20
> **rnerwein said:**
> hi
here is the trick ( "man eval" )
[COLOR=Red]eval $bob[/COLOR]  ==> hello world
the shell qoutes are a never ending story !

ciao

Nice - thanks, that did the trick...

---

