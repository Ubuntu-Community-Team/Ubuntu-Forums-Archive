---
title: "Basic Scripting Help"
date: 2012-04-04
forum: General Help
---

### Post by SupaRice on 2012-04-04
How can I create a simple script that will check for the existance of a set of numbers within a file listing previous sets?

For example:

Does 11 55 88

Exist in the following list

66 77 99
42 33 29
88 55 11

And order is not relevant. So in the above example, there would be a match for the last line. I was trying to think of a way of doing this in Libre Office, but couldn't get it to work even seperating numbers into different fields.

---

### Post by zero2xiii on 2012-04-04
Hay,

Seems like (after some googling) there is no simple answer, seeing as the order does not matter. How ever, you might try something like this, I dont have time to write code and test it. But here is the outline:

Value 11 22 88
Asign $1 $2 $3

String to test: 
Value 22 11 88
Asign $4 $5 $6

Test sequence: If ${1..3}=${4..6} then +1 $string_match
If $string_match => then echo "String match" else "string doesn't match"...

This should be easy to do, as AWK allows using data already in coloums by specifing it:
[http://www.unix.com/unix-dummies-questions-answers/26884-grep-column-please-help.html](http://www.unix.com/unix-dummies-questions-answers/26884-grep-column-please-help.html)
> In its simplest usage awk is meant for processing column-oriented text data, such as tables, presented to it on standard input. The variables $1, $2, and so forth are the contents of the first, second, etc. column of the current input line. For example, to print the second column of a file, you might use the following simple awk script: 
        awk < file '{ print $2 }'
 This means "on every line, print the second field". 

 To print the second and third columns, you might use 
        awk < file '{ print $2, $3 }'


Comparing the inputs to each other is as easy as en if statement:

```
If [ "a$1" -eq "a$4" ]
then
   $match="$match + 1"
fi
```


This may be seriously errorous.. But thats the rough idea I have.. May be a MUCH simpler way... I am just to asleep to think straight atm.

Cherz

EDIT
Fixed some major typos.. and Gave more relavent info... I am seeing dubble and its not cause of bubble :) hahahaha:lolflag:

---

### Post by TeoBigusGeekus on 2012-04-04
A (very) lazy approach:
```
grep '11 55 88\|11 88 55\|88 11 55\|88 55 11\|55 88 11\|55 11 88' /path/file
```

---

### Post by Vaphell on 2012-04-04
quick and dirty, slighly less lazy approach ;-)
```
rec="55 11 88"
sorted_rec=$( echo "$rec" | tr " " "\n" | sort | tr "\n" " " )
sorted_rec=${sorted_rec% }; sorted_rec=${sorted_rec# }
echo "rec: ($rec) -> ($sorted_rec)"

while read line
do
  sorted_line=$( echo "$line" | tr " " "\n" | sort | tr "\n" " " );
  sorted_line=${sorted_line% }; sorted_line=${sorted_line# };
  echo "($line) -> ($sorted_line)" $( if [ "$sorted_line" = "$sorted_rec" ]; then echo "LINE FOUND ($rec)"; fi )
done < input_file
```

output```

rec: (55 11 88) -> (11 55 88)
(66 77 99) -> (66 77 99)
(42 33 29) -> (29 33 42)
(88 55 11) -> (11 55 88) LINE FOUND (55 11 88)

```

sorting input and lines of data file and testing sorted forms against each other

---

### Post by SupaRice on 2012-04-04
Wow... Thanks guys!

That last one looks like what I'm after. But I'm confused... Not sure what I'm looking at there. My script-fu is not the strongest.

---

### Post by Vaphell on 2012-04-04
it's time to change that unpleasant fact then ;-)

first part takes the data to find and sorts it
echo prints it, tr takes over and replaces spaces with newlines (sort works with lines not words), sort takes over and sorts (duh), and then tr makes the opposite transformation: newlines to spaces. Store the result in variable: var=$( ... ). Next line trims left- and rightmost spaces, should they exist after transformations, and now you have sorted data in original format, as evidenced by 'rec: (...) -> (...)' line

now *while read line; do ...; done < file* reads the file one by one, line variable holding the content
for each line variable is used to get the sorted line.
in if you compare the 2 sorted variables - if they match do whatever you want. Here if is embedded in a quite verbose echo which may make it look complicated but by looking at the output you can easily figure out how it works

if you want to make a script of it
```
#!/bin/bash

rec="$1 $2 $3"   # if parameters are separate numbers xx yy zz
# or
# rec="$1" # if parameter passed to the script is single string "xx yy zz"

# sort elems
sorted_rec=$( echo "$rec" | tr " " "\n" | sort | tr "\n" " " )
# trim space at the: end of variable; start of variable
sorted_rec=${sorted_rec% }; sorted_rec=${sorted_rec# }
# print rec and sorted version of rec
echo "rec: ($rec) -> ($sorted_rec)"

# read input_file line by line
while read line
do
  sorted_line=$( echo "$line" | tr " " "\n" | sort | tr "\n" " " );
  sorted_line=${sorted_line% }; sorted_line=${sorted_line# };
  # print line, sorted line and marker if line matches rec
  echo "($line) -> ($sorted_line)" $( if [ "$sorted_line" = "$sorted_rec" ]; then echo "LINE FOUND ($rec)"; fi )
done < input_file

```
then make it executable
```
chmod +x script_name
```

run it like this
```
./script_name 22 11 33
```

---

### Post by markbl on 2012-04-04
This kind of thing is much easier done in python (and I have been programming unix/linux shell script for >20 years)
```

#!/usr/bin/env python
import sys
data = [sorted(line.split()) for line in open('input_file')]
print 'Line was%s found' % ('' if sorted(sys.argv[1:]) in data else ' not')

```
Put this in a file and run same usage as previous shell example.

---

### Post by SupaRice on 2012-04-05
Thanks so much for the responses guys! I'm going to play around with these, learn something new every day! :)

---

### Post by codemaniac on 2012-04-05
a simple
```
awk '/11/ && /55/ && /88/' */path/to/file*
``` would do it .

---

### Post by SupaRice on 2012-04-06
> **codemaniac said:**
> a simple
```
awk '/11/ && /55/ && /88/' */path/to/file*
``` would do it .

Blammo!

U ---> :guitar:

That works perfectly.

---

