---
title: "need to extract data from .txt files. Need the best and brightest"
date: 2012-03-17
forum: General Help
---

### Post by jquis8411 on 2012-03-17
In my work a day life I deal with a program that spits out files that can be opened with  MS notepad, word, as well as linux gedit, nano and solaris text editor. it is  a .txt file in actuality although the file extension is always a sequential  number foo.99, foo.98 the file prefix is always the same (bar.99, bar.98, bar.97). I need to be able to collect data from a particular line in these files. To say it in plain english the script or command would say "from files foo.wildcard print lines 3, and 15-17 to file ~/test. Any help is appreciated Thank you community

---

### Post by papibe on 2012-03-17
Hi jquis8411

If the files are plain text files, I think the best tool is 'awk'. For instance, if you want to print line 3 of the file 'bar.txt':
```
awk 'NR==3 {print}'  bar.txt
```
where
[INDENT]NR is the variable that hold the current line.
print will print the whole line.
[/INDENT]If you want the result of that command save into the file 'test.txt' you do this:
```
awk 'NR==3 {print}'  bar.txt  > test.txt
```
In case you need more lines, just add another rule. For example, if you need to print line 3 and 15:
```
awk 'NR==3 {print} NR==15 {print}'  bar.txt  > test.txt
```

When you need a range, you can use the && operator in your condition. This will print lines 3, and lines between 15 and 17 (those included):
```
awk 'NR==3 {print} NR>=15 && NR<=17 {print}'  bar.txt  > test.txt
```

Now, let's say you want to do the same operation to several text files (like bar.01, bar.02, etc). 'awk' will have no problem receiving them as parameters, however the NR will count all lines on those files as they were being paste together. Luckily, there's a another internal variable that hold the value of the current line per file: FNR.

With all that in mind, I think this would get you very close on what you're looking for:
```
awk 'FNR==3 {print} FNR>=15 && FNR<=17 {print}'  bar.*  >  ~/test
```
[Here]("http://www.thegeekstuff.com/2010/01/awk-introduction-tutorial-7-awk-print-examples/")'s more basic examples on how to use awk.

Hope that helps, and tell us how it goes.
Regards.

---

### Post by jquis8411 on 2012-03-17
I wish you could see the smile on my face right now. Excellent work, you are a credit to the community. This is exactly what I was hunting for.

---

