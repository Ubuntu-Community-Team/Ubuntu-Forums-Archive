---
title: "How to return a list of files without the extensions"
date: 2011-01-03
forum: General Help
---

### Post by rickcjmac on 2011-01-03
I am writing a bash shell script and I am trying to use a select case to modify a few files with the same filename but different extensions (i.e. problem.tex problem.log problem .pdf etc.)

It goes something like this:

Select item in $list
do 
compile $item.tex
open    $item.pdf
delete  $item.log
break
done
exit

Right now my list is 
list=$( find . -maxdepth 1 -name "*.tex" )
which returns a list only from the current directory of all files ending in .tex so when I try to open the resulting .pdf file I get the error:

error: file problem.tex.pdf doesn't exist

So I'm trying to find a way to use just the name in a select menu. If anyone has a work around I would be very appreciative :)

Thanks for the help!

---

### Post by PapaNerd on 2011-01-03
Try creating a new variable which is everything up to the period.```
shortname=`echo $item | nawk 'BEGIN {FS="."} {print $1}'`
```
If the file name contains more than one period, you will need to add a look within nawk to process that.
If the file name will always have a three character extension, you can always just lop off the final four characters.

---

### Post by Vaphell on 2011-01-03
you can also use sed to do substitution at the end (in the example .tex is replaced by empty string)
echo "$item" | sed 's/\.tex$//g'

---

### Post by sisco311 on 2011-01-03
I would try something like:
```
for file in *.tex; do
  item="${file%.tex}"
  **open** "${item}.pdf"
  **delete** "${item}.log"
done
```

---

### Post by rickcjmac on 2011-01-04
All of these replies worked perfectly. I used

```
select file in *.tex; do
  pdflatex $file
  item="${file%.tex}"
  gnome-open "${item}.pdf"
  delete "${item}.log"
  break
done
```

and it works perfect. It does exactly what I want it to :)

Thank you for all of your help!!! Community support is awesome :)

---

### Post by sisco311 on 2011-01-04
Cool! You are welcome.

Don't forget to mark this thread as [SOLVED].

---

