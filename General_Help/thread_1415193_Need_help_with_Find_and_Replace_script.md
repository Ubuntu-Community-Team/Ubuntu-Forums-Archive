---
title: "Need help with Find and Replace script"
date: 2010-02-24
forum: General Help
---

### Post by Funkey Monkey on 2010-02-24
Hello Guys,

I have a few .htm files that I would like to convert to XHTML standard.

To do think I need to find for example <HTML> and replace it with <html>

I did some googling:
[http://www.brunolinux.com/02-The_Terminal/Find_and%20Replace_with_Sed.html](http://www.brunolinux.com/02-The_Terminal/Find_and%20Replace_with_Sed.html)
[http://saragossa.net/linux-tips/pages/Linux+Find+and+Replace.php](http://saragossa.net/linux-tips/pages/Linux+Find+and+Replace.php)

and tailored the script to:

#!/bin/bash
     for fl in *.htm; do
     mv $fl $fl.old
     #sed 's/FINDSTRING/REPLACESTRING/g' $fl.old > $fl
     sed 's/<HTML>/<html>/g' $fl.old > $fl
     sed 's/<\/HTML>/<\/html>/g' $fl.old > $fl
     rm -f $fl.old
     done

Then I saved the file as FindandReplace in the same directory as the files to be "edited"
Then I made the file executable
Then I double clicked on the file
Then I checked the the .htm files but none of the <HTML> tags was changed to <html>

Please be so kind as to advise me as to what I am doing wrong.
Also how do I "run" the file in gnome-terminal

Thanks

---

### Post by DaithiF on 2010-02-24
the main problem is that your two sed commands operate on the (same) original file, so the first set of changes are discarded ... ie. no matter what changes your first sed command starts with, the second one starts again with the original file, so the first changes are lost.

you can solve this in many ways, one way would be to use this command instead of your script.  Open a gnome-terminal, cd to the directory in which the htm files exist, and then do:
```
sed -i.old -e 's/<HTML>/<html>/g' -e 's/<\/HTML>/<\/html>/g' *.htm

```

this will keep copies of the original files with a suffix of  '.old', so you could revert to the originals if you have any problems.

---

### Post by Funkey Monkey on 2010-02-24
Thanks DaithiF, gonna give it a try right now, will report back.

Reportback:
Great its working. Thanks alot.


Here is the command I have for the items I wanted to change to be inline with XHTML.
This is by no means a complete list of items to change, but its a good starting point.

1) Copy code below, then remove tabs and returns (all code needs to be on a single line)
2) cd to the dir where the files are that needs to be changed
3) past and enter the code to have the changes made
sed -i.old
	-e 's/<HTML/<html/g'
	-e 's/\/HTML>/\/html>/g' 
	-e 's/<P/<p>/g'
	-e 's/\/P>/\/p>/g'
	-e 's/<LINK/<link/g'
	-e 's/\/LINK>/\/link>/g'
	-e 's/<BODY/<body/g'
	-e 's/<\/BODY>/<\/body>/g'
	-e 's/<META/<meta/g'
	-e 's/<\/META>/<\/meta>/g'
	-e 's/<DIV/<div/g'
	-e 's/<\/DIV>/<\/div>/g'
	-e 's/<I/<em/g'
	-e 's/<\/I>/<\/em>/g'
	-e 's/<SPAN/<span/g'
	-e 's/<\/SPAN>/<\/span>/g'
	-e 's/<SUP/<sup/g'
	-e 's/<\/SUP>/<\/sup>/g'
	-e 's/<TABLE/<table/g'
	-e 's/<\/TABLE>/<\/table>/g'
	-e 's/<TR/<tr/g'
	-e 's/<\/TR>/<\/tr>/g'
	-e 's/<TD/<td/g'
	-e 's/<\/TD>/<\/td>/g'
	-e 's/<BR>/<br /\>/g'
	-e 's/<B>/<strong>/g'
	-e 's/<\/B>/<\/strong>/g'
	-e 's/<SCRIPT/<script/g'
	-e 's/<\/SCRIPT>/<\/script>/g'
*.html

---

