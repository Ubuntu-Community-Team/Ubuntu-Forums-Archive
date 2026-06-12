---
title: "Help with sed please, I'm stuck"
date: 2009-06-29
forum: General Help
---

### Post by kapu222 on 2009-06-29
I am trying to extract table information.
The target data is spread out among thousands of html files saved on my hard drive. 
Luckily, the data I need is consistent in that it has a predictable beginning and end.
So I tried to use sed, and am about to flipping lose it trying to get it to do this.
Maybe someone here can help.

So, like I said, the data is in HTML files stored locally, and nested deep in hundreds of directories. 

_The data I wish to extract is always preceded by:_
<table border><tr><th>Name<th>What<th>Region<th>Country<th>Lat<th>Long<th>Elev Ft.<td>Pop Est</tr>

_And always followed by:_
</table>


Between these can be anywhere from one record to hundreds of records.
_A single record example follows:_
<tr><td><a href=0/Angochi.html>Angochi</a><td>city<td><td>Aruba<td>12.5166667<td>-69.95<td>223<td>29442</tr>

I'll show you how terrible my regex skills are if you don't laugh too hard. _Here is what failed for me:_

sed 's/.*<tr><th>Name<th>What//;s/<\/table>.*//' *.*

It's hopeless I know. I am trying to learn. I would very much like to have this regex troll through the directory tree scanning each html file and output it to one file.

---

### Post by t4thfavor on 2009-06-29
I suggest brushing up on your admitedly sparse knowledge of regex. I am by no means a master of either sed, or its buddies, but I can be pretty sure that with a bit of regex training, or a generator(regexbuddy for windows...) you can probably find your way through this.

---

### Post by Celauran on 2009-06-29
What is the desired output? Are you trying to extract all the relevant tables and store them somewhere? Are you doing find-and-replace?

---

### Post by kapu222 on 2009-06-29
> **Celauran said:**
> What is the desired output? Are you trying to extract all the relevant tables and store them somewhere? Are you doing find-and-replace?

The desired output is each instance of a record, all in one file. the output can, if necessary, include what I earlier referred to as "what precedes the records", and "what follows the records". I can easily weed out the multiple instances of these "markers". But, if your skill set in regex sed awk what-have-you is ninja level, well I guess it could be done so that the output does not contain the "markers". So, once again, I am trying to concatenate all instances of "records" into one big file.

---

### Post by t4thfavor on 2009-06-29
why not match records only with something like this:

```

sed -n -e '/<tr><td><a href/p' table.html > html2.txt

```

This will give you just the url withouth the a.

I'm afraid I'm at my limit of sed and friends, I hope I was helpful.
```

#!/usr/bin/perl

my $sedout = `sed -n -e '/<tr><td><a href/p' /home/chance/table.html | /bin/grep \"$_\" | awk '{
            print \$2}'`;
print $sedout;

```

---

### Post by kapu222 on 2009-06-29
> **t4thfavor said:**
> why not match records only with something like this:

```

sed -n -e '/<tr><td><a href/p' table.html > html2.txt

```

extremely helpful!
Its something I will have to study, like you said. I hope someday It will just click for me. But regexes, sed, awk continue to challenge me. Thank you for your time!

---

### Post by Celauran on 2009-06-29
```
#!/usr/bin/env python

import re, sys

try:
    input_file = sys.argv[1]

f = open(input_file)
a = f.read()
f.close()

regex = re.compile('(?s)<table>.*?</table>')

results = regex.search(a).group()
results += "\n"

of = open('output', 'a+')
of.write(results)
of.close()
```

I wrote a tiny python script that will extract everything between <table> and </table> and append it to a file called output. You should be able to combine this with find to get the results you're looking for.

---

### Post by ghostdog74 on 2009-06-30
> **kapu222 said:**
> I am trying to extract table information.
The target data is spread out among thousands of html files saved on my hard drive. 
Luckily, the data I need is consistent in that it has a predictable beginning and end.
So I tried to use sed, and am about to flipping lose it trying to get it to do this.
Maybe someone here can help.

So, like I said, the data is in HTML files stored locally, and nested deep in hundreds of directories. 

_The data I wish to extract is always preceded by:_
<table border><tr><th>Name<th>What<th>Region<th>Country<th>Lat<th>Long<th>Elev Ft.<td>Pop Est</tr>

_And always followed by:_
</table>


Between these can be anywhere from one record to hundreds of records.
_A single record example follows:_
<tr><td><a href=0/Angochi.html>Angochi</a><td>city<td><td>Aruba<td>12.5166667<td>-69.95<td>223<td>29442</tr>

I'll show you how terrible my regex skills are if you don't laugh too hard. _Here is what failed for me:_

sed 's/.*<tr><th>Name<th>What//;s/<\/table>.*//' *.*

It's hopeless I know. I am trying to learn. I would very much like to have this regex troll through the directory tree scanning each html file and output it to one file.

the above sed will not work if your data spans multiple lines. show more details of your HTML file.

---

