---
title: "produce graph from top linux value"
date: 2010-06-04
forum: General Help
---

### Post by el_fiqs on 2010-06-04
[FONT=Tahoma][SIZE=2]hello..
i'm using top in linux to read the performance for memory,cpu and so on.
if i would like to generate a graph from the top values for memory for 1 minute, how to do that?
please help me..[/SIZE][/FONT]

---

### Post by StuartN on 2010-06-04
```
top -b -d 1 -n 60 > top.out
```

This will run top in batch mode, updating every second, for 60 seconds, and send the output to a (big) file top.out.

You might want to check the commandline options or to save a /etc/toprc or ~/.toprc to configure the output.

---

### Post by el_fiqs on 2010-06-04
[FONT=Courier New][SIZE=2]thanks, but your command is to save the top values. how to produce a graph from the saved file before?[/SIZE][/FONT]

---

### Post by StuartN on 2010-06-04
> **el_fiqs said:**
> how to produce a graph from the saved file before?

I would convert it to CSV (using grep and sed) and open it in the statistical package R, but that is overkill - I assumed from your original question that you needed to know how to save the data. You could try OpenOffice Calc or some other package that has numeric graphing.

(Why doesn't System -> Administration -> System Monitor work?)

---

### Post by el_fiqs on 2010-06-04
[FONT=Courier New][SIZE=2]the system monitor data is not enough for my project. what is CSV?
[/SIZE][/FONT]

---

### Post by StuartN on 2010-06-04
> **el_fiqs said:**
> [FONT=Courier New][SIZE=2]the system monitor data is not enough for my project. what is CSV?
[/SIZE][/FONT]

CSV is comma-separated values, a fairly standard way of passing tabular data between applications. The output from top can not be graphed directly, so you will need to convert it into useable separate values.

For example, the following (incomplete) command would retrieve the Cpu statistics and convert to comma-separated values:

```
cat top.out | grep "Cpu(s):" | sed -e "s/Cpu(s): //" -e "s/%us//" ...
```

---

### Post by el_fiqs on 2010-06-04
[FONT=Courier New][SIZE=2]ohh.. i got some idea but still blur.
can you give me the full command from the example for the cpu that you gave just now?
i can modify it when i understand it[/SIZE][/FONT]

---

### Post by StuartN on 2010-06-04
> **el_fiqs said:**
> [FONT=Courier New][SIZE=2]ohh.. i got some idea but still blur.
can you give me the full command from the example for the cpu that you gave just now?
i can modify it when i understand it[/SIZE][/FONT]

```
cat top.out | grep "Cpu(s):" | sed -e "s/Cpu(s): //" -e "s/%us//" ...
```

The command grep locates just the lines containing "Cpu(s): ".

The command sed replaces patterns, so sed -e "s/Cpu(s):\//" substitutes "Cpu(s): " with nothing, -e "s/%us//" substitutes "%us" with nothing, etc. You need to add the remaining patterns to convert:

```
From:
  Cpu(s): 15.7%us,  4.7%sy,  2.1%ni, 70.7%id,  6.4%wa,  0.2%hi,  0.1%si,  0.0%st
To:
  15.7, 4.7, 2.1, ...
```

---

### Post by el_fiqs on 2010-06-04
[SIZE=2][FONT=Courier New]thanks for the guide, i'll try it. :)[/FONT][/SIZE]

---

### Post by el_fiqs on 2010-06-05
StuartN, please help me.

i av include screenshot of the top in the attachment. i want only memory usage for the Snort or PID number 5922 only. how to grab the data?

please help :confused:

---

### Post by StuartN on 2010-06-05
> **el_fiqs said:**
> i want only memory usage for the Snort or PID number 5922 only. how to grab the data?

If there is only one copy of Snort running, then this would generate a list of numbers, one per line, for the memory usage (the eleventh field, counting a blank at the start of the line) at each second for 60 seconds:

```
top -b -d 1 -n 60 | grep Snort | tr -s " " "\t" | cut -f 11
```

---

### Post by el_fiqs on 2010-06-06
StuartN, i have try this code :

top -b -d 1 -n 60 | grep Snort | tr -s " " "\t" | cut -f 11

but i did not get the output? where is the output? :confused:

---

### Post by StuartN on 2010-06-07
> **el_fiqs said:**
> where is the output? :confused:

Why not **top -b -d 1 -n 60 > top.out** to check what it is that you want to select, and then **cat top.out | grep ...**?

---

