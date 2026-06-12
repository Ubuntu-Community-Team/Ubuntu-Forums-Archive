---
title: "Scripting Help - Grabbing Variables from Output"
date: 2011-06-09
forum: General Help
---

### Post by Kissell on 2011-06-09
I want to be able to grab some text from a directory listing in a bash script, and then apply that text to future commands in the same script.  

For instance, say I do "ls -lais /media/Movies" and get:
> 
2147560409   712544 -rwxr-x---  1 root users   729645056 1999-03-07 11:45 Young Guns (1987).avi
2147560410   712400 -rwxr-x---  1 root users   729497600 2002-01-09 01:11 Young Guns II (1990).avi


Then say I want to grab the year from this output and then use that information as part of the command to modify the file timestamp, such as:
> 
touch "Young Guns (1987).avi" -t 198701011200
touch "Young Guns II (1990).avi" -t 199001011200


So that the result of ls -lais is:
> 
2147560409   712544 -rwxr-x---  1 root users   729645056 1987-01-01 12:00 Young Guns (1987).avi
2147560410   712400 -rwxr-x---  1 root users   729497600 1990-01-01 12:00 Young Guns II (1990).avi


Anyway, that's just one example, but I often find myself needing to do this type of thing, and I'm sure its possible, just not really done enough scripting recently to know how to do it without some help.  TIA

NOTE: Yes, I changed Young Guns to be released in '87, it is an '88 movie, but when I type "eight right-parenthasis" it does this: 8)

---

### Post by sisco311 on 2011-06-09
In bash you can use [parameter expansion]("http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion").

Something like:
```

shopt -s nullglob
cd  path/to/dir

for file in *.avi
do
  # remove the characters before ( including (
  year="${file#*\(}"
  # remove the characters after ) including )
  year="${year%\)*}"
  # if the result is a valid number then run touch
  if ! [[ $year = *[!0-9]* ]]
  then
    touch "$file" -t "${year}01011200"
  fi
done

```

> **Kissell said:**
> 
Anyway, that's just one example, but I often find myself needing to do this type of thing, and I'm sure its possible, just not really done enough scripting recently to know how to do it without some help.  TIA


Check out this guide: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
alongside with the BashFAQ and BashPitfalls on the same page.

> **Kissell said:**
> 
NOTE: Yes, I changed Young Guns to be released in '87, it is an '88 movie, but when I type "eight right-parenthasis" it does this: 8)

:)

Use the [noparse]```
8)
```[/noparse] or [noparse][noparse]8)[/noparse][/noparse] tags. See: [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

;)

---

### Post by Kissell on 2011-06-09
Thanks, that worked great.  Now I just need to read up on what all those commands and syntax do, so I can write my own similar scripts in the future, but it does work really well.

---

### Post by sisco311 on 2011-06-09
> **Kissell said:**
> Thanks, that worked great.


You're welcome!

> **Kissell said:**
> 
Now I just need to read up on what all those commands and syntax do, so I can write my own similar scripts in the future, but it does work really well.

If you need any future help feel free ask.

---

### Post by Kissell on 2011-06-09
In this example, we just took the year from the filename...  it would be nice to actually pull the release date from imdb.com and modify the day and month as well.  

Unfortunatly I couldn't find a script already setup to do that, and I briefly looked at the imdb-tools package in the repository, but it doesn't appear to work very well, at least with the repository version for Maverick.

---

### Post by sisco311 on 2011-06-09
> **Kissell said:**
> In this example, we just took the year from the filename...  it would be nice to actually pull the release date from imdb.com and modify the day and month as well.  


Sounds interesting, but I think you should start a new thread for this.

---

