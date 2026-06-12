---
title: "Bash -- open mlocate search results"
date: 2011-03-22
forum: General Help
---

### Post by kmcbest on 2011-03-22
Hi all,

Upon a while of searching, I think I failed to find the correct terms and I'm posting here.

I often use mlocate to search for files. For example, if I say
```
$ mlocate temp_2.pdf
```I'll get two results:
```
/home/kmc/Documents/latex/temp_2.pdf
/home/kmc/Documents/latex/test/temp_2.pdf

```Now if I want to open one of them, I'll have to either open Acroread and browse to their locations. Or select and copy, and call acroread in terminal like
```
$ acroread /home/kmc/Documents/latex/temp_2.pdf
```This is tedious to me. I'm thinking of a way of quickly open its search results, I've tried **pipe**s like this but it doesn't work:
```
$ mlocate temp_2.pdf | acroread
```maybe it doesn't work this way.

So what does the trick? *What's the name of this trick*? I've googled for
> Linux bash catch output, pipe output, open mlocate resultsAnd *is it possible to handle multiple lines of output*, e.g., can I choose which line of output get forwarded to relative programs?

**Thanks.**

---

### Post by DaithiF on 2011-03-22
use xargs:
```
mlocate -0 temp_2.pdf | xargs -0 acroread
```

(this will open all search results)

---

### Post by kmcbest on 2011-03-22
OK that works. Thanks. 

And is there a way to selectively open results when the list is long?

---

### Post by DaithiF on 2011-03-22
> **kmcbest said:**
> And is there a way to selectively open results when the list is long?

for that you'd need to write a script ... something like this maybe: (uses dialog for creating the menu of results ... sudo apt-get install dialog) 

```
#!/bin/bash

t=$(mktemp)
locate "$1" | cat -n > $t

[[ -s $t ]] || { echo "No results found"; exit; }

response=$(dialog --stdout --menu 'Choose a File:' 20 70 15 --file $t)

if [[ -n "$response" ]]; then
    file=$(sed -n "/^\s*$response\t/{s/^.*\t//;p}" $t)
    if [[ -n $file ]]; then 
        echo "You chose $file"
        acroread "$file" &
    fi
fi
```

---

### Post by kmcbest on 2011-03-22
That's cool and easy to use, thanks!

There's one minor thing: if there's only one result, this will give an error

Error: Expected 2 arguments, found only 1.
Use --help to list options.

---

### Post by DaithiF on 2011-03-22
thats not an issue with 1 result, its an issue with spaces in filenames.  For 1 result there should be no need to pop up a choice of course.  And hard-coding to acroread limits the usefullness quite a lot, so heres a version should addresses those various issues:

```
#!/bin/bash

t=$(mktemp)
locate "$1" | awk '{ printf "%4d\t\"%s\"\n",  NR, $0 }' > $t

[[ -s $t ]] || { echo "No results found"; exit; }

rows=$(wc -l "$t" | cut -d' ' -f1)

if [[ $rows == 1 ]]; then 
     file=$(sed 's/^.*\t"\(.*\)"$/\1/' $t)
    xdg-open "$file" &
else
    response=$(dialog --stdout --menu 'Choose a File:' 20 70 15 --file $t)
    if [[ -n "$response" ]]; then
        file=$(sed -n "/^\s*$response\t/{s/^.*\t\"\(.*\)\"$/\1/;p}" $t)
        if [[ -n $file ]]; then 
            echo "You chose $file"
            xdg-open "$file" &
        fi
    fi
fi

```

---

### Post by kmcbest on 2011-03-22
You're right. Now everything can be found and opened by default program.

Can "dialog" wrap the long lines? I've tried changing 70 to 200 but still some well-buried files can't be displayed in one line.

Thanks!

---

### Post by DaithiF on 2011-03-22
> **kmcbest said:**
> 
Can "dialog" wrap the long lines? I've tried changing 70 to 200 but still some well-buried files can't be displayed in one line.

