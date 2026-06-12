---
title: "Command Line help: Find and Replace text within multiple files?"
date: 2010-08-28
forum: General Help
---

### Post by Razmear on 2010-08-28
I'm pretty sure this is doable from the command line, but my CLI skills have degraded a lot since my pre-Y2K admin days.

The goal is to search all the files in the directory for a very long string of text and replace it with another string of text. The text being searched for is my Google Adsense code (which will be stripped from my website) and it will be replaced with a placeholder so I can easily tack something else in there in the future. Seeing how I have that long snip of code on about 100 pages, automating the process would make life easier. 

If I was searching for a single word, I can see ways to do this. 
If I paste the code I'm searching for into a text file, is there a way to:
find (contents of oldstring.txt) and replace with (contents of newstring.txt)? 

Thanks, and sorry being less clear than possible,
eb

---

### Post by yabbadabbadont on 2010-08-28
You could use grep with the option to only return matching file names, then take that output and use it with sed and tee to replace the text and save the modified files with new names.

(the exact details are left as an exercise for the student... ;))

---

### Post by minigeek on 2010-08-28
> **Razmear said:**
> I'm pretty sure this is doable from the command line, but my CLI skills have degraded a lot since my pre-Y2K admin days.

The goal is to search all the files in the directory for a very long string of text and replace it with another string of text. The text being searched for is my Google Adsense code (which will be stripped from my website) and it will be replaced with a placeholder so I can easily tack something else in there in the future. Seeing how I have that long snip of code on about 100 pages, automating the process would make life easier. 

If I was searching for a single word, I can see ways to do this. 
If I paste the code I'm searching for into a text file, is there a way to:
find (contents of oldstring.txt) and replace with (contents of newstring.txt)? 

Thanks, and sorry being less clear than possible,
eb

Hi 

This my help

[http://www.liamdelahunty.com/tips/linux_search_and_replace_multiple_files.php](http://www.liamdelahunty.com/tips/linux_search_and_replace_multiple_files.php)
:D

---

### Post by Razmear on 2010-08-28
Thanks Yabba and mini ;)

I found the link that mini referred to, it was the first result in my fruitless search. The problem with the example there is placing, and properly escaping, the adsense code into that neat little string. 

yabba, all the files are in the same directory, easy to locate and isolate. 
At least I have a new command: tee to check the man page on and see if I can figure this out. This is super low priority, so I don't mind having to scrounge a bit for the solution, but if anyone wants to slip this student the answer under the table I won't complain either. 

eb

edit: 
RTFM: [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

### Post by d3v1150m471c on 2010-08-29
you can just do this with sed and pipe it into a file with > newfile.txt
```

d3v11@laptop:~$ echo "well, something for nothing, $LOGNAME" | sed 's/something for nothing/whoa/'
well, whoa, d3v11
d3v11@laptop:~$ 

```if you want to do this to all the files in the directory just use a for-loop:
```

for x in *; do
cd /to/the/directory
sed 's/your old text/your new text/' $x > "$x"new
done

```

---

### Post by Razmear on 2010-08-29
Thanks for the info dv3, 
The 'for-loop' method looks promising. 
Can the /your old text/ section somehow call a text file the contains what needs to be replaced? 

The code that is being stripped is: 
```

<script type="text/javascript"><!--
google_ad_client = "pub-01234567890123456";
google_ad_width = 728;
google_ad_height = 90;
google_ad_format = "728x90_as";
google_ad_type = "text_image";
google_ad_channel ="";
google_color_border = "EEEECC";
google_color_bg = "EEEECC";
google_color_link = "1111BB";
google_color_text = "000000";
google_color_url = "008000";
//--></script>
<script type="text/javascript"
  src="http://pagead2.googlesyndication.com/pagead/show_ads.js">
</script> 

```
which makes it a bit trickier than "your old text" to pull off. 

I really appreciate the nudges in the right direction! 
eb

---

### Post by Vaphell on 2010-08-29
i concocted something like this:

```

#!/bin/sh

IFS='
'

subst='######## my stuff goes here ############
'
substlines=1

file="repl.txt";

pat1='<script type="text/javascript">\s*<!--\s*google_ad_client = "pub-01234567890123456";(\s*.*\s*)*?src="http://pagead2.googlesyndication.com/pagead/show_ads.js">\s*</script>'

echo Counting in all files:
grep -Pc $pat1 *

#a nice loop goes here

for file in *.html
do
  echo 'GREP
----------------------'
  line=`grep -Pn $pat1 $file | tr -s '\n' ' ' | sed 's/:.*$//g'`
  nlines=`grep -P $pat1 $file | grep -c '.'`
  echo pattern starts at line $line
  echo lines: $nlines
  endline=$((line+nlines-1))
  echo last 'line: $endline

'
  echo 'RESULT
-------------------'
  sed_ins=`echo "$line"i $subst`
  cat $file | sed $sed_ins > $file.tmp

  line=$((line+substlines))
  endline=$((endline+substlines))
  sed_cut=$line,"$endline"d
  sed $sed_cut $file.tmp
  sed $sed_cut $file.tmp > $file.result
  rm $file.tmp
done

```

currently it assumes that there is only 1 occurence in a file, that there is nothing in the same line at the beginning and end of the pattern (whole lines are replaced), there are no empty lines inside the pattern (non-empty line counting). Script currently works only on a single file defined at the beginning. Adding a loop would be trivial.
I used a lot of variables for parameters because i couldn't understand what was happening way to often and i echoed everything :)
regexp may suck in some cases (different formatting, additional or missing spaces/newlines - necessary fixes with \s*) but worked on my example file just fine and i really had enough fun with this already ;-).

