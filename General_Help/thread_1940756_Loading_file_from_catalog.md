---
title: "Loading file from catalog"
date: 2012-03-14
forum: General Help
---

### Post by lolek198787 on 2012-03-14
Hi,

I'm going to write script which count numbers of line in file.
Code:
```
#!bin/sh  
 for i in `ls ./zzz` 
do 
number=0         
while read line        
 do                
  number=`expr $number + 1`       
  done < "./zzz/$i" 
echo "$i: $number"        
 if [ $line -lt 10 ]; then          
 echo "File: $i less then 10 line.\n"         
  else           
echo "OK"          
 fi   
done 
```Problem is that var i is readed only one time, for other files no(For example catalog has 5 files: one, two,three,four,five and readed is only file "one" and has got 2 lines, for other number of line is 0)

---

