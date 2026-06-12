---
title: "tar compression via terminal"
date: 2012-07-06
forum: General Help
---

### Post by mijonuha on 2012-07-06
Hi
I tried to write down a scrip in 
**~/.gnome2/nautilus-scripts**
in order to get a compressed back-up from selected file(s).
now it is on my nerve.
first of all using "${$parameterNumber}" did not work for me and I was obliged to use **shift** instead.
when the file name has space inside, the problem arises due to wrong interpretation of the parameters and  files included space will be ignored. by putting file names inside the quotation, **tar** command will have the problem.
What should I do?
```
#! /bin/bash

DestinationFolder="/media/Media/Copy"

Source="$1"
SourceAll=""
while [ $# -ne 0 ]
do
    arg="${1}"
    SourceAll="$SourceAll $arg";
    shift
done;
DPart=`date +"_%m-%d-%y-%H;%M;%S"`
Basename=`basename $Source`
extention='tar.bz2'
Destination=$DestinationFolder"/"$Basename"$DPart."$extention
tar -jcvPf $Destination $SourceAll
zenity --info --text="tar -jcvPf $Destination $SourceAll"
```note: Source is name of the first argument used for making output file name. while SourceAll includes all arguments' names.

with quotes:
```
     SourceAll="$SourceAll '$arg'";

```and even what if in case destination also includes space?

the interesting part is that by copy past the command in terminal it works but not with the nautius script.

---