how it works. Regexp searches for <beginning>(n lines of whatever)<ending> and calculates the number of lines the pattern occupies, custom string is inserted at that position thus moving the pattern down, calculated number of lines after the inserted string are out (pattern is removed).

edit: added a halfassed loop with no testing

---

### Post by d3v1150m471c on 2010-08-29
note the "*" in my post above. it's a bash alias for everything. in this  case every file in your working directory where "x" is the variable for  "*" because sed will assume * or "x" as a file. thus, the for-loop will  do what it's told to every file ( * ) it finds in the directory you're  in.

I made this bash script with the name "some" and ran it:
```

#!/bin/bash
for x in *
do sed 's/something for nothing/whoa/' "$x" > "$x".new
done

```

This is the result. A new file named some.new with the contents:
```

#!/bin/bash
for x in *
do sed 's/whoa/whoa/' "$x" > "$x".new
done

```

As you can see above the for-loop worked and changed the section "something for nothing" to "whoa" in our .new file

---

### Post by Razmear on 2010-08-29
> **Vaphell said:**
> ... worked on my example file just fine and i really had enough fun with this already ;-).


Wow! Thanks Vaphell! 
I'll play around with your code tomorrow after work and see if I can make it work on a backup copy of the website. The pages have between 0 and 2 instances of the code, so running the script twice to ensure a complete purge is no problem at at all, and certainly better than hand editing the 85 to 100 pages on the sites. 

I owe ya one Vaphell!
eb

---

### Post by Vaphell on 2010-08-30
nlines=... part will not be trivial. Currently it counts the non-empty lines in grep output, but if there are 2+ occurences it will sum up all lines of all results and a bunch of newlines everywhere doesn't make it any easier to decide where things start and where they end. Some neat trick is required to split results nicely.

edit:
grep -m 1 stops searching after 1 match, so it should be possible to do it your way with as many steps as needed.

god damn, this script is so fragile >_< i got all the loops and stuff but i can't get proper insertions and deletions :/
edit2: my bad - i wanted to do too much on a single temporary file and soon i was getting empty one :-)

```
#!/bin/sh

IFS='
'

subst='######## my stuff goes here ############
'
ext="new"
pat1='<script type="text/javascript">\s*<!--\s*google_ad_client = "pub-01234567890123456";(\s*.*\s*)*?src="http://pagead2.googlesyndication.com/pagead/show_ads.js">\s*</script>'

echo Counting in all files:
grep -Pc $pat1 *.html

echo === MODIFICATION OF FILES ===
delext="del"
for file in *.html
do
  echo FILE: $file
  count=`grep -Pc $pat1 $file`
  echo \# of occurences: $count
  tmpfile=$file.tmp
  cp $file $tmpfile
  echo created temporary file $tmpfile
  
  for i in $(seq 1 $count)
  do
    line=`grep -Pn -m 1 $pat1 $tmpfile | tr -s '\n' ' ' | sed 's/:.*$//g'`
    nlines=`grep -P -m 1 $pat1 $tmpfile | grep -c '.'`
    echo pattern $i starts at line $line
    echo lines: $nlines
    endline=$((line+nlines-1))
    echo last line: $endline

    echo cutting lines $line-$endline
    sed_cut=$line,"$endline"d
    sed $sed_cut $tmpfile > $tmpfile.$delext

    sed_ins=`echo "$line"i $subst`
    sed $sed_ins $tmpfile.$delext > $tmpfile 
    echo "$subst" inserted at line $line

  done
#  echo === RESULT ===
#  cat $tmpfile
  echo __________________________________________
  echo Saving as $file.$ext
  echo '__________________________________________
'
  mv $tmpfile $file.$ext && rm $tmpfile.$delext
done
```

file with a bunch of keyboard mashing junk and 3 instances of the code snippet passes with flying colors here

---

