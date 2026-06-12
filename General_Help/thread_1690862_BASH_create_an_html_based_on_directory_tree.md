---
title: "BASH: create an html based on directory tree"
date: 2011-02-19
forum: General Help
---

### Post by ethernaly on 2011-02-19
Hello, I've a complex folders structure.

Main folder called "progetti" (/root/progetti) with a lot of projects (for example, project1, project2, project3..)

every project has 6 subfolders (CD1, CD2, CD3, CD4, CD5, CD6) and all of those folders have a certain numbers of PDF files.

For example:
```
:~# ls progetti/progetto1/CD2/  
a-2-1.pdf  a-2-2.pdf
```

At the moment, I make this script:
```
#!/bin/bash
rm lista.html
touch lista.html

echo '<!DOCTYPE HTML>' > lista.html
echo '<html><body>' >> lista.html
echo '<div id="contenitore">' >> lista.html

IFS='
'

array=(`ls /root/progetti/`) 
len=${#array[*]}
i=0
while [ $i -lt $len ]; do
echo '<div id="' ${array[$i]} '">Progetto' ${array[$i]} '</div><br>' >> lista.html
let i++
done

arraya=(`ls /root/progetti/`)
lin=${#arraya[*]}
i=0
while [ $i -lt $len ]; do
echo '<div id="'${array[$i]}'-CD1"><a href="#'${array[$i]}'-exp1"> CD1</a></div><br>' >> lista.html
echo '<div id="'${array[$i]}'-CD2"><a href="#'${array[$i]}'-exp2">  CD2</a></div><br>' >> lista.html
echo '<div id="'${array[$i]}'-CD3"><a href="#'${array[$i]}'-exp3">  CD3</a></div><br>' >> lista.html
echo '<div id="'${array[$i]}'-CD4"><a href="#'${array[$i]}'-exp4">  CD4</a></div><br>' >> lista.html
echo '<div id="'${array[$i]}'-CD5"><a href="#'${array[$i]}'-exp5">  CD5</a></div><br>' >> lista.html
echo '<div id="'${array[$i]}'-CD6"><a href="#'${array[$i]}'-exp6">  CD6</a></div><br>' >> lista.html
let i++
done

echo '</div>' >> lista.html
echo '</body></html>' >> lista.html
```

but now, I've some problem to continue with others array to list the content of every CD's folder of every project folder to make something similar:
```
<div id="${array[$i]}-exp">
<a href="$PDFNAME1">$PDFNAME1</a>
<a href="$PDFNAME2">$PDFNAME2</a>
<a href="$PDFNAME3">$PDFNAME3</a>
<a href="$PDFNAMEN">$PDFNAMEN</a>
...etc..
</div>
 
```

If something is not clear, please ask me :) I hope someone of you will can help me.


Have a nice day, best regards,


Edit:

I have thought to insert after:
```
echo '<div id="'${array[$i]}'-CD6"><a href="#'${array[$i]}'-exp">  CD6</a></div><br>' >> lista.html
```
something similar:
```

echo '<div id="'${array[$i]}'-exp1'">" >> lista.html
arrayc=(`ls /root/progetti/${array[$i]}/CD1/`)
lon=${#arrayc[*]}
b=0
while [ $b -lt $len ]; do
echo '<a href="Documents/'${arrayc[$i]}'">'${arrayc[$i]}'</a><br>' >> lista.html
let i++
done

echo '<div id="'${array[$i]}'-exp2'">" >> lista.html
arrayd=(`ls /root/progetti/${array[$i]}/CD2/`)
lon=${#arrayd[*]}
b=0
while [ $b -lt $len ]; do
echo '<a href="Documents/'${arrayd[$i]}'">'${arrayd[$i]}'</a><br>' >> lista.html
let i++
done

echo '<div id="'${arraye[$i]}'-exp3'">" >> lista.html
arraye=(`ls /root/progetti/${array[$i]}/CD3/`)
lon=${#arraye*]}
b=0
while [ $b -lt $len ]; do
echo '<a href="Documents/'${arraye[$i]}'">'${arraye[$i]}'</a><br>' >> lista.html
let i++
done

echo '<div id="'${arrayf[$i]}'-exp4'">" >> lista.html
arraye=(`ls /root/progetti/${array[$i]}/CD3/`)
lon=${#arrayf[*]}
b=0
while [ $b -lt $len ]; do
echo '<a href="Documents/'${arrayf[$i]}'">'${arrayf[$i]}'</a><br>' >> lista.html
let i++
done

and also for other 3 CDs
```

well.. this code isn't good... no error but my "lista.html" increase it's size a lots (600MB), so I stopped it,  the strange thins is that there aren't a lots of pdf to parse..

---

### Post by lykeion on 2011-02-19
I think it would be easier to do this with a Python script instead of a bash script. Here's a starting point: [http://mayankjohri.wordpress.com/2008/07/02/create-list-of-files-in-a-dir-tree/](http://mayankjohri.wordpress.com/2008/07/02/create-list-of-files-in-a-dir-tree/)

---

