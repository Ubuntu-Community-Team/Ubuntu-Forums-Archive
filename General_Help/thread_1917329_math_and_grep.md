---
title: "math and grep"
date: 2012-01-29
forum: General Help
---

### Post by conradin on 2012-01-29
Hi all is there a way to use math and grep together?
Heres the gist:
There is a long string in a file formatted like this:
$ stuff,stuff,stuff,stuff,stuff,stuff,A*stuff>

where stuff is stuff I just dont care about at all, and ,A* is all I want to find in any string that starts with $ and ends with >
is there some easy way to count the commas (6 of them) then look for the letter "A" Followed by the asterisk, and ending in ">"?
That seems like the way to go if its possible.

---

### Post by conradin on 2012-01-29
```
 grep '\$GPGLL\,[[:digit:]][[:digit:]][[:digit:]][[:digit:]]\.[[:digit:]][[:digit:]][[:digit:]][[:digit:]]\,[[:alpha:]]\,[[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]]\.[[:digit:]][[:digit:]][[:digit:]][[:digit:]]\,[[:alpha:]]\,[[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]]\.[[:digit:]][[:digit:]][[:digit:]]\,[A]\*' someFile

```
matches, 
$GPGLL,4250.5589,S,14718.5084,E,092204.999,A*2D>
which is a valid string, and will deject a string like:
$GPGLL,4250.5589,S,14718.5004,E,000004.909,V*2D> but will fail, if there is different numbers of numbers.

Can someone help me simplify this? 
The NEMA Standard Im trying to match is GPGLL listed here:
[http://robosoft.info/en/technologies/knowledgebase/nmea0183](http://robosoft.info/en/technologies/knowledgebase/nmea0183)

---

### Post by conradin on 2012-01-30
Got with help from scu-ba-de-buntu:
This code validates the nema standard for a GPGll sentence as shown (to my understanding of it) at:
[http://robosoft.info/en/technologies/knowledgebase/nmea0183](http://robosoft.info/en/technologies/knowledgebase/nmea0183)
 
```
 grep -E -o '\$GPGLL,[0-9]+\.[0-9]+,[NS],[0-9]+\.[0-9]+,[EW],[0-9]+\.[0-9]+,A\*..>' <filename>

```

:KS:KS:KS:KS:KS

---

