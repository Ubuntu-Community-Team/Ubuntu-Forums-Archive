---
title: "Gedit 2.30.4 string replace problem..."
date: 2011-10-27
forum: General Help
---

### Post by dewplex on 2011-10-27
I'm working on a 10000 line document with <xml id="34567_fix"> type tags in it, this is taking me forever to just remove those tags from the document so that I can turn it into a flat .sh file.  Is there a faster way than just going through the document and deleting them a line at a time.  I will post an exact example below so that you can see the kinds of tags I'm dealing with.  Any help anyone could offer would be of great help.  Sorry if this is a stupid question.

```

<fix id="F-23915r1_fix"/>


<check system="C-27704r1_chk">


<fixtext fixref="F-23915r1_fix">


  V-22436">
GEN003950
    
    SV-26676r1_rule"

```

The above tags and code segments are all sections I need to just remove, and have been trying variations with the replace tool and advanced replace tools.  the numbers obviously change but the rest of the tags/code stays the same.

---

### Post by Vaphell on 2011-10-27
do yourself a favor and read about regular expressions and commandline tools like sed. Also there is a plugin for gedit that allows for regular expression magic.
[http://halfhourhacks.blogspot.com/2008/03/gedit-regular-expression-plugin.html](http://halfhourhacks.blogspot.com/2008/03/gedit-regular-expression-plugin.html)

for example to remove lines that look like <[some chars] [some chars]=[anything]>
```
**$ sed -r '/<[a-z]+ [a-z]+=.+>/d' test.txt**
V-22436">
GEN003950
   SV-26676r1_rule"

```
as you can see full tags from your example are gone

to replace [2 capital letters]-[numbers or chars]_rule with a string of choice
```
**$ sed -r 's/[A-Z]{2}-[0-9a-z]+_rule"/STRING_OF_CHOICE/g' test.txt**
<fix id="F-23915r1_fix"/>
<check system="C-27704r1_chk">
<fixtext fixref="F-23915r1_fix">
  V-22436">
GEN003950
   STRING_OF_CHOICE
```

---

