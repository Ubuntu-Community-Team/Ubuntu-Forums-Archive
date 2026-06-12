---
title: "how to get it with shell?"
date: 2010-04-07
forum: General Help
---

### Post by luofeiyu on 2010-04-07
there is a txt file :
["date"]1
["asset"]2
["cash"]3
["finance"]4
["note"]5
["2009-12-31"]6
["580 "]7
["1,693,048,000,000"]8
["20,147,000,000"]9
["500"]10
["2009-09-30"]11
[" 680"]12
["1,777,512,000,000"]13
["24,977,000,000"]14
["700"]15

what i want to get is :
["date"]0
["asset"]1
["cash"]2
["finance"]3
["note"]4
["2009-12-31"]5
["580 "]6
["1,693,048,000,000"]7
["20,147,000,000"]8
["500"]9
["2009-09-30"]10
[" 680"]11
["1,777,512,000,000"]12
["24,977,000,000"]13
["700"]14

how to get it with shell?

---

### Post by cjhabs on 2010-04-07
```

cat test.txt | while read line; do 
		echo -n ${line%]*}]
		let newnumber=${line#*]}-1
		echo $newnumber		
done

```

where your data is in test.txt
I am getting a spurious line at the end - not sure why.

---

### Post by diesch on 2010-04-07
```
awk -F ']' '{print $1"]"$2-1}' test.txt
```

---

### Post by luofeiyu on 2010-04-07
both of them can get what i want,thank you 
awk -F ']' '{print $1"]"$2-1}' test.txt  >>  aftertest.txt
the command make aftertest.txt  contain  the result.

how to add some commands in the script  to  load  the result??
such as :  awk -F ']' '{print $1"]"$2-1}' test.txt  >>  aftertest.txt

cat test.txt | while read line; do 
		echo -n ${line%]*}]
		let newnumber=${line#*]}-1
		echo $newnumber		
done

---

### Post by sisco311 on 2010-04-07
```

cat test.txt | while read line; do 
  echo -n ${line%]*}]
  let newnumber=${line#*]}-1
  echo $newnumber		
done > path/to/file
```

---

### Post by luofeiyu on 2010-04-08
now i have a txt file :
for x in {1..10..2}
> do
> echo  $x
> done

i want to get :
for x in {1..10..2}
do
echo
done

i  can  change  the following file txt1  with command into  txt2
txt1
> do
> echo  $x
> done
command
awk -F ' '  '{print $2 }'  txt1

txt2
do
echo
done

how to change txt3  into  txt4  with awk??
txt3
for x in {1..10..2}
> do
> echo  $x
> done
txt4
for x in {1..10..2}
do
echo
done

i will appreciate your help.

---

