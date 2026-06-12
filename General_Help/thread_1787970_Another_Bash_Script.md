---
title: "Another Bash Script"
date: 2011-06-21
forum: General Help
---

### Post by OldManRiver on 2011-06-21
All,

Still have not solve my mount issues for the thread at:

[http://ubuntuforums.org/showthread.php?t=1757014](http://ubuntuforums.org/showthread.php?t=1757014)

but have another more pressing problem right now.  Have a client with a huge web implementation, of over 5,000 web pages, due to bad advice on SEO, but have to search these files for specific strings.  To add to the problem the ISP has not and will not install the "locate" fuction on their server, so having to use the "find" command to get the job done.

Anyway have to use find to catalog the files, then use cat with grep to find the string, I'm looking for.  Here is where I'm at with my code:
**Calling Script:**
```
#! /bin/bash



bash str-search.sh /home/mypath "php*, htm*, tpl" $hostname

```
and the code it is calling is:
```
#! /bin/bash



vpath=$1;   # Get the file path to process

vfext=$2;   # Get the file extension(s) to process

vtext=$3;   # Get the string to find in the files



echo "P==> $vpath";

echo "E==> $vfext";

echo "T==> $vtext";


# Go to the path/directory

   if [ -z "$vpath" ]            # Is parameter #1 zero length?

   then

     cd /home/my_def_path;

   else

     cd $vpath;

   fi


# Parse the ext var as array

fargs = explode($vfext);



for file in `find $vpath/. -name "*.php*"`

do

    result=`grep $vtext $file`;

    if [[ $? -eq 0 ]]

    then

        echo $file $result $linenum;

    fi

done



for file in `find $vpath/. -name "*.htm*"`

do

    result=`grep $findstr $file`;

    if [[ $? -eq 0 ]]

    then

        echo $file $result $linenum;

    fi

done



for file in `find $vpath/. -name "*.tpl*"`

do

    result=`grep $findstr $file`;

    if [[ $? -eq 0 ]]

    then

        echo $file $result $linenum;

    fi

done


filecontent=( `cat "logfile" `)



for t in "${filecontent[@]}"

do

echo $t

done




```
I have not dome any array processing in BASH before so at line 20 of this code I need to know the way to process the EXT var/array to allow for a loop instead of the separate hard coded calls I have now for the EXTs.

Would appreciate all help!

Thanks!

OMR

---

### Post by OldManRiver on 2011-06-22
All,

My latest code promises some improvement:```
#! /bin/bash



vpath=$1;   # Get the file path to process

vfext=$2;   # Get the file extension(s) to process

vtext=$3;   # Get the string to find in the files



echo "P==> $vpath";

echo "E==> $vfext";

echo "T==> $vtext";


# Go to the path/directory

   if [ -z "$vpath" ]            # Is parameter #1 zero length?

   then

     cd /home/my-def-path;

   else

     cd $vpath;

   fi


# Parse the ext var as array

nargs = ${vfext[@]};


for (( i=0; i<${nargs}; i++ ));
   do
      arelm = ${vfext[$i]};
      for file in `find $vpath/. -name "*.$arelm*"`

         do

            result=`grep $vtext $file`;

            if [[ $result -eq 0 ]]

               then

               echo $file $result $linenum;

            fi

         done

   done



filecontent=( `cat "logfile" `)



for t in "${filecontent[@]}"

do

echo $t

done




```
Just got to figure out where my "cat" statements go and how to pipe it to the output file.

Thanks!

OMR

---

### Post by weblordpepe on 2011-06-22
Hi dude. Could you please clarify what the task is you want to do?
From what I understand you want to know the line number and contents of every line which matches '.htm' and other file contents, and show you the file which includes that match?

This is what fgrep is for :) Let me check to see if I can do a similar thing hold on.

---

### Post by weblordpepe on 2011-06-22
Outputting to a file is straightforward. Just do a > 

```
echo $file $result $linenum > ./outputfile.txt
```



```
frep -nr derp /home/pants/Documents/path/*
```

