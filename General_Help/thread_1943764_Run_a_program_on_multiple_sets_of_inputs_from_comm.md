---
title: "Run a program on multiple sets of inputs from command line"
date: 2012-03-20
forum: General Help
---

### Post by orrymr on 2012-03-20
Hi (I hope I'm posting this thread in the right section)

I've written a program which takes as input a midi file and output multiple csv lines

I know in Bash I can do something like 
```
 touch test{0,1,2}
``` to create multiple files

The problem is that it doesn't seem to work when I do something like:
```

./myProgram midi{0,1,2,3,4} > output{0,1,2,3,4}

```Basically I want it to take in multiple midi files, and output multiple text files.

---

### Post by MG&amp;TL on 2012-03-20
You could do it with a for-loop or similiar. I'm just trying to think of a way of keeping the filenames unique. I think this one ends up with .midi.csv extension. 

```
for $files in *.midi; do ./myprogram > $files.csv
```

or you could do it in-program with a for-loop which iterates over stdin until done.

Somebody probably has  a better idea.

---

### Post by Vaphell on 2012-03-20
> I've written a program which takes as input a midi file and output multiple csv lines

1 midi = multiple csv files? so how does this work exactly? details would be nice because i have some trouble visualizing it.

---

### Post by orrymr on 2012-03-22
> **Vaphell said:**
> 1 midi = multiple csv files? 

1 midi = 1 csv file. That's what I'd like. At the moment If I run the program, it prints to stdout, which I then just redirect to a txt file.

All my midi files are similarly named: Beat0.mid, Beat1.mid....
and for each midi file I'd like to have a csv file corresponding to that midi file: data0.txt, data1.txt....

I'm just wondering how I'd do it so that I wouldn't have to type out many statements:
```

./myProgram Beat0.mid > data0.txt
./myProgram Beat1.mid > data1.txt
./myProgram Beat2.mid > data2.txt
.

```

---

### Post by Vaphell on 2012-03-25
for loop is your friend then

```
for **i** in {1..5}; do ./myProgram Beat**$i**.mid > data**$i**.txt; done
```

---

