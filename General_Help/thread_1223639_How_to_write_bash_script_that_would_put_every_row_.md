---
title: "How to write bash script that would put every row in one file to its own file?"
date: 2009-07-26
forum: General Help
---

### Post by abcuser on 2009-07-26
Hi,
I have a ascii file like with 50 rows of text. I would like to write bash script which would write each row to its own file. So result of executed bash script should be 50 files.

How to write such a bash script?
Regards

---

### Post by DaithiF on 2009-07-26
something like:

while read line

---

### Post by DaithiF on 2009-07-26
sorry, hit enter too soon :)

```
while read line
do
echo $line > "$line"
done < filetoread
```

---

### Post by kaibob on 2009-07-26
What do you want the new files to be named? If you want the file name to be the same as the line of text, then see DaithiF's suggestion. Thus, for example, if line 1 of the input file is "this is a test" then the first new file would be named "this is a test" and would contain the text line "this is a test."

---

### Post by lswb on 2009-07-26
> **kaibob said:**
> What do you want the new files to be named? If you want the file name to be the same as the line of text, then see DaithiF's suggestion. Thus, for example, if line 1 of the input file is "this is a test" then the first new file would be named "this is a test" and would contain the text line "this is a test."

This might be OK for the OP purposes, but if there are 2 identical lines in the file the 2nd instance will overwrite the 1st instead of creating a separate file. If separate files for all lines including duplicate lines are required, a system of using numbered filenames could b included in the while loop, something like this
```

number=1
while read line
do
echo $line > "line$number"
(( number++ ))
done < filetoread

```

---

