---
title: "Adding New Sequential Sub-Folders via BASH Script"
date: 2010-01-09
forum: General Help
---

### Post by Trapper on 2010-01-09
I am really stuck. I have a situation where I have a folder named parts. In parts I have numerous subfolders labeled sprocket1, sprocket2, spoke1, spoke2, spoke3, rim1, rim2, etc.

I need to occasionally create new sequential subfolders via a bash script. I am not versed in bash but have been trying for several days to put something together but I don't even get close.

Let's say I need to create a sequential spoke subfolder. As listed above, we know that would be spoke3. But let's say we don't know what the sequence number is for the last created spoke subfolder. How can I determine that via bash and create a new subfolder in sequence?

---

### Post by falconindy on 2010-01-09
Too bad. I actually had (past tense) a script that did just this, but with a slightly different purpose. No matter, it's not difficult!

This script takes 2 arguments -- the first is the base folder name, and the second is how many more folders of that name to create. I spent far too much time making it clever.
```
#!/bin/bash

[[ $# -ne 2 ]] && {
    echo "Error: requires a folder name and the number of folders to make";
    exit 1;
}

[[ ! -d "$1*" ]] && {
    mkdir -p "${1}1";
    set "$1" $(( $2 - 1 ))
}

base_file="$(echo "$1" | awk -F\/ '{print $NF}')"
max=$(basename "$(ls -d $1* | sort -n | tail -1)")
next=$(( ${max//$base_file} + 1 ))

for i in $(seq $next 1 $(( $next + $2 - 1 ))); do
    mkdir -p "$(dirname $1)/${base_file}${i}"
done

```
So something like.... './moreparts.sh /path/to/parts/chain 4' would make the folders (assuming none exist):
/path/to/parts/chain1
/path/to/parts/chain2
/path/to/parts/chain3
/path/to/parts/chain4

If spoke3 exists and you run the script with parts/spoke 2, it should create:
parts/spoke4
parts/spoke5

Notice that it should handle relative versus absolute paths properly.

Let me know if you have any problems with it.

edit: clean up quoting to handle white space properly.

---

### Post by Trapper on 2010-01-09
I appreciate you sharing this script with me falconindy. I've been working with it but my results have been negative. I have enclosed some of my attempts below.

```
trapper@Ubuntu-910-64:~$ sh moreparts.sh /home/trapper/parts/spoke 3 
moreparts.sh: 2: [[: not found 
Error: requires a folder name and the number of folders to make 
: not foundh: 3: 
``````
trapper@Ubuntu-910-64:~$ bash moreparts.sh /home/trapper/parts/spoke 3 
Error: requires a folder name and the number of folders to make 
: command not found3: 
``````
trapper@Ubuntu-910-64:~$ ./moreparts.sh /home/trapper/parts/spoke 3 
bash: ./moreparts.sh: /bin/bash^M: bad interpreter: No such file or directory
```Here's a listing of what's in /home/trapper/parts prior to and after running the script.
```
trapper@Ubuntu-910-64:~$ ls /home/trapper/parts 
chain1  handlebars1  spoke1  spoke2
```

---

### Post by falconindy on 2010-01-09
Amusing. Your first example (using sh) obviously doesn't work because sh is tripping on my double square brackets. Invoking with Bash doesn't work because you're modifying the number of arguments... taking out the first few lines that checks that would fix it.

However, the third error shows that the file is formatted Windows style with \r\n linebreaks rather than \n. Make sure you're not trying to copy this script and save it from Windows.

edit: Quick rewrite to make it sh compatible and remove the arg check at the start.

```

#!/bin/sh

[ ! -d $1* ] && {
    mkdir -p "${1}1";
    set $1 $(( $2 - 1 ))
}

base_file=$(echo "$1" | awk -F\/ '{print $NF}')
max=$(basename "$(ls -d $1* | sort -n | tail -1)")
next=$(( ${max//$base_file} + 1 ))

for i in $(seq $next 1 $(( $next + $2 - 1 ))); do
    mkdir -p "$(dirname $1)/${base_file}${i}"
done

```

---

### Post by Trapper on 2010-01-10
> **falconindy said:**
> 

