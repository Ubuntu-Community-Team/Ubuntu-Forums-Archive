---
title: "Shell Script for Running a Program Multiple Times"
date: 2010-07-26
forum: General Help
---

### Post by shouraku on 2010-07-26
Hello everyone,

I am having an issue that I am hoping someone may be able to assist me with (sorry if I posted this in the wrong place, but I am not sure if it qualifies as an absolute beginner question or not):

I have many plots to make (thousands). For each plot I have a gnuplot file containing the appropriate commands and data. Now I know how to generate one plot (terminal command):

```
gnuplot "example_1.gp"
```

But as I said, I have thousands to make. Thus I was wondering if anyone could assist me in making a shell scrip that would let me run the above command for all the files I need processed.

Note: Originally I thought that I could just make a list as an output of a related program that I wrote to print:

```
gnuplot "example_1.gp"
gnuplot "example1_2.gp"
gnuplot "example1_3.gp"
gnuplot "example1_4.gp"
..........
```

to a text file. I figured that I could then just copy the above list and paste it to the terminal. Which seems not to work (does not process every line). However, I do have this lovely list if it will be of any help. 

Could I just add a command to the beginning of the list to indicate that I want each line in the list to be run as if I had manually entered it into the terminal (make it into a shell script)?

Thank you for your time,

Shouraku

---

### Post by RiceMonster on 2010-07-26
You mean something like this?

```
#!/bin/bash

for i in 1..4
do
    gnuplot "example_$i.gp"
done
```

Change the range to suite your needs/

---

### Post by shouraku on 2010-07-26
That is great, however, I may need to be more specific.

The files are not labeled as simply as example_1,example_2, etc.

In other words, they contain names that are to dissimilar for that method to work.

But thank you anyway, If all else fails, I can rewrite my program to give them more simple names.

---

### Post by nmaster on 2010-07-26
would this work?
```

#!/bin/bash

for i in $@ ; do
    gnuplot "$i"
done

```
then give the script the filenames as arguments

---

### Post by phatqao on 2010-07-26
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

check it out

---

### Post by shouraku on 2010-07-26
Maybe I need to give a part of the list so that it is more apparent why this is an issue:

```

gnuplot "SN2_u.gp"
gnuplot "SN2_g.gp"
gnuplot "SN2_r.gp"
gnuplot "SN2_i.gp"
gnuplot "SN2_z.gp"
gnuplot "SN2_redshift.gp"
gnuplot "SN3_u.gp"
gnuplot "SN3_g.gp"
gnuplot "SN3_r.gp"
gnuplot "SN3_i.gp"
gnuplot "SN3_z.gp"
gnuplot "SN3_redshift.gp"

```

As you can see, the naming convention used in the files is the issue. Basically, there is more then one file for each Supernova (6 bands to be exact).

Thank you phatqao, but I have already been there (for a good long time). Unfortunately, my skills are novice enough to where I am unable to find the solution in the given text (it may very well be there, I just don't know enough to be able to identify it).

Can I assume that there would be nothing wrong with:

```
#!/bin/bash

for i in 2..300
do
    gnuplot "SN$i_u.gp"
    gnuplot "SN$i_g.gp"
    gnuplot "SN$i_r.gp"
    gnuplot "SN$i_i.gp"
    gnuplot "SN$i_z.gp"
    gnuplot "SN$i_redshift.gp"
done
```

?

---

### Post by nmaster on 2010-07-26
use the script that i posted above.  put in a file called script.sh (call it whatever you want) then move it along with all the files into a new directory.  then do this:
```

cd /path/to/the/new/directory
chmod +x script.sh
./script.sh *.gp

```

---

### Post by apmcd47 on 2010-07-26
> **shouraku said:**
> Maybe I need to give a part of the list so that it is more apparent why this is an issue:

```

gnuplot "SN2_u.gp"
gnuplot "SN2_g.gp"
gnuplot "SN2_r.gp"
gnuplot "SN2_i.gp"
gnuplot "SN2_z.gp"
gnuplot "SN2_redshift.gp"
gnuplot "SN3_u.gp"
gnuplot "SN3_g.gp"
gnuplot "SN3_r.gp"
gnuplot "SN3_i.gp"
gnuplot "SN3_z.gp"
gnuplot "SN3_redshift.gp"

```

As you can see, the naming convention used in the files is the issue. Basically, there is more then one file for each Supernova (6 bands to be exact).




If you want to plot them in that order try this:
```
#!/bin/sh
for i in "$@" 
do
   for j in u g r i z redshift
   do
      gnuplot "$i_$j.gp"
   done
done

```
and call it something like "novaplot". Now you can invoke it like:
```
novaplot SN2
```
or
```
novaplot SN2 SN3
```

Andrew

---

### Post by shouraku on 2010-07-26
Thank you neal.m.master. That was exactly what I needed.

And thank you all for your assistance. You really got me out of a bind!

---

### Post by nmaster on 2010-07-26
> **shouraku said:**
> Thank you neal.m.master. That was exactly what I needed.

And thank you all for your assistance. You really got me out of a bind!

score! i win! i helped someone with a problem! lol, it actually makes me feel good to know enough to be able to aid others. :)

you should really learn more about bash scripting though.  as you now know, its *very* useful.  it might go a bit slowly at first because the syntax is so different from many other programming languages, but once you get past that its easy to pick up new things.

---

### Post by shouraku on 2010-07-27
> **nmaster said:**
> score! i win! i helped someone with a problem! lol, it actually makes me feel good to know enough to be able to aid others. :)

you should really learn more about bash scripting though.  as you now know, its *very* useful.  it might go a bit slowly at first because the syntax is so different from many other programming languages, but once you get past that its easy to pick up new things.

You should feel good, you really got me out of a difficult spot!

And, you are correct, bash scripting is one of those things that I never really got around to learning even though I was aware of its usefulness. No time like the present to begin.

Thank you again :D

---

