---
title: "For Loop and Files Names with Spaces"
date: 2011-11-19
forum: General Help
---

### Post by jfluckey on 2011-11-19
I am writing a script to rename files and I have hit a wall.  I have in a directory with the following (2) files:

testfile1
test file 2

If I have the following script:

```
Files=`ls -p | grep -v / | grep -v .sh`  #Eliminates directories and script file
for i in $Files
  do
     echo $i
  done
```The output of this script is: 
```
testfile1
test
file
2
```I expect the output to be:
```
testfile1
test file 2
```How do I obtain this?  Also, I put quotes around "$Files" in the loop declaration, but the output then became:
```
testfile1  test file 2
```

---

### Post by Toz on 2011-11-19
Try this:
```

IFS=$'\n'
for file in $(ls -p | grep -v / | grep -v .sh)
do
   echo "$file"
done
```

---

### Post by papibe on 2011-11-19
Hi jfluckey.

If you quote your variables, you'll get rid of the spaces problem:
```
Files=$(ls -p | grep -v / | grep -v .sh)  # Eliminates directories and script file
for i in "$Files"
do
    echo "$i"
done
```
Note also that the syntax $( ) is preferred to the old back ticks.

Another way to get the files in the actual directory that are not shell scripts would be:
```
find -maxdepth 1 -type f -not -name '*.sh'
```
That will have the same output as the 'for' above. If you want to do more interesting things besides printing the list you can use the output of the find into a loop:
```
while read -r file
do
    echo "$file"
    # something more interesing with "$file"
    #....
done < <(find -maxdepth 1 -type f -not -name '*.sh')
```
Now, if you want to be very strict, there could be a rare problem when files have other problematic characters in their names (like newlines). Then this would be the safest way to go:
```
while IFS= read -r -d '' file
do
    echo "$file"
    # something more interesing with "$file"
    #....
done < <(find -maxdepth 1 -type f -not -name '*.sh' -print0)

```
Hope it helps,
Regards.

---

### Post by jfluckey on 2011-11-26
> **Toz said:**
> Try this:
```

IFS=$'\n'
for file in $(ls -p | grep -v / | grep -v .sh)
do
   echo "$file"
done
```


O.K. I am back and going over the responses.  The above fixed my problem.  

I read somewhere else that I don't want to be changing IFS willy nilly, so I changed the code to:

```

Files=$(ls -p | grep -v / | grep -v .sh)  #changed syntax per comment of post #3
IFSOLD=$IFS
IFS=$'\n'
   for i in $Files
    do
      echo "file is $i"
    echo
    done
IFS=$IFSOLD
```I will now check my results per the comments of papibe.

---

### Post by jfluckey on 2011-11-26
> **papibe said:**
> Hi jfluckey.

If you quote your variables, you'll get rid of the spaces problem:
```
Files=$(ls -p | grep -v / | grep -v .sh)  # Eliminates directories and script file
for i in "$Files"
do
    echo "$i"
done
```Note also that the syntax $( ) is preferred to the old back ticks.

My goal is to rename the files in the for loop.  Per the statement before the last quote box of my original post, I put "$Files" in the declaration of the for loop, but it does not work.  Again, and perhaps a little clearer results, if I have files named "testfile1" and "test file 2" the output of the following code: ```

for i in "$Files"
do
   echo "file is $i"
done
```is ```

file is testfile1
test file 2
```

---

### Post by jfluckey on 2011-11-26
> **papibe said:**
> 
If you want to do more interesting things besides printing the list you can use the output of the find into a loop:
```
while read -r file
do
    echo "$file"
    # something more interesing with "$file"
    #....
done < <(find -maxdepth 1 -type f -not -name '*.sh')
```Now, if you want to be very strict, there could be a rare problem when files have other problematic characters in their names (like newlines). Then this would be the safest way to go:
```
while IFS= read -r -d '' file
do
    echo "$file"
    # something more interesing with "$file"
    #....
done < <(find -maxdepth 1 -type f -not -name '*.sh' -print0)

```Hope it helps,
Regards.

I am new to scripting so I need a little help with these unfamiliar commands.  Can you go through the first (while loop) and last (done) line and and explain what the shell is doing?  Also, it looks like the only differences between your last two code boxes is adding -d in the while loop and -print0 at the EOF.  Please touch on how the those two differences affect the results.

Finally, the output of these scripts does give me desirable results.  It is a little more work to manipulate the file name to what I want than the solution given by Toz because the output of the echo appends "./" to the beginning of the file name.  I could see where this would be beneficial in some applications, but not in mine.  Regardless, I was given two working solutions and I thank you both.

---

### Post by fdrake on 2011-11-26
how about
```

url=`find -maxdepth 1 -type f | cut -d "/" -f 2 | grep -v .sh`
for i in $url
do 
 echo "this is file $i"
done

```
this will get rid of the "./" of the path of the file

---

### Post by jfluckey on 2011-11-26
> **fdrake said:**
> how about
```

url=`find -maxdepth 1 -type f | cut -d "/" -f 2 | grep -v .sh`
for i in $url
do 
 echo "this is file $i"
done

```this will get rid of the "./" of the path of the file

A couple methods of defining a vector of file names has been given:

1.)  find -maxdepth 1 -type f | cut -d "/" -f 2 | grep -v .sh
2.)  ls -p | grep -v / | grep -v .sh

The first is nice because it could easily be changed to go deeper in the directory tree if it were desired.  Is there any other advantages of one over the other?  Sometimes different solutions to the same problems are not supposed to be used in Linux (e.g. using "sudo gedit" instead of "gksudo gedit" (I still haven't taken the time to find why on this either)).

---

