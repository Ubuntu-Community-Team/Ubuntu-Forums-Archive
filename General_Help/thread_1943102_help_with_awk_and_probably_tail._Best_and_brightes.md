---
title: "help with awk and probably tail. Best and brightest users"
date: 2012-03-18
forum: General Help
---

### Post by jquis8411 on 2012-03-18
I deal with a program that spits out a lot of .txt files into a folder for these files. Each of these files, while encoded as .txt has a sequential number extension, foo.98, foo.97 etc. I need to find a way to print, for example line two of each of these files followed by the last eleven lines or even better the next five lines following a string on a line. For example, If line 56 has the characters "after this line is the data I need" the next five lines will be printed to a file. I have been working with this command  awk 'FNR==2 {print} FNR>=140 && FNR<=170 {print}'  foo.*  >  ~/output. I works as it should however the data I need to collect does not always wind up in lines 140-170.
The data I need to collect does always wind up in the last 11 lines in the file and is always the five lines following  a specific line (cut and pasted)" |                   delimiter offset                    |" .  Any ideas are appreciated . Thank you

---

### Post by HiImTye on 2012-03-18
print the last 11 lines of a file:
```
tail -11
```
print the lines following regex, but not regex
```
awk '/regex/{getline;print}'
```

---

### Post by jquis8411 on 2012-03-19
I have been playing with these commands for about an hour.:lolflag:  Either I cannot figure out the syntax or they just dont suit the need. If I tail then pipe into awk wont I just get the last 11 lines of the output of tail and have awk give the first two lines of that? What I really want to have happen is have the second line of each file in a folder that has the same prefix followed by the five lines after the words "delimiter offset" appear in a line of text. Thank you for the help

---

### Post by HiImTye on 2012-03-19
if you tail it then you will end up with whatever tail passes, but that doesnt mean you can't use multiple commands, i.e.
```
cat infile | awk 'NR==2' >> outfile
cat infile | tail -11 | awk '/\| delimiter offset \|/,0' >> outfile
```and you could script it like this:

```
cat $infile | awk 'NR==2' >> $outfile
cat $infile | tail -11 | awk '/\| delimiter offset \|/,0' >> $outfile
```which lets you play with the filenames outside of it while still getting the functionality you want

and if you want to make sure that you end up with a fresh file every time, replace the first >> with > i.e.
```
cat $infile | awk 'NR==2' > $outfile
cat $infile | tail -11 | awk '/\| delimiter offset \|/,0' >> $outfile
```

---

### Post by HiImTye on 2012-03-19
after re-reading your response, if you mean you want to name them based on the second line you could do something like this:

```
outfilename=$(cat $infile | awk 'NR==2')
cat $infile | tail -11 | awk '/\| delimiter offset \|/,0' >> $outfilename
```

---

