---
title: "Need help with ls filename &gt;&gt; text file"
date: 2010-12-13
forum: General Help
---

### Post by darkcoffee on 2010-12-13
I want to write the filename list into a text file.  But each filename has to be written twice on the same line. 
   ```
ls  
file1  
file2  
file3
```  must look like  
```
file1 file1  
file2 file2 
file3 file3
```when I open the text file.  How can this be done?

---

### Post by gmargo on 2010-12-13
See the **paste(1)** command.
```

$ ls > ls.out
$ paste ls.out ls.out > combined.out

```

---

### Post by rubylaser on 2010-12-13
Or, you could do it like this assuming your files are in a folder named test

```
#! /bin/bash
#Cleanup old version
rm ls.out
#Make new file
touch ls.out
ls ~/test |
while read filename
do
   echo $filename $filename >> ~/ls.out
done
```

Outputs this...
```
file1 file1
file2 file2
file3 file3

```

Although the above solution is definitely shorter and easier to execute.

---

### Post by Slim Odds on 2010-12-13
I love this little bash shell exercises... you get 20 different ways to do it ;)

```

#! /bin/bash
#Cleanup old version
rm ~/ls.out
for f in `command ls -1`; do
    echo $f $f >> ~/ls.out
done
```Note: if you have filenames with spaces, this will need to be modified to handle those

---

### Post by sisco311 on 2010-12-13
@Slim Odds

One should use globs:
```
for file in *; do
```

See: [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)


paste one liner:
```
paste <(ls) <(ls) > file
```

sed:
```
ls | sed 's/\(.*\)/\1\t\1/' > file
```

---

### Post by Slim Odds on 2010-12-13
ls without the -1 parameter produces a lot more than just a filename

---

