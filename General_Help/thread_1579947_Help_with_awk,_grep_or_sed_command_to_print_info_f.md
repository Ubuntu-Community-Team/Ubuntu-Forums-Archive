---
title: "Help with awk, grep or sed command to print info from text file ???"
date: 2010-09-22
forum: General Help
---

### Post by dark-triad on 2010-09-22
Hi, i have a txt file containing weather info such as:

```
<dnam>Norwich, United Kingdom</dnam>
<tm>7:26 PM</tm>
<lat>52.63</lat>
<lon>1.30</lon>
<sunr>6:33 AM</sunr>
<suns>7:03 PM</suns>
<t>Partly Cloudy</t>
```

and im after a command that will print the "Partly Cloudy" from inbetween   <t>........</t>, or the "7:26" from between <tm>.........</tm>  etc. i have been playing with sed, awk and grep, im geting there, but the closest i have came to is printing all numbers in the file rather than just the ones i specify, i cant seem to get the command right, and now my head and eyes are starting to ache from reading man pages, examples and staring at the terminal lol, so im giving in and asking for help, anyone know of a solution?

Thanks, any help appreciated!

---

### Post by sisco311 on 2010-09-22
Try something like:
```
awk -F "</?dnam>" '{if ($2!="") print $2}' path/to/file
```

---

### Post by blueridgedog on 2010-09-22
Worse implementation, but I typed it, so I will post it:


```
cat pathtofile | awk '/<tm>/,/<\/tm>/' | awk 'sub(/<tm>/,"")' | awk 'sub(/<\/tm>/,"")
```'

---

### Post by dark-triad on 2010-09-22
Haha its working , cheers brother!
However ive just realised that further down in the text file some are used multiple times such as the "<t>" like

```
<t>WSW</t>
<t>Partly Cloudy</t>
<t>Waxing Gibbous</t>
<t>Drizzle Late</t>
<t>N/A</t>
```

So the command spits out:

```
WSW Partly Cloudy Waxing Gibbous Drizzle Late N/A
```

Can i pipe into another command to break it into individual words or specify the individual words?

Such as just "Partly Cloudy" or "Waxing Gibbous" etc

Thanks

---

### Post by dark-triad on 2010-09-22
Thanks sisco311 and blueridgedog both commands are working, but i still have the issue with multiple matches due to the text layout of the file.

---

### Post by VCoolio on 2010-09-22
Try to pipe to sed like this:
```
cat file | sed -e :a -e 's/<[^>]*>//g;/</N;//ba'
```
[credits](http://www.pement.org/sed/sed1line.txt)

---

### Post by dark-triad on 2010-09-22
Thanks Vcoolio but that seems to chop the words up and mix them together or something, it returns:

```
WSWzzle Lateus
```

---

### Post by Girya on 2010-09-30
try this

```
sed -e :a -e 's/<[^<]*>/ /g;/</{N;s/\n/ /;ba;}' 
```

worked fine with your example.

I pinched it from this page [http:///www.unixguide.net/unix/sedoneliner.shtml]("http:///www.unixguide.net/unix/sedoneliner.shtml")

---

