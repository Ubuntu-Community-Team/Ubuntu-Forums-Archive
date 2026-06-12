---
title: "Grep + scripting? Need guidance (general linux)"
date: 2010-02-17
forum: General Help
---

### Post by Strid on 2010-02-17
Hi!

I have a queue system running across 7 nodes with each 8 cores.

When I want to see how many cores are currently available, I usually type the command, and I get a number of CPUs running for each job.

```

[strid@fruitcluster ~]$ qstat -f | grep "ppn"
    Resource_List.nodes = 1:ppn=4
    Resource_List.nodes = 1:ppn=4
    Resource_List.nodes = 1:ppn=4
    Resource_List.nodes = 1:ppn=2
    Resource_List.nodes = 1:ppn=4
    Resource_List.nodes = 1:ppn=2
    Resource_List.nodes = 1:ppn=2
    Resource_List.nodes = 1:ppn=2
    Resource_List.nodes = 1:ppn=2
    Resource_List.nodes = 1:ppn=1
    Resource_List.nodes = 1:ppn=2
    Resource_List.nodes = 1:ppn=1
    Resource_List.nodes = 1:ppn=1
    Resource_List.nodes = 1:ppn=1
[strid@fruitcluster ~]$ 

```

My end goal is to make a shell script, that outputs only the number of available cores, i.e. sums up the last number of each grep line and subtracts it from 56 (the total number of cores) and displays. 

Any ideas on how to treat the output (esp. the last char) of grep as an integer in a shell script?

Thanks, Andy

---

### Post by dcstar on 2010-02-18
> **Strid said:**
> Hi!

I have a queue system running across 7 nodes with each 8 cores.

When I want to see how many cores are currently available, I usually type the command, and I get a number of CPUs running for each job.

```

[strid@fruitcluster ~]$ qstat -f | grep "ppn"
    Resource_List.nodes = 1:ppn=4
    Resource_List.nodes = 1:ppn=4
    Resource_List.nodes = 1:ppn=4
    Resource_List.nodes = 1:ppn=2
    Resource_List.nodes = 1:ppn=4
    Resource_List.nodes = 1:ppn=2
    Resource_List.nodes = 1:ppn=2
    Resource_List.nodes = 1:ppn=2
    Resource_List.nodes = 1:ppn=2
    Resource_List.nodes = 1:ppn=1
    Resource_List.nodes = 1:ppn=2
    Resource_List.nodes = 1:ppn=1
    Resource_List.nodes = 1:ppn=1
    Resource_List.nodes = 1:ppn=1
[strid@fruitcluster ~]$ 

```

My end goal is to make a shell script, that outputs only the number of available cores, i.e. sums up the last number of each grep line and subtracts it from 56 (the total number of cores) and displays. 

Any ideas on how to treat the output (esp. the last char) of grep as an integer in a shell script?

Thanks, Andy

```
man cut
```

---

### Post by Strid on 2010-02-18
Thanks! I got the problem solved. I did a python script instead of a shell script.

---

### Post by woodmaster on 2010-02-18
maybe you could post some script details and mark it solved for others?

---

### Post by Strid on 2010-02-18
Great idea! ;)

So it's a three file solution. First I execute the command and grep the lines I want and pipe the output into a file called 'ncpus.txt'

```
qstat -f | grep 'ppn' > ncpus.txt
python ncpus.py

```

Then I have a tiny Python scrip that reads the 32rd character of each line in the file (which is the number I want to extract) and converts to an integer.

```

data = open("ncpus.txt") #opens pdb file in read mode

line = data.readlines()



m = 0


for i in line:

    n = int(i[32])
 #make an integer of character 32 of the line
    m = m + n

print "Number of available CPU cores: ", 48 - m

```

---

