---
title: "Use Linux script to batch change file names in a folder"
date: 2009-11-09
forum: General Help
---

### Post by jiapei100 on 2009-11-09
I would like to change file names in two ways

1)
1.jpg -> 0001.jpg
2.jpg -> 0002.jpg
...
x.jpg -> 000x.jpg
...
xy.jpg -> 00xy.jpg

2)
5201.jpg -> 5001.jpg
5202.jpg -> 5002.jpg
...
5xyz.jpg -> 5(x-2)yz.jpg (where x >= 2)


Can anybody please be kind enough to help???

Best Regards
JIA

---

### Post by eric3_14159 on 2009-11-09
I realize that these are two very different approaches, but they're the first ways which occurred to me for each.

For the first case, this should do it, assuming that the files go from 1 to 20:
```

for i in `seq 1 20`
 do
 mv "$i.dat" `printf "%04d.txt" $i`
done

```
For the second case, assuming all of the files are in the form 5xyz.jpg:
```

for i in 5???.jpg
 do
 n=`basename "$i" .jpg`
 n=`expr $n - 200`
 mv "$i" "$n.jpg"
done

```

Hope that helps! I'll be happy to explain any parts of the scripts that don't make sense or don't work, if you need it.

---

### Post by mo.reina on 2009-11-09
this would be my solution for the first

```
#!/bin/bash

total=ls | grep -c .txt 		#counts number of jpg files
x=1					#variable used for naming files
counter=0				#variable used
while [ $counter -lt $total ]; do
	mv "$x.txt" "000$x.txt" 	#renames filenames
	x=$[x+1]	
	counter=$[counter+1] 
done

```

---