This will search for the string **derp** in all the files matching **/home/pants/Documents/path/***

The output will be separated by colons. Im not sure how to make it separate by tabs instead.
**-n** makes fgrep give you line numbers, and **-r **makes it recursive, to eat through the subdirectories too.

Theres options to make it process binary files too. check out the man page for fgrep if ya interested


```
man fgrep
```

Hail the power of linux! :)

---

### Post by OldManRiver on 2011-06-28
> **weblordpepe said:**
> Hi dude. Could you please clarify what the task is you want to do?
From what I understand you want to know the line number and contents of every line which matches '.htm' and other file contents, and show you the file which includes that match?

This is what fgrep is for :) Let me check to see if I can do a similar thing hold on.

weblordpepe,

Actually no I want to find a string, let's say for example the variable $hostname inside all files on a web site with over 150,000 files.  I want to find this string in all files with extensions of .php*, .htm*, .tpl* or any other list of extensions.  I have to make mods, where I find this so need a file generated that contains?  path, file, linenumber and line, so I can see if I need to mod the line and where to find it to quickly make the edit.

This is on a shared host box so the find /. does not work as that would take me to root and not my web page root, so have to have the actual path name in the search to keep it localized, so path might be: /home/content/a/b/c/myuid/html/htdocs and search has to start there and recurse through all subdirectories.

Does this help?

Thanks!

OMR

---

### Post by OldManRiver on 2011-08-23
All,

Guess I scared everybody off with this one, but should be doable.

OMR

---

### Post by sisco311 on 2011-08-23
```
find /path/to/dir \( -iname '*.html' -o -iname '*.php' \) -exec grep -Hn -e 'text' '{}' \+
```

will output something like:
```
/path/to/dir/path/to/file1:line number:matched line
/path/to/dir/path/to/file2:22:foo
/path/to/dir/path/to/file3:42:Answer to the Ultimate Question of Life, the Universe, and Everything
```

you can redirect the output to a file:
```
find /path/to/dir \( -iname '*.html' -o -iname '*.php' \) -exec grep -Hn -e 'text' '{}' \+ > filename
```

If you want to process the file, you can try something like:
```
while IFS=: read -r file line text
do
    echo "file name: $file"
    echo "line number: $line"
    echo "text: $text"
done < filename
```

---

### Post by ofnuts on 2011-08-23
> **OldManRiver said:**
> weblordpepe,

Actually no I want to find a string, let's say for example the variable $hostname inside all files on a web site with over 150,000 files.  I want to find this string in all files with extensions of .php*, .htm*, .tpl* or any other list of extensions.  I have to make mods, where I find this so need a file generated that contains?  path, file, linenumber and line, so I can see if I need to mod the line and where to find it to quickly make the edit.

This is on a shared host box so the find /. does not work as that would take me to root and not my web page root, so have to have the actual path name in the search to keep it localized, so path might be: /home/content/a/b/c/myuid/html/htdocs and search has to start there and recurse through all subdirectories.

Does this help?

Thanks!

OMRI don't see you looking at several thousand files afterwards to see if a change should be made or not. IMHO the only reasonable way to handle this is to express the conditions for a change as regular expressions and feed that to find+sed which would only process the files where this is relevant.

[http://xkcd.com/208/](http://xkcd.com/208/)

---

### Post by OldManRiver on 2011-08-27
All,

Thanks for the inputs!  Messing around with the code submitted by sisco311 and weblordpepe.  

ofnuts,

As for you comment, this should never produce more than 100 files, even though we have 150K+ files, but these should be items we are searching for in the function libraries, not the user interface files.

Let you all know where I get on this.  We migrated all the code to a single server, so at least now it is centralized.

Thanks!

OMR

---

### Post by OldManRiver on 2011-09-28
All,

Put together this quick scipt:
```
#! /bin/bash

dir=$1;
fnm=$2;
tgt=$3;
ext=$4;
rep=$5;
# Need to explode $ext to gen line following
fln="-iname '*.htm*' -o -iname '*.php*' -iname '*.tpl*'";
find "$dir" \( "$fln" \) -exec grep -Hn -e "$tgt" '{}' \+ > "$fnm";

while IFS=: read -r file line text
do
    echo "file name: $file line number: $line text: $text";
    # Replace the target ($tgt) in line with correct value ($rep)
done < "$fnm"

```

Hope now all understand the intent, and the 2 line in the code with "#" still need to be coded out per these notes.

Thanks!

OMR

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #23 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

### Post by greenpeace on 2012-06-08
Hi, 

Does the hosting company's server have sed?

Here's the basics of what you need to do in a one liner with **find** and **sed**:

```
find . \( -type f -iname *.html -o -iname *.php -o -iname *.py \) -exec sed -i 's/search_string/new_string/g' '{}' \+
```

you can replace .html, .php and .py as best suits your situation.

the -i flag on sed will make it do the substitution in-place.

**search_string** is what you're looking for
**new_string** is what you want to put there

You can also add a suffix to be used in making backups... have a look at the -i option in the man pages for sed 

I tested this on my box, and it seemed to work ok... but I would really recommend that you test on a copy of the files first to make sure it works as you need.

you can check effectiveness afterwards using grep (with a -R flag to recurse)

If you set a suffix to use in making backups of the files, then you can use find again to identify the changed files.

hope that helps!

---