However, the third error shows that the file is formatted Windows style with \r\n linebreaks rather than \n. Make sure you're not trying to copy this script and save it from Windows.

I am definitely not using windows but what you say here did ring a bell. I am using geany and recently saved some text files to send to a windows user. I had geany set up to save in windows format and I never changed back from that. After reverting back to unix format in geany I copied, pasted and saved your original script. 

I was able to run the following to create new folders: ```
./moreparts.sh /home/trapper/parts/spoke 3
```

If no folders are present it creates spoke1, 2 & 3. If one or more spoke folders are present it creates 2 folders. If I continue to rerun the script it will do this up to and including spoke11. If I have spoke11 it will give me zero new folders. If I change the parameters to spoke 4 with 11 folders present it will give me one new folder (spoke12)

---

### Post by falconindy on 2010-01-10
Heh, it's failing partially because I wrote it as a Bash script and it didn't enjoy my 5 second attempt at converting to Dash... so Bash is how it'll be. ;) Hmm, it's tripping on the sort... how to fix...

```
#!/bin/bash

[[ ! -d "${1}1" ]] && {
    mkdir -vp "${1}1";
    set "$1" $[ $2 - 1 ];
}

base_file=$(echo "$1" | awk -F\/ '{print $NF}')
max=$(ls -d ${1}[[:digit:]]* | sed -e 's/.*\/[A-Za-z]*//g' -e sed 's/[A-Za-z]*//' | sort -n | tail -1)
next=$[ $max + 1 ]

for i in $(seq $next 1 $[ $max + $2 ]); do
    mkdir -vp "$(dirname $1)/${base_file}${i}"
done
```

Basically a rewrite. Realized I was approaching it from the wrong angle and it was prone to other bugs (like trying to make a chain directory when chainring already existed). It's verbose now too, so you know exactly what it's doing.

This is proving to be slightly trickier than dealing with files when I did this last time. I have a strange attraction to shell scripting though, so I've been having fun doing this. Sorry to "drag" you along.

Sample output...
```
 [haruko@quake ~]$ rm -r tmp
 [haruko@quake ~]$ bin/moreloops.sh tmp/chain 3
mkdir: created directory `tmp'
mkdir: created directory `tmp/chain1'
mkdir: created directory `tmp/chain2'
mkdir: created directory `tmp/chain3'
 [haruko@quake ~]$ bin/moreloops.sh tmp/chainring 3
mkdir: created directory `tmp/chainring1'
mkdir: created directory `tmp/chainring2'
mkdir: created directory `tmp/chainring3'
 [haruko@quake ~]$ bin/moreloops.sh tmp/chainring 3
mkdir: created directory `tmp/chainring4'
mkdir: created directory `tmp/chainring5'
mkdir: created directory `tmp/chainring6'
 [haruko@quake ~]$ bin/moreloops.sh tmp/chainring 3
mkdir: created directory `tmp/chainring7'
mkdir: created directory `tmp/chainring8'
mkdir: created directory `tmp/chainring9'
 [haruko@quake ~]$ bin/moreloops.sh tmp/chainring 3
mkdir: created directory `tmp/chainring10'
mkdir: created directory `tmp/chainring11'
mkdir: created directory `tmp/chainring12'
 [haruko@quake ~]$ bin/moreloops.sh tmp/chainring 24
mkdir: created directory `tmp/chainring13'
mkdir: created directory `tmp/chainring14'
mkdir: created directory `tmp/chainring15'
mkdir: created directory `tmp/chainring16'
mkdir: created directory `tmp/chainring17'
mkdir: created directory `tmp/chainring18'
mkdir: created directory `tmp/chainring19'
mkdir: created directory `tmp/chainring20'
mkdir: created directory `tmp/chainring21'
mkdir: created directory `tmp/chainring22'
mkdir: created directory `tmp/chainring23'
mkdir: created directory `tmp/chainring24'
mkdir: created directory `tmp/chainring25'
mkdir: created directory `tmp/chainring26'
mkdir: created directory `tmp/chainring27'
mkdir: created directory `tmp/chainring28'
mkdir: created directory `tmp/chainring29'
mkdir: created directory `tmp/chainring30'
mkdir: created directory `tmp/chainring31'
mkdir: created directory `tmp/chainring32'
mkdir: created directory `tmp/chainring33'
mkdir: created directory `tmp/chainring34'
mkdir: created directory `tmp/chainring35'
mkdir: created directory `tmp/chainring36'
```

