---
title: "How to break a long string in multiple lines bash command"
date: 2009-10-01
forum: General Help
---

### Post by zggame on 2009-10-01
I try to write a bash script with "sed" command.  it has a very long string 

such as this

#!/bin/bash
sed -e \
"s|[0-9a-zA-Z/-]*\(year20\)\([0-9a-zA-Z]*\)/person00\([0-9a-zA-Z]*\)/00\([0-9a-zA-Z]*.wav\)|mv & \2\3\4|g"<$1 >$2

It works just fine as one line, but pretty difficult to edit in tools like nano.  I am wondering how to break it down into several lines.  I tried to add "\" with a new line, but it completely messed up the pattern.  :confused:

I understand this is probably not the most proper place for such questions?  But this is the forum I used mostly and I am fairly new to bash script.  Can anyone point me to some better place?

---

### Post by StuartN on 2009-10-02
> **zggame said:**
> I am wondering how to break it down into several lines.

Type a "\" before the carriage return and the carriage return will be ignored, eg:

```
stuart@mypc:~$ echo this \
> is one line
this is one line
```

---

### Post by geirha on 2009-10-02
You might want to have a look at the rename command in Ubuntu. It renames files based on regular expressions. Though, it uses perl-regexes which has some slight differences to the regular expressions sed uses.

This first hit on google shows some nice examples:
[http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

---

### Post by zggame on 2009-10-03
That works for things not in " ", (I used it before -e "..."), but for the part in "", I want to break this long pattern in "", \ does not work there.   

> **StuartN said:**
> Type a "\" before the carriage return and the carriage return will be ignored, eg:

```
stuart@mypc:~$ echo this \
> is one line
this is one line
```

---

### Post by zggame on 2009-10-03
> **geirha said:**
> You might want to have a look at the rename command in Ubuntu. It renames files based on regular expressions. Though, it uses perl-regexes which has some slight differences to the regular expressions sed uses.

This first hit on google shows some nice examples:
[http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

That is really nice. But my case is more complicated. I have a directory trees, every node has the files with the same name. I need to move them into one directory, so I have to encode some path name into the file name.

---

### Post by akakingess on 2009-10-03
Trying to dig into the memory banks, but will /n or /b not work, or am I digging the memory banks for another language? I know that sounds silly, but if I'm not currently in "bash" mode, I might be in "python" mode, or something like that.

---

### Post by bigboy_pdb on 2009-10-03
You can use variables to store parts of the pattern. For example:
```

year='((1|2)[0-9]{3})' # A year between 1000 and 2999
month='(0[1-9]|1[0-2])' # The month (from 01 to 12)
day='(0[1-9]|[12][0-9]|3[01])' # The day (from 01 to 31)
div='[/-]' # The separator (a slash or dash)

date="${year}${div}${month}${div}${day}"

# NOTE: The curly brackets aren't necessary in this case but they improve readability.

# Can be separated onto different lines if the line gets too long
date="${year}${div}"\
"${month}${div}"\
"${day}"

```

The pattern that I've written could have a much more rigid date format (ie. 2000-02/31 would be considered valid when it isn't), but it shows how you can use variables to split up patterns.

---

### Post by StuartN on 2009-10-03
> **zggame said:**
> That works for things not in " ", (I used it before -e "..."), but for the part in "", I want to break this long pattern in "", \ does not work there.

You can simply concatenate multiple quoted strings, with a \-newline in between them, e.g. sed "s/string1/string2/" can be expressed as:

  sed "s/""string1/""string2/"

or

  sed "s/"\
  "string1/"\
  "string2/"

---

### Post by geirha on 2009-10-03
> **zggame said:**
> That is really nice. But my case is more complicated. I have a directory trees, every node has the files with the same name. I need to move them into one directory, so I have to encode some path name into the file name.

Which is where rename comes in...

```

level1='[[:alnum:]-]*year20([[:alnum:]]*)'
level2='person00([[:alnum:]]*)'
level3='00([[:alnum:]]*\.wav)'
find . -type f -name "*.wav" -exec \
    rename -n "s|\./$level1/$level2/$level3|\$1\$2\$3|" {} +

```

A bit of guessing on how the directory tree looks here, but I'm sure you can adapt it.

---

### Post by zggame on 2009-10-04
Thank you all very much.  They are all great tips.

---

