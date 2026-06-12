---
title: "Reading a unformatted text file in Ubuntu"
date: 2010-04-22
forum: General Help
---

### Post by nandugopan on 2010-04-22
Guys, I dont know where else to post this, thats why I am posting this here.

I am using Karmic and I have a unformayted dump file that needs to be analysed. Very specifically the fourth column of the unformatted dump file needs to be read and stored in a new file if the value is greater than a particular value. My friend wrote me a bash script for this but I just cant seem to get the bash script to work.I think its because bash does not recognise floating point logic. I want this comparison repeated for the thousands of files that are there in the folder.Could anyone help me out with this?:confused:

the shell script:
#!/bin/bash
cd "/media/FE207E65207E2535/check"
c=0
for i in `ls out*.*${1}`
do
    fname[$c]=$i
    echo "Filename =${fname[$c]} "
    c=`expr $c + 1`
done

j=0

while [ $j != $c ]; do
    cc=0

    while read line
    do
        temp=$line

        temp2=`echo "$temp" |awk '{ print $5 }'`


        if test "$temp2" = "" ; then
            something=nothing
        else
            if test "$temp2">"1.000005"; 
 then
                linehere[$cc]=$temp2
                echo "${linehere[$cc]}">>Filen$j.xls
                cc=`expr $ccj + 1`
            fi
        fi
    done   
    
done < ${fname[$j]}
j=`expr $j + 1`

sample lines from unformatted dump:

150 -0.0150504 -0.0644572 0.00718489 0.0665798 
670 -0.147198 -0.0512124 0.0742086 0.172617 
684 -0.119705 -0.0616156 -0.131713 0.188346 
152 0.013734 0.067267 0.113046 0.13226 
650 -0.0882756 0.119042 0.0522627 0.157146

---

### Post by Portmanteaufu on 2010-04-22
In the time it would've taken me to read the bash script, I wrote a perl one to the same. :D

```

#!/usr/bin/perl
while(my $line = <STDIN>)
{
   my @cols = split /\s+/, $line;
   if($cols[3] > $ARGV[0])
   {
       print("$cols[3]\n");
   }
}

```

Usage: 
```

cat somefile | scriptname [some number] > output.txt

```
It'll dump any fourth column value greater than "some number" and put the results in output.txt.

Hope that helps, feel free to ask questions.

---

### Post by nandugopan on 2010-04-23
Dear Portmanteaufu,

AMAAAAAAAAAAZING...=D>

Thanks a million..That works like a charm!!!And I feel like a dinosaur :)
But can this be done for a series of files? I got 1000 or so files to analyse. I am sure there must be a better way of doing it than calling the perl script from a bash loop...:P

---

### Post by Portmanteaufu on 2010-04-23
> **nandugopan said:**
> 
But can this be done for a series of files? I got 1000 or so files to analyse. I am sure there must be a better way of doing it than calling the perl script from a bash loop...:P


Hah, actually, that's probably exactly what I would do. :) How exactly do you want to hand it the files, though, and where do you want the files to be output?

For the sake of expediency, I'll assume that you have a tree structure full of files, and that you only care about files with a certain file extension (I'll use ".txt" as my example file extension.) Every file will have its output be in the same directory and be called out.<ORIGINAL NAME>.txt.

```

#!/bin/bash
find . -type f -name '*.txt' -print0 | while read -d $'\0' file
do
  cat $file | scriptname [some number] > out.$file
done

```

I don't know how familiar you are with bash, so if you need some other approach and don't know how to do it just say the word. Enjoy!

---

### Post by nandugopan on 2010-04-24
Dear Portmanteaufu,

You have done it again....Yes the issue is solved.And that too far more neatly than I ever expected. Thank you!!
5 STARS :KS:KS:KS:KS:KS


Well my knowledge of bash is minimal. I mostly try to learn from online bash tutorials and try to put together something that works.Could you suggest some good guide to scripting (perl and bash)?

Partially related to this I have another issue (due to a messup on my part)

 I have  1000 unformatted text files. I need to sort them all based on a value (say, in column 1) and then subtract the values of another column (say, column 3) of each of these files from a standard reference file that has also been sorted (based on column 1).

Any suggestions how to go about this. Spreadsheet does not seem to be an option.:P

---