---

### Post by Trapper on 2010-01-11
Oh, you're not just dragging me along falconindy. I am enjoying this too.

As for your latest ... I am definetly not getting the same results as you. Here's what I ran and my results:

```
trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/spoke 3 
mkdir: created directory `/home/trapper/parts/spoke1' 
sed: -e expression #2, char 3: unterminated `s' command 
mkdir: created directory `/home/trapper/parts/spoke2' 
trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/spoke 3 
sed: -e expression #2, char 3: unterminated `s' command 
mkdir: created directory `/home/trapper/parts/spoke3' 
trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/spoke 3 
sed: -e expression #2, char 3: unterminated `s' command 
trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/spoke 3 
sed: -e expression #2, char 3: unterminated `s' command 
trapper@Ubuntu-910-64:~$
```The result of all this was folders spoke1, 2 & 3

Here's another. It's one folder shy.

```
trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/sprocket 7 
mkdir: created directory `/home/trapper/parts/sprocket1' 
sed: -e expression #2, char 3: unterminated `s' command 
mkdir: created directory `/home/trapper/parts/sprocket2' 
mkdir: created directory `/home/trapper/parts/sprocket3' 
mkdir: created directory `/home/trapper/parts/sprocket4' 
mkdir: created directory `/home/trapper/parts/sprocket5' 
mkdir: created directory `/home/trapper/parts/sprocket6' 
trapper@Ubuntu-910-64:~$ 
```
Here's what I'm running:
```
#!/bin/bash

[[ ! -d "${1}1" ]] && {
    mkdir -vp "${1}1";
    set "$1" $[ $2 - 1 ];
}

base_file=$(echo "$1" | awk -F\/ '{print $NF}')
max=$(ls -d ${1}[[:digit:]]* | sed -e 's/.*\/[A-Za-z]*//g' -e sed 's/[A-Za-z]*//' | sort -n | tail -1)
next=$[ $max + 1 ]

for i in $(seq $next 1 $[ $max + $2 ]); do
    mkdir -vp "$(dirname $1)/${base_file}${i}"
done

```

---

### Post by falconindy on 2010-01-11
:oops: I see the mistake. I have an extra 'sed' in there. Made the change locally, guess I never edited it here.

```
# Out with the old...
max=$(ls -d ${1}[[:digit:]]* | sed -e 's/.*\/[A-Za-z]*//g' -e sed 's/[A-Za-z]*//' | sort -n | tail -1)

# In with the new...
+max=$(ls -d ${1}[[:digit:]]* | sed -e 's/.*\/[A-Za-z]*//g' -e 's/[A-Za-z]*//' | sort -n | tail -1)
```

---

### Post by Trapper on 2010-01-11
Okay falconindy, here's the script as I now have it, what I ran and the results:

```
#!/bin/bash

[[ ! -d "${1}1" ]] && {
    mkdir -vp "${1}1";
    set "$1" $[ $2 - 1 ];
}

base_file=$(echo "$1" | awk -F\/ '{print $NF}')
+max=$(ls -d ${1}[[:digit:]]* | sed -e 's/.*\/[A-Za-z]*//g' -e 's/[A-Za-z]*//' | sort -n | tail -1)
next=$[ $max + 1 ]

for i in $(seq $next 1 $[ $max + $2 ]); do
    mkdir -vp "$(dirname $1)/${base_file}${i}"
done
``````
trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/sprocket 1 
mkdir: created directory `/home/trapper/parts/sprocket1' 
./moreparts3.sh: line 9: +max=1: command not found 

trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/sprocket 1 
./moreparts3.sh: line 9: +max=1: command not found 

trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/sprocket 1 
./moreparts3.sh: line 9: +max=1: command not found 

trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/sprocket 4 
./moreparts3.sh: line 9: +max=1: command not found 
mkdir: created directory `/home/trapper/parts/sprocket2' 
mkdir: created directory `/home/trapper/parts/sprocket3' 
mkdir: created directory `/home/trapper/parts/sprocket4' 

trapper@Ubuntu-910-64:~$ 
``````
trapper@Ubuntu-910-64:~$ ls /home/trapper/parts/
sprocket1  sprocket2  sprocket3  sprocket4
```

---

### Post by Trapper on 2010-01-11
I found the problem:

The corrected line starts with a '+' I removed it and the script works correctly.

```
#Old Line:
+max=$(ls -d ${1}[[:digit:]]* | sed -e 's/.*\/[A-Za-z]*//g' -e 's/[A-Za-z]*//' | sort -n | tail -1)

#New line:
max=$(ls -d ${1}[[:digit:]]* | sed -e 's/.*\/[A-Za-z]*//g' -e 's/[A-Za-z]*//' | sort -n | tail -1)
```Results:

```
trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/sprocket 1 
mkdir: created directory `/home/trapper/parts/sprocket1' 
trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/sprocket 1 
mkdir: created directory `/home/trapper/parts/sprocket2' 
trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/sprocket 1 
mkdir: created directory `/home/trapper/parts/sprocket3' 
trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/sprocket 1 
mkdir: created directory `/home/trapper/parts/sprocket4' 
trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/sprocket 4 
mkdir: created directory `/home/trapper/parts/sprocket5' 
mkdir: created directory `/home/trapper/parts/sprocket6' 
mkdir: created directory `/home/trapper/parts/sprocket7' 
mkdir: created directory `/home/trapper/parts/sprocket8' 
trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/sprocket 8 
mkdir: created directory `/home/trapper/parts/sprocket9' 
mkdir: created directory `/home/trapper/parts/sprocket10' 
mkdir: created directory `/home/trapper/parts/sprocket11' 
mkdir: created directory `/home/trapper/parts/sprocket12' 
mkdir: created directory `/home/trapper/parts/sprocket13' 
mkdir: created directory `/home/trapper/parts/sprocket14' 
mkdir: created directory `/home/trapper/parts/sprocket15' 
mkdir: created directory `/home/trapper/parts/sprocket16' 
trapper@Ubuntu-910-64:~$ ./moreparts3.sh /home/trapper/parts/sprocket 2 
mkdir: created directory `/home/trapper/parts/sprocket17' 
mkdir: created directory `/home/trapper/parts/sprocket18' 
trapper@Ubuntu-910-64:~$  
```So, I think the script below does the trick but I will test it more.

```
#!/bin/bash

[[ ! -d "${1}1" ]] && {
    mkdir -vp "${1}1";
    set "$1" $[ $2 - 1 ];
}

base_file=$(echo "$1" | awk -F\/ '{print $NF}')
max=$(ls -d ${1}[[:digit:]]* | sed -e 's/.*\/[A-Za-z]*//g' -e 's/[A-Za-z]*//' | sort -n | tail -1)
next=$[ $max + 1 ]

for i in $(seq $next 1 $[ $max + $2 ]); do
    mkdir -vp "$(dirname $1)/${base_file}${i}"
done
```

---

### Post by falconindy on 2010-01-11
> **Trapper said:**
> I found the problem:

The corrected line starts with a '+' I removed it and the script works correctly.
Ahh yes, a remnant leftover from the diff between your script and mine. Serves me right for looking at code at 7:30am (pre-coffee). Glad it's finally working. Feel free to holler if it breaks.

---

### Post by Trapper on 2010-01-11
> **falconindy said:**
> Ahh yes, a remnant leftover from the diff between your script and mine. Serves me right for looking at code at 7:30am (pre-coffee). Glad it's finally working. Feel free to holler if it breaks.

Yeah, I know what you mean. I found myself up prior to 5 AM yesterday trying to figure all this out. That was pre-coffee too (and a mistake). ;)

I have used the script in several scenarios that I'd utilize it in and it does as desired and expected. I will use it, keep tabs on it and let you know if something strange evolves. I do feel it will work perfectly though.

I do appreciate what you've done, the help you've provided and the time you've put in. I'll be slicing up the script to figure out what's actually being done and why so I'll actually be learning from it.

I am going to mark this thread solved.

Thanks Again,
     Trapper

---

