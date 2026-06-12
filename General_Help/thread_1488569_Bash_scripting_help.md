---
title: "Bash scripting help"
date: 2010-05-20
forum: General Help
---

### Post by satish_j on 2010-05-20
Does the bash scripts in linux work like Functions in programming languages??
i mean do they accept input arguments??

---

### Post by WorMzy on 2010-05-20
Yes, $1 is the first argument, $2 is the second, etc.

---

### Post by satish_j on 2010-05-20
Can someone help me with a script which will take file-names(entire path) as the input arguments(may be 4 to 5 in number) and check whether those files are present or not??This check should be performed every n interval of time,which can be configured within script..
And if present,then run del command on those files....:confused::confused:

---

### Post by ba_saish on 2010-05-20
If you want to learn scripting this should help 
[http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)

---

### Post by satish_j on 2010-05-21
thanks for the links bro,but iam really not interested in learning it for just a single purpose...
I know just the basic things like the script can be written in common text files,renaming them *.sh,making them executables,....
But(no offence),i do not have time to learn the syntax of bash scripting...
Iam really expecting a ready-made script from the Linux Gods to achieve the same..;);)

---

### Post by Chesamo on 2010-05-21
You're expecting us to do the work for you? That's impudent if I've ever seen it.

```
#!/bin/sh
## This script is UNTESTED.
## Good luck.
##
## Use syntax:
## ./script.sh file1 file2 file3 file4 file5

rm $1 && rm $2 && rm $3 && rm $4 && rm $5
```
To run it every nth interval, put that command into the crontab. If the files don't exist, it doesn't matter. The command will execute anyway.

---

### Post by satish_j on 2010-05-21
Very much thanks for the code Chesamo,but my logic is somewhat diff..I want the script to work as follows:
1. check whether file 1 exists..if it does not exists,do nothing..
2. Keep checking after regular intervals..if file 1 is found,delete it.
3. Take now file 2 and check whether it exists....same proc as above..and so on..

And,i do know it is imprudent to expect the work from others,but it is basically a request..if possible,very good
I just learned from a blog that bash scripting in Linux is a really powerful utility and can automate many tasks..i would really love to learn it,but due to the time constraints,i cannot...

---

### Post by Timothytech on 2010-05-21
But his script does exactly that?? just skipping the if statements. Beggars cant be choosers. that file deletes files with the names you input or does nothing if they dont exist... you wouldnt be doing homework now would you? :P


also crontab works in intervals... daily weekly or monthly. 

I think adding 

```

5 12  * * *

```

 to the beginning of the string will make it daily... at 5:12am. Im most likely wrong on the syntax but dont underestimate the power of cron

---

### Post by satish_j on 2010-05-21
@Timothytech,
The script deletes all the files provided as arguments in a single go and not one by one..
Also,does crontab work in intervals of minutes???
what i want is:```

Step 1::
Does file1 exists??
If Yes-->delete it..Proceed to step 2
If No-->Wait for some interval(value of which will be stored in a variable).Afer that interval,go back to step1
Step 2::
Does file2 exists??
If Yes-->delete it..
If No-->Wait for some interval.Afer that interval,go back to step3
---
likeise
--Upto last file
```

---

### Post by Chesamo on 2010-05-21
There's no reason to check! rm will just exit if there's no file to delete.

---

### Post by satish_j on 2010-05-21
> **Chesamo said:**
> There's no reason to check! rm will just exit if there's no file to delete.

Okay,lets say i want to check the file size once it is found..if the size exceeds certain limit,then delete it,otherwise not..
Any ideas???
Also,can you tell me whether crontab runs in minutes intervals???

---

### Post by satish_j on 2010-05-26
No answers...i think that was quite complex...
Ok,I need to pass filepaths as parameters to the script..
any inputs for properly passing the same??Should they be single-quoted or not??

---

### Post by StuartN on 2010-05-26
> **satish_j said:**
> Okay,lets say i want to check the file size once it is found..if the size exceeds certain limit,then delete it,otherwise not..
Any ideas???
Also,can you tell me whether crontab runs in minutes intervals???

The smallest crontab interval is minutes, e.g. /5 in the first field would run every five minutes.

```
for file in "$@" ; do
  echo $file
  if [ -f "$file" ] ; then
    echo " exists"
    size=$(stat -c%s "$file")
    if [ $size -gt 1000000 ] ; then
      echo " big"
      rm "$file"
    fi
  fi
  sleep 1
done
```

For each command line argument (enclose any filenames that contain spaces in ""), first see if it exists, then retrieve the size in bytes and, if greater than 1 Mb, remove the file. Sleep for 1 second before testing next file.

---

### Post by satish_j on 2010-05-26
> **StuartN said:**
> The smallest crontab interval is minutes, e.g. /5 in the first field would run every five minutes.

