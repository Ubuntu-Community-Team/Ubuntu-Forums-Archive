---
title: "SED command help: not quite getting results I want"
date: 2012-05-01
forum: General Help
---

### Post by jclose on 2012-05-01
Hey all,
   I am trying to get a SED command set up to insert a colon into a string.  I want to match a certain pattern, of course, and then insert the colon two numbers from the end of the pattern.  (I hand typed in some 'time' value in a text document, and now I want to import that into a spreadsheet; the spreadsheet won't recognize it as a 'time' without a colon.)
    My input file is a CSV file.  Here is a sample:
```

TIME LOG,,,,,,,,,,,,,,,
Date,Start,End,Hrs,,Task,Description,,,,,,,,,
2012.1.11,,,,,,,,,,,,,,,
,845,1000,,295:  CMs ,,,,,,,,,,,
,1000,1030,,445 request,,,,,,,,,,,
,1030,1100,,295; analyze ,,,,,,,,,,,
,1100,1230,,272; Beta ,,,,,,,,,,,
,1230,1300,,295  Mtg,,,,,,,,,,,
,1300,1330,,295  Finish,,,,,,,,,,,
,1330,1615,,272 again,,,,,,,,,,,

```

1st column is the date, 2nd and 3rd are the two time values.

Here is the SED command I have been fiddling with:
```

sed 's/\(,[0-9]*[0-9]\)\([0-9][0-9],\)/\1:\2/g' <test.csv >temp.csv

```

I was trying to accomplish:  
<group1>
"comma" followed by
"Zero or more digits" followed by
"One digit"
</group1>
<group2>
"one digit" followed by 
"one digit" followed by
"comma"
</group2>

Substitute with:
"group1:group2"


(My version of Sed didn't seem to recognize the '+' operator as a 'one or more' function.  So did the zero-more and one form in the first group.  Didn't see a '--version' option in the man, so don't know which it is exactly.  This is on Mac OS 10.6.8, actually.  :) )

Here's my output:
```

TIME LOG,,,,,,,,,,,,,,,^M
Date,Start,End,Hrs,,Task,Description,,,,,,,,,^M
2012.1.11,,,,,,,,,,,,,,,^M
,8:45,1000,1:55,295:  CMs ,,,,,,,,,,,^M
,10:00,1030,,445  request,,,,,,,,,,,^M
,10:30,1100,,295; analyze ,,,,,,,,,,,^M
,11:00,1230,,272; Beta ,,,,,,,,,,,^M
,12:30,1300,,295  Mtg ,,,,,,,,,,,^M
,13:00,1330,,295  Finish,,,,,,,,,,,^M
,13:30,1615,,272 again ,,,,,,,,,,,^M

```

I wanted it global to hit both 2nd and 3rd field.  It doesn't seem to be doing that.  (Although it did grab the 4th field in one instance.)

This form was working pretty well, except that it grabbed some extra things in the first field:
```

sed 's/\([0-9]*\)\([0-9][0-9],\)/\1:\2/g' <test.csv >temp.csv

```

Any help would be appreciated.

Thanks,
J

---

### Post by steeldriver on 2012-05-01
I think the problem is the *first* match eats commas at both ends

,1000,

leaving

1030,,...

so there is no leading comma to match your regex on the next attempt - how about only matching the trailing comma of each csv field i.e.

sed 's/\([0-9]*[0-9]\)\([0-9][0-9],\)/\1:\2/g'

---

### Post by jclose on 2012-05-01
Ah, I see what you are getting at.  I added that leader for some reason...I think it was to prevent matching the last two digits in the first field (year.mo.dy).  But I don't think that I tried it with the newer 'leading digits before the last two' form.  I will give it another shot. 

Thanks for the suggestion!

- J

---

### Post by jclose on 2012-05-01
Yep, that appears to have done it!

It also inserts into the fourth field, but I don't care about that; I will be deleting that column anyway.  (And there are only 1 or 2 instances of data in that field to begin with.)

Thanks again Steeldriver!

- J

---

