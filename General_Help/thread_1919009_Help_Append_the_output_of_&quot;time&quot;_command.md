---
title: "Help: Append the output of &quot;time&quot; command to the same file and insert timestamp?"
date: 2012-02-02
forum: General Help
---

### Post by vcrpcant on 2012-02-02
How can I append output of "time" command to a file and insert timestamp?




Currently I can achieve the first part, which is this :
$ { time cp -R /home/user/folder1/* /home/user/folder2/; } 2>>output.txt

(text in the output.txt):

real    0m0.002sa
user    0m0.010s
sys    0m0.000s

real    0m0.002sw
user    0m0.010s
sys    0m0.000s

real    0m0.002s
user    0m0.010s
sys    0m0.000s




But what I want to achieve is this:
(text in the output.txt):

20120101
real    0m0.002sa
user    0m0.010s
sys    0m0.000s

20120202
real    0m0.002sw
user    0m0.010s
sys    0m0.000s

20120203
real    0m0.002s
user    0m0.010s
sys    0m0.000s

---

### Post by Wayne_V on 2012-02-02
probably something more along the lines of:

$ cd /home/user/folder1 ; for f in * ; do date +%Y%m%d ; time cp -R $f ../folder2 ; done | tee output.txt 2>&1

as long as you don't have files with special characters in the names ....  if you do you will have to change the "for f in *" to something like "ls -1 . | while read f" and then wrap $f with quotes as well

---

### Post by Vaphell on 2012-02-02
> as long as you don't have files with special characters in the names .... if you do you will have to change the "for f in *" to something like "ls -1 . | while read f" and then wrap $f with quotes as well

sorry but no, if anything it's the exact opposite.
globbing in *for f in ** is built-in and as foolproof as it gets, while your idea of parsing the ls output is doomed to fail at special characters, newlines, etc. Ls should not be used to provide the list of files to work on, ever.

any variable that potentially has whitespaces in it should be double-quoted - agreed.

---

### Post by vcrpcant on 2012-02-05
I've tried, but no success:( 
wasted about three hours on this:(

---

### Post by Khayyam on 2012-02-05
vcrpcant ..

Something like this?

```
echo $(date +%Y%m%d) 1>>output.txt ; {time cp -R /home/user/folder1/* /home/user/folder2/;} 2>>output.txt
```

HTH ...

---

### Post by vcrpcant on 2012-07-01
I will give it a try one of this days :)
I've managed to live with a simples solution meanwhile...

---

### Post by Paddy Landau on 2012-07-01
Khayyam comes closest to the solution.

Here is a simplified version. If this is in a script, do it over two lines:
```
date +$'\n'%Y%m%d >>output.txt    # Log the date after a blank line.
time cp -R /home/user/folder1 /home/user/folder2 >>output.txt # Copy folder1 to folder2, noting the time taken.
```If it is a single line that you need, separate the commands with a semi-colon:
```
date +$'\n'%Y%m%d >>output.txt; time cp -R /home/user/folder1 /home/user/folder2 >>output.txt
```

EDIT: This should really be in the [Programming Talk forum]("http://ubuntuforums.org/forumdisplay.php?f=39").

---

