---
title: "help with awk (mutiple files)"
date: 2009-08-05
forum: General Help
---

### Post by guano on 2009-08-05
Hello all, if there is any awk guru out there to help me,I'd be really thankful.

I have three files:

file1:
495375|3877875|206.5650482178
495625|3877875|128.8113861084
495875|3877875|125.6818237305
496125|3877875|138.5249481201

file2:
495375|3877875|0.325424552
495625|3877875|0.498895824
495875|3877875|1.0152260065
496125|3877875|0.7567434907

file3:
495375|3878125|1675.7559814453
495625|3878125|1676.5754394531
495875|3878125|1677.4501953125
496125|3878125|1679.7961425781

As you can see, columns 1 and 2 are the same on all the files.

I want to parse these files with awk to get a new file with the third column of each one, like:

newfile:
206.5650482178 0.325424552 1675.7559814453
128.8113861084 0.498895824 1676.5754394531
125.6818237305 1.0152260065 1677.4501953125
138.5249481201 0.7567434907 1679.7961425781

any hints? I've been searching this, but awk is kinda weird for me..

many thanks

---

### Post by guano on 2009-08-05
Just so you know, so far I'm at this point:


```
awk  '
FILENAME==ARGV[1] { file_1_data[$1]=$0; next }
FILENAME==ARGV[2] { file_2_data[$1]=$0; next }
FILENAME==ARGV[3] { file_3_data[$1]=$0; next }
END {

for(i in file_1_data)
    for(j in file_2_data)
        for(k in file_3_data)
            split (file_1_data[i],a,"|")
            split (file_2_data[j],s,"|")
            split (file_3_data[k],e,"|")
            printf "%.2f %.2f %.1f\n", a[3], s[3], e[3]
}
' file1 file2 file3
```

and the output is this (a single line so far)

```
128.81 0.50 1677.5
```

If anyone can point out where I need to fix it so I get all the lines in the files...

---

