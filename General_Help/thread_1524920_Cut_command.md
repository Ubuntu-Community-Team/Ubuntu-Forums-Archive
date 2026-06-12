---
title: "Cut command"
date: 2010-07-05
forum: General Help
---

### Post by agamjain on 2010-07-05
I need a command to seperate a part or a column from the output of an 'ls -ltra' command. Suppose I do 'lts -ltra', I get an output with multiple column and multiple rows. I need a command by which I can obtain the first column of the result and parse through it row by row. Kindly help me out.

---

### Post by Johnny B on 2010-07-05
awk is a command built exactly for this purpose:
```
ls -ltra | awk '{print $1}'
```
$1 will give you the first column, $2 for the second... etc

---

### Post by agamjain on 2010-07-05
I was trying this command, and I agree that it would print the first column. But what I need is a command by which I can compare the rows of the first column with a value row by row. For that I need to parse the column. How can I achieve that?

---

### Post by Johnny B on 2010-07-06
are you asking to print one line at a time?
i am not sure what you mean by "compare the rows of the first column with a value row by row"

---

### Post by kaibob on 2010-07-06
Like Johnny B, I am uncertain precisely what you want to do and in what context. Perhaps a shell script such as the following will do what you want.

```
#!/bin/bash

while read -r status _ _ _ _ _ _ file ; do
  [ "$status" = -rw-r--r-- ] && echo "$file"
  [ "$status" = -rw------- ] && echo "$file"
done < <(ls -lra)
```

The use of the ls command in a bash shell script is generally frowned upon, but that's the question you asked. You may want to review the following FAQ, which discusses obtaining file permissions without parsing ls -l output:

[http://mywiki.wooledge.org/BashFAQ/087](http://mywiki.wooledge.org/BashFAQ/087)

---

### Post by agamjain on 2010-07-06
> **kaibob said:**
> Like Johnny B, I am uncertain precisely what you want to do and in what context. Perhaps a shell script such as the following will do what you want. Just insert the comparison in place of "echo $column_1".
 
```
#!/bin/bash
 
ls -ltra | while read -r column_1 _ ; do
  echo $column_1
done
```
 
The use of the ls command in a bash shell script is generally frowned upon, but that's the question you asked. You may want to review the following FAQ, which discusses obtaining file permissions without parsing ls -l output:
 
[http://mywiki.wooledge.org/BashFAQ/087](http://mywiki.wooledge.org/BashFAQ/087)
I will tell you precisely what I need. I am using CVS for a project of mine. I run the command 'cvs -nq update' which gives me the list of packages which have been checked out by the user for updation. Now, the result of running this command gives me an output just like 'ls -ltra' for a directory. But here, the first column of the output tells me the status of the software package. Now, I need a command by which I can check this status for each of the rows and perform different operations based on the status.

---

### Post by agamjain on 2010-07-06
> **Johnny B said:**
> are you asking to print one line at a time?
i am not sure what you mean by "compare the rows of the first column with a value row by row"
 I don't need to print anything. I need to parse the first column row by row.

---

### Post by mandar.mitra on 2010-07-06
> **agamjain said:**
> I don't need to print anything. I need to parse the first column row by row.


Did you try something like:


awk '{ if ($1 == "something") { ... } else if ($1 == "something else") { } ...}'

---

### Post by agamjain on 2010-07-06
> **mandar.mitra said:**
> Did you try something like:
 
 
awk '{ if ($1 == "something") { ... } else if ($1 == "something else") { } ...}'
 Will this command run for all the rows of the output?

---

### Post by mandar.mitra on 2010-07-06
> **agamjain said:**
> Will this command run for all the rows of the output?


Yes. You can either specify the file(s) on the command line (e.g. "awk ... abc.txt"), or you can pipe the output of some command to awk (e.g. "ls -ltra | awk ..."). Take a look at the man page for awk, or any of a number of internet tutorials on awk.

---

### Post by agamjain on 2010-07-06
> **mandar.mitra said:**
> Yes. You can either specify the file(s) on the command line (e.g. "awk ... abc.txt"), or you can pipe the output of some command to awk (e.g. "ls -ltra | awk ..."). Take a look at the man page for awk, or any of a number of internet tutorials on awk.
 I will try it out and get back to you people if something does not work out. Thanks for the help.

---

