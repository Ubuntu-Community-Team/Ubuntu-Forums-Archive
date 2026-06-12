---
title: "How to parse line with colon field separation"
date: 2011-01-16
forum: General Help
---

### Post by inverser on 2011-01-16
Source:
```
JAMES ::: AAAA ::: 1111
JANET ::: BBBB ::: 2222
LAURA ::: CCCC ::: 3333
DAVID ::: DDDD ::: 4444
```Desired Output:
```
JAMES:AAAA
JANET:BBBB
LAURA:CCCC
DAVID:DDDD
```Is there a way to do this from command line?

---

### Post by TeoBigusGeekus on 2011-01-16
```
sed -i "s/.........$//" nameoffile.ext
```
Delete the last 9 characters from every line.
```
sed -i "s/ ::: /:/" nameoffile.ext
```
Replace the string " ::: " with ":".

---

### Post by Smart Viking on 2011-01-16
One way with sed:
```
sed 's/ ::: /:/g' file.txt
```
or if you pipe it
```
cat file.txt | sed 's/ ::: /:/g'
```

---

### Post by inverser on 2011-01-16
> **TeoBigusGeekus said:**
> ```
sed -i "s/.........$//" nameoffile.ext
```Delete the last 9 characters from every line.
```
sed -i "s/ ::: /:/" nameoffile.ext
```Replace the string " ::: " with ":".
Hi, TBG. Thank you for your reply. 

In regards to your solution, 

1) Some of the values of field #3 (1111, 2222, 3333, 4444) are longer than 9 char. How I solve this?

---

### Post by TeoBigusGeekus on 2011-01-16
Replace the first command I gave you with this
```
sed -i "s/ ::: [0-9]*$//" nameoffile.ext
```
Deletes the pattern " ::: any_number anyothercharacters" from the end of each line.

---

### Post by mobilediesel on 2011-01-16
> **inverser said:**
> Source:
```
JAMES ::: AAAA ::: 1111
JANET ::: BBBB ::: 2222
LAURA ::: CCCC ::: 3333
DAVID ::: DDDD ::: 4444
```Desired Output:
```
JAMES:AAAA
JANET:BBBB
LAURA:CCCC
DAVID:DDDD
```Is there a way to do this from command line?
Awk can handle that easily:
```
awk -F' ::: ' '{print $1":"$2}' file.txt
```

---

### Post by inverser on 2011-01-16
> **mobilediesel said:**
> Awk can handle that easily:
```
awk -F' ::: ' '{print $1":"$2}' file.txt
```
Wow, thank you mobilediesel. That chugged through my database very quickly. 

Thank you everyone for your help!!

---

### Post by mobilediesel on 2011-01-16
> **inverser said:**
> Wow, thank you mobilediesel. That chugged through my database very quickly. 

Thank you everyone for your help!!

I've only been learning awk fairly recently. Sed can actually do the job pretty easily, as well.
```
sed 's/\(.*\) ::: \(.*\) ::: .*/\1:\2/' file.txt
```
There would probably be a speed difference on large amounts of data but I don't know which would be faster.

---