```
for file in "$@" ; do
  echo $file
  if [ -f "$file" ] ; then
    echo " exists"
    size=$(stat -c%s "$file")
    if [ $size -gt 1000000 ] ; then
      echo " big"
      rm "$file"
    fi
  fi
  sleep 1
done
```

For each command line argument (enclose any filenames that contain spaces in ""), first see if it exists, then retrieve the size in bytes and, if greater than 1 Mb, remove the file. Sleep for 1 second before testing next file.

very thxx for the code frnd..
can i use -e instead of -f in:
```
 if [ -f "$file" ]
```
i have read the documentation..it says -f is for regular files,but i cannot understand the term 'regular':confused:

---

### Post by sfp100 on 2010-05-26
There are some options for conditions, for example
```
 if [ -z $1 ] then .... 
```should test if the file from first argument exist or not, but I'm not sure -- list of options you can get in bash tutorial or, for sure, in man (man bash), but it's quite long reading....
For waiting some time is command ```
sleep
```, refer to man for details: ```
man sleep
```I think that script you need is quite simple -- for me about 1-2 hour of writing, testing, etc., shorter if ones write Bash scripts mere frequently than once by month. 

Good lack!

---

### Post by dino99 on 2010-05-26
[http://manpages.ubuntu.com/manpages/lucid/en/man5/crontab.5.html](http://manpages.ubuntu.com/manpages/lucid/en/man5/crontab.5.html)

---

### Post by StuartN on 2010-05-26
> **satish_j said:**
> can i use -e instead of -f

-f will test if $file exists and is a regular file, i.e. not a directory, link, etc. I assume you want regular files because you want to check the size and delete large ones.

Use -e if you handle file being a directory, because rm directory will often fail.

---

### Post by satish_j on 2010-05-26
> **StuartN said:**
> -f will test if $file exists and is a regular file, i.e. not a directory, link, etc. I assume you want regular files because you want to check the size and delete large ones.

Use -e if you handle file being a directory, because rm directory will often fail.

Hmm,Ok...thanks  a lot for your time..:)

---

### Post by satish_j on 2010-06-04
Consider the foll code:
```

   for file in "$@" ; do
     while true
      do
        if [ -f $file ]; then
         --do something;--
         break;
        else 
         sleep 60;
        fi
      done
   done

```
Just wanted to know whether the 'while' loop will keep on iterating until the file is found...
i.e I will pass the absolute pathnames as arguments to the script while calling..Path1(Arg1) is taken first and checked whether file exists or not..if not,wait for 60sec..once path1 exists,it will do some activity and exit from while loop.
Then,Path2(Arg2) will be taken and worked upon as above..
Just wanted to know whether the script will work as above or Not????

---

### Post by StuartN on 2010-06-04
> **satish_j said:**
> Just wanted to know whether the script will work as above or Not????

Did you try running it? That would be far preferable to asking here (so long as --do something-- is not dangerous).

---

### Post by ThesaurusRex on 2010-06-04
> **satish_j said:**
> Consider the foll code:
```

   for file in "$@" ; do
     while true
      do
        if [ -f $file ]; then
         --do something;--
         break;
        else 
         sleep 60;
        fi
      done
   done

```
Just wanted to know whether the 'while' loop will keep on iterating until the file is found...
i.e I will pass the absolute pathnames as arguments to the script while calling..Path1(Arg1) is taken first and checked whether file exists or not..if not,wait for 60sec..once path1 exists,it will do some activity and exit from while loop.
Then,Path2(Arg2) will be taken and worked upon as above..
Just wanted to know whether the script will work as above or Not????

Theoretically, yes, although I don't really see the need for such a script. Your inner while loop will run forever if that file is never created.

---

### Post by satish_j on 2010-06-05
> **StuartN said:**
> Did you try running it? That would be far preferable to asking here (so long as --do something-- is not dangerous).

You are right..i should have directly tested it..
Okay,it is givng foll err:
```

/home/satish/Desktop/Testing2.sh: 12: --do: not found
/home/satish/Desktop/Testing2.sh: 12: --: not found

```
:confused:

---

### Post by Leppie on 2010-06-05
you would have to replace "--do something--" with the command you want your script to execute.
in your case something like: rm $file
have you tried [StuartN]("http://ubuntuforums.org/member.php?u=808325")'s script?

---

### Post by satish_j on 2010-06-06
> **Leppie said:**
> you would have to replace "--do something--" with the command you want your script to execute.
in your case something like: rm $file
have you tried [StuartN]("http://ubuntuforums.org/member.php?u=808325")'s script?

oops...what a silly mistake by me...i should have commented that line...thanks anyway frnd...

---

### Post by BoneKracker on 2010-06-06
Here is another version of essentially the same script, which demonstrates a function (which I think you asked about earlier):

