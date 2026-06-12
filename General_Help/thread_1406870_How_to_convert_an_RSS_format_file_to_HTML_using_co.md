---
title: "How to convert an RSS format file to HTML using command line tools"
date: 2010-02-14
forum: General Help
---

### Post by keithpeter on 2010-02-14
Hello All

I'd like to find a way of 

1) capturing an RDF formatted RSS feed as a file on my computer

2) converting the result to HTML using local command line tools

I've sorted 1) with wget

Any ideas on 2? I've discovered xsltproc but I'm going round in circles.

The master plan is to import my [pinboard bookmarks]("http://feeds.pinboard.in/rss/u:keithpeter/") into a static web site produced on my linux box using a [handful of clever bash scripts]("http://www.cns.gatech.edu/~caballero/webconvertscripts.html").

---

### Post by keithpeter on 2010-02-14
Did some more googleing with better keywords

[http://www.webreference.com/perl/tutorial/8/](http://www.webreference.com/perl/tutorial/8/)

The perl modules install ok on Lenny

The script can be hacked easily to make the HTML output less clunky.

Anyone got anything better?

---

### Post by laceration on 2010-02-14
Maybe I am just a hacker, but I think XSLT is one of those ridiculous things that have to put a lot more into than you get out of it.  Bash is actually quite good for parsing RSS like so:  
```

xmllint -format $uri |
while read line 
do
	if expr match "$line" "<item.*"
	then
		itemfound=1
	fi
	if [ $itemfound ]
	then
		if expr match "$line" "<title.*"
		then 
                # do stuff

```
xmllint will get the RSS file like wget, but will format it with line endings, so the above will work.
If you decide to do it like this, I wrote a short and sweet function that will get element or attribute values.  Let me know in a reply and I'll post it here.

---

### Post by ilembitov on 2010-02-14
Use rawdog?

---

### Post by keithpeter on 2010-02-19
Hello All

Thanks for these replies, I've discovered that xmllint is already installed and found out about rawdog, which was not caught by my previous Google queries. 

@laceration, if you were to post your function, I would read it.

@ilembitov, the idea is to build part of a web site by pulling the links from my existing bookmark page on pinboard. So only one source...

Cheers

---

### Post by laceration on 2010-02-19
Here is my gxml function, which simply gets element or attribute values from xml, etc.  Save it as gxml in /usr/bin or wherever and 
$ gxml -h
for help/instructions

and a note... I was on [http://www.w3schools.com](http://www.w3schools.com) the other day and took a look at the XSLT tutorial, contrary to my previous experiences, it looked reasonable.  Maybe I just did not find a good guide to it before + that soured me.

gxml:
```

#!/bin/bash
#gxml
if test -z "$1"
then
echo "get element and attribute values from xml
usage: \$gxml \"xmlstring\" <attributename>
-h or --help for help"
elif [ $2 ]
then
#get attribute
y="$2="
v=${1##**$y}
v=$(echo $v | cut -d ' ' -f 1)
v=${v%\/\>**}
v=${v%\>**}
echo ${v//\"}
#bash handles the quotes
elif [ "$1" == "-h" -o "$1" == "--help" ]
then
echo "gxml is a quick and dirty helper app originally for OSTV to simply get element and attribute values from xml.
usage: \$gxml \"xmlstring\" <attributename>
usage examples:
\$gxml \"<media:title type=\"plain\">Nerac Pro Cycling Promotional Video</media:title>\"
will return element value:
Nerac Pro Cycling Promotional Video
\$gxml \"<media:title type=\"plain\">Nerac Pro Cycling Promotional Video</media:title>\" type
will return attribute value:
plain
Always double quote the the first argument string, even if using a variable:
gxml \"\$z\" 
Though the xmlstring may have double quoted attribute(s) within, which on its face would seem to break the program, bash handles it.  It actually breaks without the double quotes.
gxml works for 1 value and 1 line at a time and is intended to be used like this:
wget xmlfile -O - | grep \"title\" |
while read line
do
gxml \"\$line\"
done
if an xml file, like many of google's, does not have line endings, preprocess with xmllint like this:
xmllint -format xmlfile.  xmllint can be used to retrieve the xml file and can replace wget in the above example.
gxml should work on html or any sgml"
else
#get element value
v=${1#\<**\>}
echo ${v%\<**\>}
fi


```

---

### Post by cariboo on 2010-02-19
This is not a Cafe thread. Moved

---

### Post by keithpeter on 2010-02-21
Thanks laceration for the function and the tutorial link.

Thanks to moderator for shifting this to a more appropriate discussion. I think I understand the difference.

---

