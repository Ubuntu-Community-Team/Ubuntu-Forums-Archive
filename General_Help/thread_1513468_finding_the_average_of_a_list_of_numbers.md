---
title: "finding the average of a list of numbers"
date: 2010-06-19
forum: General Help
---

### Post by netmonky on 2010-06-19
Hi guys,

I am new to linux and I would like to know how to find the average of a list of numbers using bash.

my file looks like below:

5.05
5.10
5.34
4.56
5.04
5.40
5.02
5.11
5.45
5.32
4.81
5.09
5.55
2.78
4.17
4.75


I basically want to add the below at the end of the file

====================
average = <average> 
====================

Can anyone help?

---

### Post by arrange on 2010-06-19
Are you looking for a complete code or just some pointers?

---

### Post by hakermania on 2010-06-19
bash script
> 
#!/bin/sh
#this is number 1 in first line
num1=`cat filepathhere | awk 'NR>0 && NR<2{print $0}'` 
#this is number 2 in second line etc etc
num2=`cat filepathhere | awk 'NR>1 && NR<3{print $0}'`

After this you do
(num1+num2+numx)/the number of the numbers

---

### Post by netmonky on 2010-06-19
I have the below to try and SUM the numbers then i was going to / by the amount of lines in the file ( wc -l). But its not accepting the decimal numbers in the variables. 

 for NUM in `cat speed.txt |  awk '{print $3}' | cut -d "(" -f2`; do SUM=`echo $NUM+$SUM |bc`; echo $NUM; done ; echo "==================="; echo "SUM = " $SUM


`cat speed.txt |  awk '{print $3}' | cut -d "(" -f2` = the output above

can anyone give me some pointers plz :-) do i need to declare the variable as something? if so, how do i do this? 

THanks in advance

---

### Post by arrange on 2010-06-19
*awk* is a great tool to do this.
I love this tutorial: [http://www.vectorsite.net/tsawk_1.html](http://www.vectorsite.net/tsawk_1.html)

So a template could look something like```
awk '{s+=$1} END {print "Average: " s/NR}' $TheFile
```

---

### Post by Boondoklife on 2010-06-19
Give this a go:
> #!/bin/bash
# requires: bc
NUMS=$(cat $1);

TOTAL=0
LINES=0

for NUM in $NUMS; do
    if [[ $NUM =~ ^[0-9]+([.][0-9]+)?$ ]]; then
        TOTAL=`echo "$TOTAL + $NUM" | bc`
        LINES=$(($LINES+1))
        echo $TOTAL
        echo $LINES
        echo -----------
    fi
done

AVG=`echo "scale=2; ${TOTAL}/${LINES}" | bc`

echo "====================" >> $1
echo "average = $AVG" >> $1
echo "====================" >> $1

---

### Post by netmonky on 2010-06-19
thanks guys. It was just missing VAR=0 :-) as i was trying to add a number to nothing :D. 


Thanks for all your help ,

---