no, but if you increase the width of your terminal dialog will use whatever is available (up to the width you specify).

---

### Post by kmcbest on 2011-03-22
I tested with single result and seemly the script halts at this line
```
if [[ $rows == 1 ]]; then 
    xdg-open "$file" &

```
because $file is not yet defined, I've tried $t but it doesn't work

---

### Post by DaithiF on 2011-03-22
> **kmcbest said:**
> I tested with single result and seemly the script halts at this line
```
if [[ $rows == 1 ]]; then 
    xdg-open "$file" &

```because $file is not yet defined, I've tried $t but it doesn't work

yes, that was the reason for my edit of the earlier post -- see the updated version.

---

### Post by kmcbest on 2011-03-22
Now works like a charm! Have a nice day DaithiF.

---

### Post by LtPitt on 2011-10-14
This is AWESOME.

This should be sticky and you all should be saints.

---

### Post by LtPitt on 2011-10-15
How it could be possible to realize a gui for this great script and use it in gnome?

---

### Post by paramvir on 2011-12-11
Ok - here is a zenity front end for locate - let me know what you think.

No issues re single search result and the search result is persistent if u want to check multiple files - click cancel when done.

```


#!/bin/bash

zen_ti="zenity --text-info --height=500 --width=550"

search_ui_msg="Enter the search text. \n\nHelp: Type -help below to learn the possible syntax. \n         Type -updatedb to update search database. \n         Type -man to view locate man page. \n"



helper ()
{
msg="This is a graphical frontend for mlocate locate program, something like  Zenity for locate. 

Primary idea from DaithiF on Ubuntuforums.

Look at the man page for locate - some features do not work here but the default behavior *searchword* works - also *someword*.odt will show you all the odt files - so it is quite versatile.  

Normally the update database command updatedb is a cron job handled by the system daily - but since locate will only show you data since the last data update you will not find results of recent nature - so do an updatedb - it will ask for your password as it is a admin (root) command.

If no results are found the search box returns !

I hope that it will be useful! 

plikhari gmail dot com - comments n suggestion r welcome

cheers 
paramvir [ 2011 ]
"
    echo -n "$msg" | $zen_ti  \
    --title="How to use this search program..." ;
}


t=$(mktemp)

lookup1()
{
    lookn1=$(zenity --title="Search with locate" --height=100 --width=500 --entry --text="$search_ui_msg" --entry-text="")
    
    if  [ $? != 0 ]; then
        exit 1
    fi
    
    if [ $lookn1 = "-help" ] ; then
        helper;
        lookup1;
    elif [ $lookn1 = "-updatedb" ] ; then
        xterm -e "sudo updatedb";
        lookup1;
    elif [ $lookn1 = "-man" ] ; then
        man locate | $zen_ti  \
            --title="Locate man page..." ;
        lookup1;
    else
        locate -i "$lookn1" | awk '{ printf "%4d\t\"%s\"\n",  NR, $0 }' > $t
        [[ -s $t ]] || { echo "No results found"; lookup1; }
        rows=$(wc -l "$t" | cut -d' ' -f1)
    fi
}


main() {


while $i ;
do 
    response=$( cat "$t" | zenity --title="Total results found: $rows     " --list --height=700 --width=800 --column="To view - Select a file and click on OK or press enter key.   $rows results found" )
    
    if  [ $? != 0 ]; then
            lookup1
            main
    elif [[ -n "$response" ]]; then
        echo response1 = "$response"
        ORG_IFS=$IFS
        IFS=$'\n'
        seen1=( $(echo "$response" | awk '{for(i=2;i<=NF;i++){printf $i " "}}' ));
        # remove " character from all over and spaces tabs start n end
        seen2=( $(echo "$seen1" | sed -e 's/\"//g' -e 's/^[ \t]*//' -e 's/[ \t]*$//'));
        if [[ -n "$seen2" ]]; then 
            xdg-open $seen2 ;
        fi

    fi

IFS=$ORG_IFS

done
}

lookup1
main




```

---

