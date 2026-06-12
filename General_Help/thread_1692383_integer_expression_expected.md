---
title: "integer expression expected"
date: 2011-02-21
forum: General Help
---

### Post by Fitch on 2011-02-21
I am connecting a fridge temperature sensor to the serial in port and have got everything just about right.
I have produced  a script below which in itself has been running fine.

#!/bin/bash
/usr/bin/digitemp_DS9097 -a -q -o"%d/%b/%g %H:%M%t%.2C" -c /etc/digitemp.conf >> /home/brafferton/Downloads/$(date +%G-%b).csv

This adds a line to the file similar to:
21/Feb/11 14:30  4.06 to a file which in this case is: 2011-Feb.csv

Because the sensor runs in parasitic mode, every now and then it reads "85.00" degrees Celsius - which is its error code, e.g:
21/Feb/11 14:31  85.00

I wanted to get the sensor to re-read if it picked up the error. 
I thought of:

#!/bin/bash
/usr/bin/digitemp_DS9097 -a -q -o"%d/%b/%g %H:%M%t%.2C" -c /etc/digitemp.conf > /home/brafferton/Downloads/check.txt
CHECK=$(tail -c 6 /home/brafferton/Downloads/check.txt)
if [ "${CHECK}" -le 20 ] ;then
cat /home/brafferton/Downloads/check.txt >> /home/brafferton/Downloads/$(date +%G-%b).csv
else
# The next bit is just to stuff the output directly into the csv file and hope it isn't 85 degrees.
# My knowledge of getting it back to line 2 is zero, (and I'm worried of an endless loop if the sensor is knackered)
/usr/bin/digitemp_DS9097 -a -q -o"%d/%b/%g %H:%M%t%.2C" -c /etc/digitemp.conf > /home/brafferton/Downloads/$(date +%G-%b).csv
fi

Anyway!
I get:

line 4: [: 85.00: integer expression expected

I know that it's expecting a number and getting a string, but I think I need the output of tail to be an integer.

Any thoughts?

---

### Post by Fitch on 2011-02-21
I think I've got it

#!/bin/bash
COUNT=4
while [ $COUNT -gt 0 ]; do
  /usr/bin/digitemp_DS9097 -a -q -o"%d/%b/%g %H:%M%t%.2C" -c /etc/digitemp.conf > /home/brafferton/Downloads/check.txt
  CHECK=$(tail -c 6 /home/brafferton/Downloads/check.txt)
     if [ "${CHECK}" = 85.00 ];then
#        echo bad result
        COUNT=$((COUNT - 1))
     else
        COUNT=0 
        cat /home/brafferton/Downloads/check.txt >> /home/brafferton/Downloads/$(date +%G-%b).csv
#        echo good result
     fi
done

---

### Post by Vaphell on 2011-02-21
hint: use [code] tags to make it readable

---

### Post by Fitch on 2011-02-21
AHA!
Didn't know the code tag existed till now Thanks.
Still looks a bit of a mess though!

```
#!/bin/bash
COUNT=4
while [ $COUNT -gt 0 ]; do
  /usr/bin/digitemp_DS9097 -a -q -o"%d/%b/%g %H:%M%t%.2C" -c /etc/digitemp.conf > /home/brafferton/Downloads/check.txt
  CHECK=$(tail -c 6 /home/brafferton/Downloads/check.txt)
     if [ "${CHECK}" = 85.00 ];then
#        echo bad result
        COUNT=$((COUNT - 1))
     else
        COUNT=0 
        cat /home/brafferton/Downloads/check.txt >> /home/brafferton/Downloads/$(date +%G-%b).csv
#        echo good result
     fi
done
```

I have to wait another hour to see if the thing works automatically (every 4 hours), but I'm hopeful..

---

