---
title: "Bash script help needed"
date: 2011-01-07
forum: General Help
---

### Post by binoplaza on 2011-01-07
Hey guys!

I'm trying to make a shell script that will inform me about new files that were created / modified. I'm having some issues with the variable that I use. I must do something wrong but the examples I found seem to do pretty much the same. Any suggestions?

```
#!/bin/bash
find //home/someUser/someFolder -type f \( -iname "*.avi" -o -iname "*.mkv" -o -iname "*.mp4" \) -ctime -1 | wc -l > count
echo 'numer of files is' $count
if [count = 0] ;
then
echo 'No New video files were downloaded in the past 24 hours'
else
echo 'New Video Downloads from the past 24 hours:\n\n'
find //home/someUser/someFolder/ -type f \( -iname "*.avi" -o -iname "*.mkv" -o -iname "*.mp4" \) -ctime -1 -printf '%f\n'
fi
echo '\n'
echo 'New Music Downloads from the past 24 hours:\n\n'
find //home/someUser/someFolder/ -type f -iname "*.mp3" -ctime -1 -printf '%f\n'
```

When I execute the script it says that it doesn't know count ...

---

### Post by dracayr on 2011-01-07
hi,

the line ```
find //home/someUser/someFolder -type f \( -iname "*.avi" -o -iname "*.mkv" -o -iname "*.mp4" \) -ctime -1 | wc -l > count
``` doesn't store the result of the find command in the variable count, it stores the result in a new file called count.
To use the variable count, write "count = find..." not "find... > count"

also, remove the semicolon after the if statement.

---

### Post by sisco311 on 2011-01-07
I would save the output of find in a temp file, then check if the file is empty or not.

Also put the -file test after the -name and -ctime test in order to avoid having to call stat(2) on every file.

Something like:
```
#!/usr/bin/env bash

find ... > ~/.tmp

if [ ! -s ~/.tmp ]; then
  echo "no new files"
else
  echo "new vid:"
  grep .mkv$ ~/.tmp

  echo "new audio:"
  grep .mp3$ ~/.tmp
fi

rm ~/.tmp

```

---

### Post by binoplaza on 2011-01-07
Thanks for your suggestion but if I try the following it will say on the next line that it doesn't know count. I would like to understand how to initialize and read out a variable afterwards properly in a shell script.

```

count = find //home/someUser/someFolder -type f \( -iname "*.avi" -o -iname "*.mkv" -o -iname "*.mp4" \) -ctime -1 | wc -l
echo 'Number of files' $count

```

The suggestion with the temporary file is intresting as well but as I said I would like to understand how to use the variables.

---

### Post by sisco311 on 2011-01-07
If you want to save the output of a command in a variable, you have to use command substitution:
```
man bash | less +/"Command Substitution"
```

---

### Post by binoplaza on 2011-01-07
> **sisco311 said:**
> If you want to save the output of a command in a variable, you have to use command substitution:
```
man bash | less +/"Command Substitution"
```

That seems indeed what I need but I'm still having problems:

```

count = $(find //home/***/*** -type f \( -iname "*.avi" -o -iname "*.mkv" -o -iname "*.mp4" \) -ctime -1 | wc -l)
echo 'numer of files is' $count

```

The second line gives still the error that it doesn't know count.

---

### Post by sisco311 on 2011-01-07
> **binoplaza said:**
> That seems indeed what I need but I'm still having problems:

```

count = $(find //home/***/*** -type f \( -iname "*.avi" -o -iname "*.mkv" -o -iname "*.mp4" \) -ctime -1 | wc -l)
echo 'numer of files is' $count

```

The second line gives still the error that it doesn't know count.

Actually the first line throws the error because there is a space after count, hence bash interprets it as a command:
```
count=$(find /...
```

---

### Post by binoplaza on 2011-01-07
I just found out that myself :)
I can print count now correctly. However when I want to check if it's zero it goes wrong
tried the following:
```

if [$count = 0]
if [$count -eq 0]

```

With or without brackets doesn't make difference, the script throws now an error ("checkForNewDownloads.sh: 11: [0: not found
") at the end of the if-statement.
I also tried to a compare count with a variable that was initialized to 0 but that didn't help either.

---

### Post by tgm4883 on 2011-01-07
> **binoplaza said:**
> I just found out that myself :)
I can print count now correctly. However when I want to check if it's zero it goes wrong
tried the following:
```

if [$count = 0]
if [$count -eq 0]

```

With or without brackets doesn't make difference, the script throws now an error ("checkForNewDownloads.sh: 11: [0: not found
") at the end of the if-statement.
I also tried to a compare count with a variable that was initialized to 0 but that didn't help either.

*************************
Scratch that, spending too much time in other languages.

A quick test shows that this works
```

#!/bin/bash

TEST=1

if [ $TEST = 0 ]; then
  echo "It's 0"
else
  echo "It's not 0"
fi

```

---

### Post by binoplaza on 2011-01-07
Got it almost working, I was causing myself a lot of troubles by inserting spaces before comparison and initialization.
Thanks for your help all!

Working script if anybody would be interested:
```

#!/bin/bash
count=$(find //home/someUser/someFolder -type f \( -iname "*.avi" -o -iname "*.mkv" -o -iname "*.mp4" \) -ctime -1 | wc -l)
echo 'numer of files is' $count
if [ $count=0 ];
then
echo 'No New video files were downloaded in the past 24 hours'
else
echo 'New Video Downloads from the past 24 hours:\n\n'
find //home/someUser/someFolder -type f \( -iname "*.avi" -o -iname "*.mkv" -o -iname "*.mp4" \) -ctime -1 -printf '%f\n'
fi
echo '\n'
echo 'New Music Downloads from the past 24 hours:\n\n'
find //home/someUser/someFolder -type f -iname "*.mp3" -ctime -1 -printf '%f\n'

```

But now if count = 1 or any other number different from 0, it doesn't go to the else :s

---

### Post by binoplaza on 2011-01-07
Solved it by using "-eq" in the if statement.

---

