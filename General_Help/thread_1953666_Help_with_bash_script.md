---
title: "Help with bash script"
date: 2012-04-06
forum: General Help
---

### Post by scar1 on 2012-04-06
Hi,

I have written a bash script to help me clear up rogue files please see below.

"#!/bin/bash
echo "This script will remove all sfv, nfo, nzb, srr & srs files from my home directory"
find /home/steve/Videos/ -name "*.sfv"
find /home/steve/Videos/ -name "*.nfo"
find /home/steve/Videos/ -name "*.nzb"
find /home/steve/Videos/ -name "*.srr"
find /home/steve/Videos/ -name "*.srs"
find /home/steve/Videos/ -name "*sample*"
echo "Debug list of files to delete"
read -p "Ok to continue? [Y/N]: " response
if [ $response = y ] ; then
find /home/steve/Videos/ -name "*.sfv" -exec rm -f {} \;
find /home/steve/Videos/ -name "*.nfo" -exec rm -f {} \;
find /home/steve/Videos/ -name "*.nzb" -exec rm -f {} \;
find /home/steve/Videos/ -name "*.srr" -exec rm -f {} \;
find /home/steve/Videos/ -name "*.srs" -exec rm -f {} \;
find /home/steve/Videos/ -name "*sample*" -exec rm -i {} \;
else [ $response =  n ] ; then
                echo "Terminating....."
fi"

Whilst the script will find the files I want to remove no problem it does not actually execute the second half which is to remove the files.

Can anyone offer any advise?

Thanks
Scar1

---

### Post by TeoBigusGeekus on 2012-04-06
If the filenames contain spaces in them, you have to enclose the brackets in parentheses, ie. "{}".

EDIT: Also, why don't you use logical operators with find?
```
find /home/steve/Videos/ \( -name "*.sfv" -or -name "*.nfo" -or -name ....etc. \)
```

EDIT2(Hopefully final): You don't have to use the -f (force) switch with rm.

---

### Post by Fwission on 2012-04-06
> **TeoBigusGeekus said:**
> If the filenames contain spaces in them, you have to enclose the brackets in parentheses, ie. "{}".

EDIT: Also, why don't you use logical operators with find?
```
find /home/steve/Videos/ \( -name "*.sfv" -or -name "*.nfo" -or -name ....etc. \)
```

EDIT2(Hopefully final): You don't have to use the -f (force) switch with rm.

I prefer to use ```
\[insert space or special character]
``` to simulate a space

---

### Post by TeoBigusGeekus on 2012-04-06
> **Fwission said:**
> I prefer to use ```
\[insert space or special character]
``` to simulate a space

Yeah, but how could he do this with find's brackets?

---

### Post by brainwash on 2012-04-06
[QUOTE=scar1]else [ $response =  n ] ; then[/QUOTE]

Replace else with elif.

---

### Post by matt_symes on 2012-04-06
Hi

Just to expand on Teo's excellent answer, here's a script i knocked up quickly.

```
matthew@matthew-Aspire-7540:~$ cat del_file_test.sh 
#!/bin/bash
echo "This script will remove all sfv, nfo, nzb, srr & srs files from my home directory"
find /home/matthew/Videos/ \( -name "*.sfv" -o -name "*.nfo" -o -name "*.nzb" -o -name "*.srr" -o -name "*.srs" -o -name "*sample*" \)
echo "Debug list of files to delete"
read -p "Ok to continue? [Y/N]: " response
if [ $response = y ]; 
then
find /home/matthew/Videos/ \( -name "*.sfv" -o -name "*.nfo" -o -name "*.nzb" -o -name "*.srr" -o -name "*.srs" -o -name "*sample*" \) -exec rm  "{}" \;
elif [ $response = n ]; 
then
echo "Terminating....."
fi
matthew@matthew-Aspire-7540:~$ 
```

Here's it in action.

```
matthew@matthew-Aspire-7540:~$ ls ~/Videos/
a.sfv  b.nfo  c.nzb  d.srr  e.srs  f.txt  g.ooc a b.nfo
matthew@matthew-Aspire-7540:~$ ./del_file_test.sh 
This script will remove all sfv, nfo, nzb, srr & srs files from my home directory
/home/matthew/Videos/c.nzb
/home/matthew/Videos/a.sfv
/home/matthew/Videos/b.nfo
/home/matthew/Videos/a b.nfo 
/home/matthew/Videos/e.srs
/home/matthew/Videos/d.srr
Debug list of files to delete
Ok to continue? [Y/N]: y
matthew@matthew-Aspire-7540:~$ ls ~/Videos/
f.txt  g.ooc
matthew@matthew-Aspire-7540:~$ 
```

Kind regards

---

### Post by TeoBigusGeekus on 2012-04-06
^^^ +1

EDIT (too many edits, I know...): Also, prefer double brackets [[ ]] for conditions in bash instead of single ones.

---

### Post by scar1 on 2012-04-07
Many thanks for all the quick replies, I will use them! Looks like me real issue here was understanding the "Find" command and utilising the best way for what I need it to do.

Thanks again....
Scar1

---

