---
title: "Sorting text files?"
date: 2010-01-20
forum: General Help
---

### Post by Zeemvel on 2010-01-20
If I have a file test.txt, and I type this:

sort test.txt > blah.txt

Then blah.txt contains the sorted version of test.txt

However if I type this:

sort test.txt > test.txt

Then I get an empty file (0kb) as a result! I'd like to sort text files without ending up with two files though...

Why is the result of the second 0kb instead of a sorted version of the file?

How can I sort a file anyway, and even better, how can I sort a whole series of text files (all having the same extension) at once with a single command? I mean if I'd have a.txt, b.txt, c.txt, etc... then the result would be that these 3 files are each a sorted version of itself.

Thanks!

---

### Post by lotharmat on 2010-01-20
sort test.txt > blah.txt & rm test.txt

---

### Post by wojox on 2010-01-20
Something like this:

```
sort files > files.sorted
```

which creates a new file named files.sorted, which contains the new, sorted output.

---

### Post by Zeemvel on 2010-01-20
> **wojox said:**
> Something like this:

```
sort files > files.sorted
```which creates a new file named files.sorted, which contains the new, sorted output.

By files, do you mean multiple files?

---

### Post by John Bean on 2010-01-20
> **Zeemvel said:**
> Why is the result of the second 0kb instead of a sorted version of the file?

Because the output file is initialised to zero size when the redirection is set up by the shell before the sort otherwise there would be nowhere to write the result.

If you want to appear to sort the data "in place" you'll need to use a copy; I'd probably do:
```
cp test.txt temp && sort temp > test.txt ; rm temp
```

---

### Post by Zeemvel on 2010-01-20
I'm going to have to sort a lot of files, does anyone know a way that doesn't involve typing the name of the file twice in the command? I'm just looking for an efficient way to do it before starting the monkey work :)

---

### Post by John Bean on 2010-01-20
> **Zeemvel said:**
> I'm going to have to sort a lot of files, does anyone know a way that doesn't involve typing the name of the file twice in the command? I'm just looking for an efficient way to do it before starting the monkey work :)

Using the same example:```
f=test.txt; cp $f temp && sort temp > $f ; rm temp
```

If they're all .txt files you can use a loop and do it automatically. You may need quotes around the filenames if they include spaces or other special characters.

---

### Post by wojox on 2010-01-20
wait

---

### Post by KeLa on 2010-01-20
You can try to play with find command like this...

find ~/test/ -type f -name "*.txt" -exec ... {} \;

or similar. if you want one line command or you can use
that find command to redirect filenames to script file and adding sort commands to it
at same time and then running that script file

---

### Post by wojox on 2010-01-20
Drank to many white Russians tonight. try this

```
find . -name "*.txt"  > files.txt
```

---

### Post by kaibob on 2010-01-20
> **John Bean said:**
> If they're all .txt files you can use a loop and do it automatically. You may need quotes around the filenames if they include spaces or other special characters.

The following shell script is an example of the loop that John Bean is referring to. It operates on all TXT files in the current directory. 

```
#!/bin/bash

for file in *.txt ; do
   sort "$file" > temp.txt
   mv temp.txt "$file"
done
```

This shell script is easily converted to a one-liner if you don't want to fool with a shell script:

```
for file in *.txt ; do sort "$file" > temp.txt ; mv temp.txt "$file" ; done
```

BTW, at least initially, be sure to work with copies of the source files until you have things sorted out.

---

### Post by falconindy on 2010-01-20
You can sort files in place by passing commands to vim as args:

```
for file in *.txt; do vim $file +:%\!sort +:x; done
```

Someone who knows Vim better than I do might be able to do this without a for loop, but I couldn't figure out how to get Vim to act across multiple open files.

---