```
#! /bin/bash

function handle {
    while true; do
        [[ -f $1 ]] && echo "Handled file ${file}!" && break || sleep 60
    done
}

for file in $@; do
    handle $file
done
```

The function must come before the code that calls it, which is why the main loop is at the bottom.  Note that "$1" in the function means "first argument passed to the _function_" and not "first argument passed to the script".

The {} brackets around the variable $file are a good idea sometimes to prevent the interpreter from thinking a character adjacent the variable is part of it (in this case, the "!", which is just part of the output text surrounding the file name).  In reality the interpreter is actually smarter than that, but it's good for code portability and readability.

Also, while they are probably something to stay away from because they can actually make code more difficult to read, you were already exposed to "command lists" earlier.

Above:
```
[[ -f $1 ]] && echo "Handled file $file" && break || sleep 60
```
... is effectively equivalent to:
```
if [ -f $1 ]; then
    echo "Handled file ${file}!"
    break
else
    sleep 60
fi
```

Since your "do something" is probably more complex than 'echo "Handled file $file", you probably wouldn't want to compress all that stuff into one line.  Don't make your code hard to read.  Still, it's an interesting feature of BASH and occasionally useful. :)

---

### Post by satish_j on 2010-06-07
> **BoneKracker said:**
> Here is another version of essentially the same script, which demonstrates a function (which I think you asked about earlier):

```
#! /bin/bash

function handle {
    while true; do
        [[ -f $1 ]] && echo "Handled file ${file}!" && break || sleep 60
    done
}

for file in $@; do
    handle $file
done
```

That's the object oriented approach of the functionality i wanted..
Thanks very much..
I have tested this script and it works upto my expectations...
:guitar:..woohoooo

---

### Post by satish_j on 2010-06-11
Iam trying to get the arguments passed to bash script along with a variable:
```

count=$#
const="/home/satish/"
for ((i=1;i<=count;i++)); do
  echo $const$i
 done

```
If i call this script --(/Testing.sh 'BackUpFiles.rar')
It shows /home/satish/1 as output..
i.e it does not take the name of argument passed to it in $i variable
:confused:

---

### Post by BoneKracker on 2010-06-11
> **satish_j said:**
> Iam trying to get the arguments passed to bash script along with a variable:
```

count=$#
const="/home/satish/"
for ((i=1;i<=count;i++)); do
  echo $const$i
 done

```
If i call this script --(/Testing.sh 'BackUpFiles.rar')
It shows /home/satish/1 as output..
i.e it does not take the name of argument passed to it in $i variable
:confused:

You are overlooking a degree of indirection.

At that point, i=1, so $i is expanded to 1, yes?  Therefore $const$i is "/home/satish/1".  This is not rocket science. :p

If you want the value of $1 (as opposed to the value of $i) you need to dereference that additional degree of indirection.  Refer to the BASH man page.  Search for "indirection" (you can search by pressing the / key and typing indirection then pressing Enter, then pressing / and Enter repeatedly until you reach what you are looking for.

I believe what you want here instead is this:
```

count=$#
const="/home/satish/"
for ((i=1;i<=count;i++)); do
  echo $const$!i
 done

```

**Note the exclamation point.  Resist the urge to try this, and read the man page first, though**, so you understand what's going on.  If you are a C/C++ programmer, you might think of this as being akin to dereferencing a pointer to a pointer ($i is a pointer to $1 which is a pointer to the literal argument assigned on the command line to parameter 1).

This is a feature of BASH I personally like but I almost never see anyone use.  I have not tested this, so I may have introduced a syntax error (i.e., maybe you have to use echo ${const}${!i}).

---

### Post by StuartN on 2010-06-11
> **BoneKracker said:**
> **Note the exclamation point.  Resist the urge to try this, and read the man page first, though**

I agree absolutely - I would eliminate indirection and step through the list:

```
const="/home/satish/"
for file in "$@" ; do
  echo $const$file
done
```

---

### Post by BoneKracker on 2010-06-11
> **StuartN said:**
> I agree absolutely - I would eliminate indirection and step through the list:

```
const="/home/satish/"
for file in "$@" ; do
  echo $const$file
done
```

Good call, Stuart.

Indirection is kind of "nifty", but it makes code really hard to read (most people aren't even aware of that feature), and there's almost always a simpler way to do things.

I think I've only used it once, in a case where it would have increased the length of a script by about 50% not to use it.

---

### Post by satish_j on 2010-06-12
Thanks Stuart and BoneKracker for your time..
Iam learning new things daily and Iam enjoying BASH SCRIPTING..:p

---

### Post by BoneKracker on 2010-06-12
You're welcome.  Good luck.  Mark the thread "solved" if you haven't done so (in thread tools).

---

