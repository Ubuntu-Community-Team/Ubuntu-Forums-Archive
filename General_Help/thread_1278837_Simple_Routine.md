---
title: "Simple Routine"
date: 2009-09-30
forum: General Help
---

### Post by djmac on 2009-09-30
Hi all,

I think this is a relatively simple question . . . . I am trying to find a way to execute a series of commands in the terminal, sequentially. I just couldn't find anything anywhere.

 Basically, I am doing some modelling using gfortran, in conjunction with gnuplot. After I have modified the program, I compile it. Then I run it. Then I plot it. After this, I usually go back and modify the program. The three commands I have been using are:

```
user@user-terminal1:~$ gfortran /Programs.f90 -o RP1.2 
```
```
user@user-terminal1:~$ ./RP1.2 
```
```
user@user-terminal1:~$ gnuplot plot "output.dat"
```

They are just the three basic ones I am using . . .  there is a *heap* of other commands I want to use within GNUplot as well, but I figured I may as well keep it simple to start with. It is not that too much of a problem . . . it is just really repeatitive / frustrating to keep running through the same commands. I am sure there is a way to compile, run and plot in one simple action. Or at least I hope there is.

Thanks for any help

---

### Post by nikhilk on 2009-09-30
You could create a shell script (simple text file) that executes any number of commands. The contents of this script would be the commands you want to execute in that order, one on each line.

For the example you have mentioned you could create a script named compile_run_plot and its contents would be something like:
```

#!/bin/bash

cd "$HOME"
gfortran /Programs.f90 -o RP1.2
./RP1.2
gnuplot plot "output.dat"

exit 0

```
Save the file and make sure that it is executable, a simple "chmod u+x compile_run_plot" would do. Now whenever you run compile_run_plot, all the commands enumerated in that file will be executed.

---

### Post by pmlxuser on 2009-09-30
why not just write a bash script in your case the following would do
open gedit 
creat a files mytasks
```

#! /bin/bash
gfortran /Programs.f90 -o RP1.2  # run first command
./RP1.2 #run second
gnuplot plot "output.dat" # run third

```

then 
```
$ chmod +x mytasks
```

you can run the task sequencially by
```
$ ./mytasks 
```

---

### Post by djmac on 2009-09-30
Thanks guys! That has helped a lot.

 I am having problems with the final command . . .  I was a bit misleading with what I said earlier.

 Gnuplot is a command line program, so what I was actually doing was:

```
 user@user-terminal1:~$ gnuplot 
```

Followed by:

```
 gnuplot> plot "Output.dat" 
```

Is there anyway that it is possible to incorporate commands from gnuplot into a bash script? or is that asking too much?

 Thanks again!! Very much appreciated!

---

### Post by ownaginatious on 2009-09-30
> **djmac said:**
> Thanks guys! That has helped a lot.

 I am having problems with the final command . . .  I was a bit misleading with what I said earlier.

 Gnuplot is a command line program, so what I was actually doing was:

```
 user@user-terminal1:~$ gnuplot 
```

Followed by:

```
 gnuplot> plot "Output.dat" 
```

Is there anyway that it is possible to incorporate commands from gnuplot into a bash script? or is that asking too much?

 Thanks again!! Very much appreciated!

If gnuplot can accept command line arguments, it should be possible. Check the manpage for gnuplot.

---

### Post by mbeach on 2009-09-30
looking over
[http://linux.byexamples.com/archives/487/plot-your-graphs-with-command-line-gnuplot/](http://linux.byexamples.com/archives/487/plot-your-graphs-with-command-line-gnuplot/)

you may be able to create a gnuplot executable file instead of calling gnuplot.

create a text file with the first line
```
#!/usr/bin/gnuplot
```
then place in whatever commands you would normally type at the gnuplot prompt. Save the file and make it executable (the same sort of chmod +x commands above), then just call the newly created file in your bash script. Lets say you saved the file as mygnuplot.pg, then your bash file would like like:
```

#!/bin/bash

gfortran /Programs.f90 -o RP1.2  # run first command
./RP1.2 #run second
. mygnuplot.pg # run third

```
or something like that - you may need to tweak a bit.

Good luck.

---

### Post by Giblet5 on 2009-09-30
To supply input to ANY command, either from the shell prompt or from within a script (in this example, gnuplot):

```
#!/bin/sh

# Compile...
gfortran /Programs.f90 -o RP1.2

# Execute...
./RP1.2

# Plot...
gnuplot << !
plot Output.dat
!
```

The shell lets you redirect stdin (input stream) as easily as the output streams. The "<<" is followed by some *unique* string (some people use %, I use an exclamation mark). All subsequent text between the two occurrences of the unique character is treated as text typed on the keyboard.

It won't work on programs that flush the input stream at runtime (sudo etc) and it usually won't work on any program using cursor control (emacs, vi, etc) because they flush the input stream on startup.

The following script, MyRead, reads three lines, then spits them out in reverse order: ```
#!/bin/sh

read a
read b
read c
echo $c $b $a
```

Easy to see how that works, right?

Now we can execute this script from another script, supply its input, and manipulate its output: ```
#!/bin/sh

./MyRead << ! | sort
aaaaa
bbbbb
ccccc
!
```

This second script (it could just as easily be done from the command line) pushes input to the MyRead script and pushes that script's output through the sort command.

Aside from wasting a lot of time, there is a lot of useful stuff going on there.

---

### Post by djmac on 2009-09-30
> 
you may be able to create a gnuplot executable file instead of calling gnuplot

 That worked great!! (I had to add the gnuplot command, -persist, for gnuplot to remain open). 

So this is what I ended up with:

```
#!/bin/bash

cd "$HOME"
gfortran /Programs.f90 -o RP1.2     #Runs first command
./RP1.2                             #Runs second command
./mygnuplot                         #Runs gnuplot executable file

exit 0
```

And the gnuplot executable file was along the lines of:

```
#!/usr/bin/gnuplot -persist

plot "Output1.dat"
```

 . . .  and any number of addition gnuplot commands.

I also tried using "<<" . . . 

> The "<<" is followed by some *unique* string (some people use %, I use an exclamation mark).

 Unfortunately that didn't seem to work. Maybe gnuplot flushes the input at runtime. Not sure. Thanks anyway.

Thanks for all you help!! It has this so much easier / less frustrating!

---

