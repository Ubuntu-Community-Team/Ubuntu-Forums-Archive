---
title: "Script to replace characters in text file"
date: 2011-06-30
forum: General Help
---

### Post by Kissell on 2011-06-30
I have an odd request, lets say I have a text file like this:
> ```

__##___##___IIIIII
__##___##_____II__
__##___##_____II__
__#######_____II__
__##___##_____II__
__##___##_____II__
__##___##___IIIIII

```


I want a script that will replace all of the hash tabs with random characters.

I found this command will generate a random character
> 
apg -a1 -n1 -m1 -x1 -d


So I guess I just need to know how to script a search and replace using that random character upon each successive find until the end of file occurs.  Can anyone help me do this?

---

### Post by Kissell on 2011-06-30
This kinda works
> 
#!/bin/bash
for j in {1..31}
do
  char=`apg -a1 -n1 -m1 -x1 -d`
  echo $char 
  sed -i '0,/#/s/#/'$char'/' test.txt
done


Resulted in this... which is what I wanted.
> 
__qj___h;___IIIIII
__o1___=<_____II__
__vS___Y:_____II__
__,=vr~?8_____II__
__+~___>8_____II__
__Y*___+}_____II__
__TU___3#___IIIIII
 

---

### Post by Kissell on 2011-06-30
Although my solution does "work", it runs unbelievably slow.  I have no idea why it is so slow.  Maybe it would run faster if I could load the file into memory instead of writing each character one at a time to the disk.

On top of that, it includes some randomly generated characters that are problematic, like quote symbols.  There is a -E parameter to exclude symbols generated, and it works on the command line, but I can't get it to work in the script.

---

### Post by Azdour on 2011-06-30
Hi,

I thought I would have a play, not sure what you need it for or if my attempt is what you are looking for:

```
#!/bin/bash

function randchar
{
char=`</dev/urandom tr -dc A-Za-z0-9 | head -c1`
}


for j in {1..31}
do
randchar
sed -i '0,/#/s/#/'$char'/' text.txt
done
```

---

### Post by sisco311 on 2011-06-30
I'm not very good with awk, but this seams to work:
```

#!/usr/bin/awk -f

BEGIN{
    OFS=FS=""
    srand()
    for(i = 48;i <=122;i++){
        if(i == 58)i+=7
        if(i == 91)i+=6 
        arr[++c] = sprintf("%c", i)
    }
}

{
    for(i=1;i<=NF;i++) sub(/\#/,arr[1 + int(rand() * c)],$i)
}1

```

I stole the ideas from [here]("http://www.linuxquestions.org/questions/programming-9/generate-special-alphanumeric-wordlist-no-repeating-characters-side-by-side-862473/#post4257327") and [here]("http://www.unix.com/302432042-post3.html").

---

### Post by Kissell on 2011-06-30
> **Azdour said:**
> Hi,

I thought I would have a play, not sure what you need it for or if my attempt is what you are looking for:

```
#!/bin/bash

function randchar
{
char=`</dev/urandom tr -dc A-Za-z0-9 | head -c1`
}


for j in {1..31}
do
randchar
sed -i '0,/#/s/#/'$char'/' text.txt
done
```

Yeah, its a bit of an odd thing to do, really just playing.  I set the for value from 1 to 31 because there were 31 hash tabs in my example...  however in real world practice there will be many more than 31...  there were 1499 in my real world file.  It would be nice to not have to count those and edit the script based on that count.  Either by the sed failing to find a hashtab, or pre-counting the number before entering the loop.

---

### Post by prodigy_ on 2011-06-30
Try something like this:
```
#!/bin/bash

# Disable '*' wildcard with set -f to protect $RandString elements.
set -f
IFS=#

# Create an array from source file.
StoredText=( $(< $1) )

# Get random string (printable characters only, no whitespaces or hashes).
# Create another array.
RandString=( $(dd if=/dev/urandom bs=$(( ${#StoredText[@]} * 5 )) count=1 2>/dev/null | \
	tr -dc [:graph:] | tr -d '#' | sed 's/./&#/g') )

# Leave the first element untouched.
printf "%s" "${StoredText[0]}" > $1

for (( i=1; i<${#StoredText[@]}; i++ ))
do
	# Append everything else, one element (from each array) at a time.
	printf "%s" "${RandString[$i]}${StoredText[$i]}" >> $1
done

printf "\n" >> $1
```

---

### Post by sisco311 on 2011-06-30
@prodigy_

Your script works, but it's a little bit slow :evil:
```
sisco@acme:~/xtmp$ ls -alh file
-rw-r--r-- 1 sisco sisco 19K 2011-06-30 23:57 file

sisco@acme:~/xtmp$ time ./prodigy_ > new

real	0m46.690s
user	0m10.559s
sys	0m5.370s

sisco@acme:~/xtmp$ time ./sisco311 file > new

real	0m0.053s
user	0m0.030s
sys	0m0.000s

```

---

### Post by prodigy_ on 2011-06-30
> **sisco311 said:**
> Your script works, but it's a little bit slow
If compared to what? :) I'm sorry, but your awk code doesn't work on a random character sequence. And I don't know awk well enough to even read it.

---

### Post by sisco311 on 2011-06-30
> **prodigy_ said:**
> If compared to what? :) I'm sorry, but your awk code doesn't work on a random character sequence. And I don't know awk well enough to even read it.

How did you test it? You have to pass the input file as an argument and it prints the output to stdout. It should replace the hashes with a random alphanumeric character.

---

### Post by Kissell on 2011-06-30
Thanks guys, they both work.  This will have endless implications for me, its not just about doing this task, but in having the ability to write similar scripts, like one that will take out the carriage returns from the ends of files.  I often web browse on my windows machine, copy and paste your scripts into notepad, then save them on the server, but have to go in and edit out the ^M at the end of every line before the script will run.  Being able to read a file and search and replace characters from the command line will help me in all sorts of ways.

I like that prodigy's solution is similar to mine, so I understand what's going on, and it generates special characters which is nice.  

But damn, sisco311's is fast.  Don't have a clue how it works, but it works quick.

---

### Post by sisco311 on 2011-06-30
> **Kissell said:**
> Thanks guys, they both work.  This will have endless implications for me, its not just about doing this task, but in having the ability to write similar scripts, like one that will take out the carriage returns from the ends of files.  I often web browse on my windows machine, copy and paste your scripts into notepad, then save them on the server, but have to go in and edit out the ^M at the end of every line before the script will run.  Being able to read a file and search and replace characters from the command line will help me in all sorts of ways.


Check out: dos2unix ans sed (search for sed one liners).

> **Kissell said:**
> it generates special characters which is nice.  


The for loop from the BEGIN stanza reads the alphanumeric characters in an array (ascii 48-57=[0-9], ascii 65-90=[A-Z] and ascii 97-122=[a-z]). You can rewrite it to include other characters too. 

> **Kissell said:**
> 
But damn, sisco311's is fast.  Don't have a clue how it works, but it works quick.

In the second block awk reads the file line by line and
the second for loop replaces each hash with a random element from the array (arr).


Your scripts are slow because You invoke sed too many times.

---

### Post by cybergalvez on 2011-06-30
> **Kissell said:**
> I have an odd request, lets say I have a text file like this:


I want a script that will replace all of the hash tabs with random characters.

I found this command will generate a random character


So I guess I just need to know how to script a search and replace using that random character upon each successive find until the end of file occurs.  Can anyone help me do this?

this should work using python

```

import random
import string

rc = ''.join(string.letters) + ''.join(string.digits) + ''.join(string.punctuation)

infile = file('in.txt').readlines()
outfile = file('out.txt', 'w')

for line in infile:
	l2 = ""
	for l in line:
		if l == '#':
			l2 += random.choice(rc)
		else:
			l2 += l
	outfile.write(l2)
outfile.close()


```

---

### Post by prodigy_ on 2011-06-30
> **sisco311 said:**
> You have to pass the input file as an argument and it prints the output to stdout. It should replace the hashes with a random alphanumeric character.
Strangely, didn't work.

[Modified my script for better performance.](http://ubuntuforums.org/showpost.php?p=10999097&postcount=7) :) Here, processing ~360 Kb from /dev/urandom as a test:

```

$ dd if=/dev/urandom bs=1000000 count=1 2>/dev/null | tr -dc [:print:] > filename

$ cat filename | wc -m
371605

$ grep -o '#' filename | wc -l
3898

$ time bash ./test.sh

real	0m0.573s
user	0m0.448s
sys	0m0.128s

$ cat filename | wc -m
371605

$ grep -o '#' filename | wc -l
0
```

---

### Post by sisco311 on 2011-06-30
> **prodigy_ said:**
> Strangely, didn't work.


Strange indeed. I tested it in mawk (Ubuntu uses it) and gawk (Arch) and it worked for me. 

> **prodigy_ said:**
> 
[Modified my script for better performance.](http://ubuntuforums.org/showpost.php?p=10999097&postcount=7) :) Here, processing ~360 Kb from /dev/urandom as a test:

```

$ dd if=/dev/urandom bs=1000000 count=1 2>/dev/null | tr -dc [:print:] > filename

$ cat filename | wc -m
371605

$ grep -o '#' filename | wc -l
3898

$ time bash ./test.sh

real	0m0.573s
user	0m0.448s
sys	0m0.128s

$ cat filename | wc -m
371605

$ grep -o '#' filename | wc -l
0
```

Cool. I didn't read carefully the whole script, but if you want to make it a bit faster, you should use **$(< file)** instead of **$(cat file)** and I think, that here strings are faster than piping echo to tr or sed. Oh, well, I will check out your script tomorrow. :)

---

### Post by prodigy_ on 2011-06-30
OK, got rid of **echo** and **cat**. :)

---

### Post by sisco311 on 2011-07-01
And here is my bash variant:
```

#!/bin/bash

rand=( 0 1 2 3 4 5 6 7 8 9
       a b c d e f g h i j
       k l m n o p q r s t
       u v w x y z
       A B C D E F G H I J
       K L M N O P Q R S T
       U V W X Y Z )


while IFS= read -r line
do
  for ((i=0; i<${#line}; i++))
  do
    if [[ ${line:i:1} == \# ]]
    then
      echo -n "${rand[RANDOM % ${#rand[@]}]}"
    else
      echo -n "${line:i:1}"
    fi
  done
  echo
done < "$1"

```

```
sisco@acme:~/xtmp$ time ./sisco311_2 file > new

real	0m1.861s
user	0m1.297s
sys	0m0.107s

```

---

