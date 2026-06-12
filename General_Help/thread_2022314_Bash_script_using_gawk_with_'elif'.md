---
title: "Bash script using gawk with 'elif'"
date: 2012-07-10
forum: General Help
---

### Post by telemaster on 2012-07-10
Hello,


I have been trying to write my first bash script. Its purpose is to read through large output files using a combo of gawk commands and select relevant results from the waffle. 

Here is the script in its present from:

#!/bin/bash
x=0
  while [get line !=0]
      do
        temp=gawk 'NR==x , NR==x+1' FeMnPO4.out
        FIRST= `$temp | gawk 'NR==1'`
        SECOND= `$temp | gawk 'NR==2'`                                     
        if [ $FIRST | gawk '/DAV/' {print $0} > filter.out && $SECOND | gawk '/DAV/' {printf $0} > filter.out ] ;then
        elif [ $FIRST | gawk '/DAV/' {printf $0} > filter.out && $SECOND | gawk '! /DAV/' {print $0 print "\n"} > filter.out] ;then 
        elif [ $FIRST | gawk '! /DAV/' {print "\\n"\} > filter.out && $SECOND | gawk '/DAV/' {printf $0} > filter.out ] ; then
          
        fi 
        ((x +=2))
      done
\f1 

I am not sure about the f1 at the end, I think this may have been inserted by the defaults on one of the editors i have been using. 
Also, I am not sure i can use get line  like above.

But the main problem is the error messages I can't overcome:

[mw2a11@blue33 One_Mn]$ ./control_edit.sh
./control_edit.sh: line 9: syntax error near unexpected token `elif'
./control_edit.sh: line 9: `        elif [ $FIRST | gawk '/DAV/' {printf $0} > filter.out && $SECOND | gawk '! /DAV/' {print $0 print "\n"} > filter.out] ;then '

i imagine that perhaps I have a misconception about using 'elif'- I've kind of blagged it, this is my first script.

BTW I am compiling this in a MAC terminal, in case that's relevant (maybe its critical!)

Please point me to the solution if its obvious!

---

### Post by Vaphell on 2012-07-10
could you wrap the code with ```
[/co****de] tags to make it easier on the eyes?

if goes like this:
[code]if <condition 1>; then
  <stuff to do>
elif <condition 2>; then
  <stuff to do>
else
  <stuff to do>
fi
```
your script lacks 'then' blocks and goes straight to elif, hence 'unexpected elif'

what is your script supposed to do? because it's rather fugly and i see you have fallen in love with awk ;-)

---

### Post by papibe on 2012-07-10
> **vaphell said:**
> could you wrap the code with [code][/co****de] tags to make it easier on the eyes?

+1

---

### Post by telemaster on 2012-07-11
```
#!/bin/bash
x=0
while [get line !=0]
do
temp=gawk 'NR==x , NR==x+1' FeMnPO4.out
FIRST= `$temp | gawk 'NR==1'`
SECOND= `$temp | gawk 'NR==2'`
if [ $FIRST | gawk '/DAV/' {print $0} > filter.out && $SECOND | gawk '/DAV/' {printf $0} > filter.out ] ;then
elif [ $FIRST | gawk '/DAV/' {printf $0} > filter.out && $SECOND | gawk '! /DAV/' {print $0 print "\n"} > filter.out] ;then
elif [ $FIRST | gawk '! /DAV/' {print "\\n"\} > filter.out && $SECOND | gawk '/DAV/' {printf $0} > filter.out ] ; then

fi
((x +=2))
done
```


Is this what you meant by wrapping the code?

@Vaphell:So yes, I see I have nothing by way of 'then' commands, sure. The actions that I want to be taken are the 'action' parts of the GAWK statements within the for loop. Gawk by default takes the action of printing if it finds a match, right? So how can I prevent gawk itself from doing something?

The idea behind the whole program, is that gawk will read in two lines at a time- then there are two variables 'FIRST' and 'SECOND' that are assigned to the first and second lines. 
The various gawk statements test if each of the two lines have the pattern i'm after- 'DAV'- if the first line contains DAV, this will be printed by gawk, but if the second line happens to be the end of a long line of 'DAV' lines in the original file, so that it contains no DAV, a blank line will be printed-
so I get columns of the results I want neatly separated in an out file.
It seems there must be a more elegant way of accomplishing this, i take your point! I couldn't think of another way of controlling the input to gawk in pairs of lines.

---

### Post by papibe on 2012-07-11
> **telemaster said:**
> Is this what you meant by wrapping the code?

Nope. I edited it for you. For future reference take a look at the Code section [here]("http://ubuntuforums.org/misc.php?do=bbcode"). 

Regards.

---

### Post by codemaniac on 2012-07-11
> **telemaster said:**
> Hello,


I have been trying to write my first bash script. Its purpose is to read through large output files using a combo of gawk commands and select relevant results from the waffle. 



Hi telemaster ,

There are cool and efficient ways to read through large text files .Can you please post a snippet of your large file you want to read , and what exactly you want to chunk out for  the file ?

---

### Post by Vaphell on 2012-07-11
you seriously overengineered it with that awk everywhere, but it's understandable as your toolbox is still small. As they say - if the only tool you got is a hammer, everything starts to look like a nail ;-)

philosophy aside - you should aim to do everything on a single pass.
You can use modulo arithmetic to work with pairs of rows, eg let's say you have data like this
```
$ echo $'r1\nr2\nr3\nr4'
r1
r2
r3
r4
```
awk with modulo arithmetic gluing pairs of rows together
```
$ echo $'r1\nr2\nr3\nr4' | awk 'NR%2==1 { printf("%s\t", $0); }; NR%2==0{ print $0; }'
r1	r2
r3	r4
```
you can mix it with other conditions eg

```
$ echo $'r1\nr2\nr3\nr4' | awk [COLOR="DarkGreen"]'NR%2==1 && !/r1/{ printf("%s\t", $0); };[/COLOR][COLOR="Blue"] NR%2==1 && /r1/ { printf("[%s]\t", $0 ); };[/COLOR] NR%2==0{ print $0; }'
[COLOR="Blue"][r1][/COLOR]	r2
[COLOR="DarkGreen"]r3[/COLOR]	r4
```

---

### Post by telemaster on 2012-07-11
@ Vaphell:


Ah, so now I see how easy it is to group the input to gawk into pairs- thank you for pointing this out. But is there a way to have a gawk command where the action taken depends on two separate lines meeting different conditions? 

eg,

 awk  '(NR%2==1 && /DAV/) && (NR%2==0 && !/DAV/) {'action'}

in the above, i intend gawk to take action if, the first condition is true when it reads the first line, and then the second condition when it reads the second line. But if i have understood the literature correctly, gawk reads lines on at a time- so I can't apply this whole control sequence to a single gawk statement like above..or can I?

---

### Post by steeldriver on 2012-07-11
it sounds like you might want to do something stateful

- when condition #1 is met, go into a state where you test for condition #2

- when condition #2 is met in state #1, do action and then set state back to 0 

Here's an outline to get you started:

```
BEGIN {dav_state = 0;} 

{  if (*condition #1*) dav_state = 1; }

{  if (dav_state == 1)
    { if (*condition #2*)
        *do action *;
        dav_state = 0; }
}

```

---

### Post by Vaphell on 2012-07-11
> so I can't apply this whole control sequence to a single gawk statement like above..or can I?

you can use variables to transmit information between blocks of code

```
$ echo $'r1\nr2\nr3\nr4' | awk 'NR%2==1 && !/r1/{ x=0; first=$0; };
                                NR%2==1 && /r1/ { x=1; first=$0; };
                                NR%2==0 && x>0 { printf("x=1:\t[%s]\t%s\n",first,$0); };
                                NR%2==0 && x==0 { printf("x=0:\t%s\t%s\n",first,$0); }'
x=1:	[r1]	r2
x=0:	r3	r4
```

you can use *if else* inside the blocks.

---

### Post by telemaster on 2012-07-11
Right. Have been taking inspiration from the posts above, and this has led me to a nearly working new script:

```

#!/bin/bash
exec 1< FeMnPO4.out
x=0
a=5
  while [ read -u1 line ]
      do
        $line | awk 'NR%2==1 && /DAV/ { x=1; first=$0; };
                           NR%2==1 && !/DAV/  { x=0; first=$0; };
                           if (NR%2==0 && x>0 && /DAV/); then { printf(first\n, $0); };
                           elif (NR%2==0 && x>0 && !/DAV/); then { printf(first\n, "\n", $a, "\n");};             ((a +=5))
                           elif (NR%2==0 && x==0 && /DAV/); then {printf($0);};
                           else
                           fi'
      done

```

However I still get this error:

./control_edit.sh: line 5: [: -u1: binary operator expected

This I am mystified by as I thought giving an integer to the -u option is giving the binary operator!

sorry again for the lack of code box, not sure why it hasn't appeared...

---

### Post by Vaphell on 2012-07-11
```
 with the other slash (/)
could you give a sample of input data and expected output?

[code]while [ <condition> ]; do ...
```
but
```
while read var; do  ...
```

besides you are supposed to mow through the file with awk only. eg
```
awk '<magic>' FeMnPO4.out
```

now it's an ungodly mixture of bash and awk syntax.

---

### Post by telemaster on 2012-07-12
Hi Vaphell. So there is something wrong with my syntax in the 'while' condition? if I need to be 'piping' the whole of my file FeMnPO4.out to awk, don't I need some kind of while, or for loop, which ends when the EOF is reached? This is what i was aiming for...

The FeMnPO4.out file i want to process is like this:

```


a=10
 running on   24 nodes
 distr:  one band on    1 nodes,   24 groups
 vasp.4.6.35 3Apr08 complex 
 POSCAR found :  5 types and   28 ions
 LDA part: xc-table for Pade appr. of Perdew
 generate k-points for:   1   2   2
 found WAVECAR, reading the header
  number of k-points has changed, file:  12 present:   4
  trying to continue reading WAVECAR, but it might fail
 POSCAR, INCAR and KPOINTS ok, starting setup
 WARNING: wrap around errors must be expected
 FFT: planning ...           1
 reading WAVECAR
 the WAVECAR file was read sucessfully
 initial charge from wavefunction
 entering main loop
       N       E                     dE             d eps       ncg     rms          rms(c)
DAV:   1    -0.204026237123E+03   -0.20403E+03   -0.18291E+03   984   0.118E+02BRMIX: very serious problems
 the old and the new charge density differ
 old charge density:   151.37063 new  150.99994
    0.546E+01
DAV:   2    -0.604596210633E+03   -0.40057E+03   -0.37179E+03  1344   0.228E+02    0.979E+01
DAV:   3    -0.266614088913E+03    0.33798E+03   -0.18894E+02  1056   0.134E+02    0.789E+01
DAV:   4    -0.217399490890E+03    0.49215E+02   -0.11627E+02  1152   0.529E+01    0.638E+01
DAV:   5    -0.250396709235E+03   -0.32997E+02   -0.45125E+02  1248   0.102E+02    0.632E+01
DAV:   6    -0.240046042204E+03    0.10351E+02   -0.38241E+01  1176   0.174E+01    0.589E+01
DAV:   7    -0.219424118109E+03    0.20622E+02   -0.40778E+00  1056   0.227E+01    0.556E+01
DAV:   8    -0.198369808501E+03    0.21054E+02   -0.18271E+01  1248   0.220E+01    0.518E+01
DAV:   9    -0.191990760382E+03    0.63790E+01   -0.13628E+01  1248   0.849E+00    0.237E+01
DAV:  10    -0.190759461090E+03    0.12313E+01   -0.25854E+01  1200   0.129E+01    0.156E+01
DAV:  11    -0.190001589232E+03    0.75787E+00   -0.38976E+00  1152   0.496E+00    0.132E+01
DAV:  12    -0.189784057547E+03    0.21753E+00   -0.41088E-01  1248   0.225E+00    0.101E+01
DAV:  13    -0.189760793016E+03    0.23265E-01   -0.44245E-02  1224   0.103E+00    0.961E+00
DAV:  14    -0.189810309477E+03   -0.49516E-01   -0.27042E-02  1248   0.752E-01    0.986E+00
DAV:  15    -0.189840938501E+03   -0.30629E-01   -0.97009E-02  1248   0.155E+00    0.930E+00
DAV:  16    -0.189810323660E+03    0.30615E-01   -0.73630E-02  1248   0.712E-01    0.781E+00
DAV:  17    -0.190012068885E+03   -0.20175E+00   -0.70796E-01  1248   0.305E+00    0.985E+00
DAV:  18    -0.190022436502E+03   -0.10368E-01   -0.83513E-02  1248   0.104E+00    0.829E+00
DAV:  19    -0.189899399359E+03    0.12304E+00   -0.67052E-01  1344   0.212E+00    0.492E+00
DAV:  20    -0.189861068520E+03    0.38331E-01   -0.37349E-02  1248   0.962E-01    0.400E+00
DAV:  21    -0.189842868097E+03    0.18200E-01   -0.61036E-02  1224   0.109E+00    0.291E+00
DAV:  22    -0.189826045150E+03    0.16823E-01   -0.13857E-01  1224   0.138E+00    0.234E+00
DAV:  23    -0.189812611200E+03    0.13434E-01   -0.15675E-02  1128   0.613E-01    0.176E+00
DAV:  24    -0.189808532328E+03    0.40789E-02   -0.30548E-02  1224   0.675E-01    0.152E+00
DAV:  25    -0.189801779464E+03    0.67529E-02   -0.84415E-03  1224   0.387E-01    0.956E-01
DAV:  26    -0.189797468068E+03    0.43114E-02   -0.22904E-02  1224   0.753E-01    0.425E-01
DAV:  27    -0.189801000198E+03   -0.35321E-02   -0.17018E-02  1224   0.416E-01    0.126E+00
DAV:  28    -0.189798294184E+03    0.27060E-02   -0.77359E-03  1176   0.297E-01    0.618E-01
DAV:  29    -0.189798665532E+03   -0.37135E-03   -0.10540E-03   792   0.170E-01    0.772E-01
DAV:  30    -0.189797219302E+03    0.14462E-02   -0.51218E-03   984   0.224E-01    0.249E-01
DAV:  31    -0.189797360417E+03   -0.14111E-03   -0.34466E-04   768   0.115E-01    0.215E-01
DAV:  32    -0.189797236728E+03    0.12369E-03   -0.33001E-04   552   0.856E-02    0.109E-01
DAV:  33    -0.189797212749E+03    0.23979E-04   -0.33471E-04   720   0.788E-02
   1 F= -.18979721E+03 E0= -.18980505E+03  d E =0.235043E-01
 writing wavefunctions
a=15
 running on   24 nodes
 distr:  one band on    1 nodes,   24 groups
 vasp.4.6.35 3Apr08 complex 
.............

```


I want to get the results separated by spaces, and with the value of the variable 'a' that each block refers to, i.e

```

a=10

DAV:   1    -0.204026237123E+03   -0.20403E+03   -0.18291E+03   984   0.118E+02BRMIX: very serious problems
 the old and the new charge density differ
 old charge density:   151.37063 new  150.99994
    0.546E+01
DAV:   2    -0.604596210633E+03   -0.40057E+03   -0.37179E+03  1344   0.228E+02    0.979E+01
DAV:   3    -0.266614088913E+03    0.33798E+03   -0.18894E+02  1056   0.134E+02    0.789E+01
DAV:   4    -0.217399490890E+03    0.49215E+02   -0.11627E+02  1152   0.529E+01    0.638E+01
DAV:   5    -0.250396709235E+03   -0.32997E+02   -0.45125E+02  1248   0.102E+02    0.632E+01
DAV:   6    -0.240046042204E+03    0.10351E+02   -0.38241E+01  1176   0.174E+01    0.589E+01
DAV:   7    -0.219424118109E+03    0.20622E+02   -0.40778E+00  1056   0.227E+01    0.556E+01

a=15

DAV:   1    -0.190029863498E+03   -0.19003E+03   -0.24201E+02   984   0.436E+01BRMIX: very serious problems
 the old and the new charge density differ
 old charge density:   151.03955 new  150.99994
    0.342E+01
DAV:   2    -0.362078544005E+03   -0.17205E+03   -0.17807E+03  1320   0.165E+02    0.795E+01
DAV:   3    -0.265385807283E+03    0.96693E+02   -0.78630E+02  1224   0.943E+01    0.643E+01
DAV:   4    -0.216787400979E+03    0.48598E+02   -0.93814E+01  1080   0.787E+01    0.489E+01
DAV:   5    -0.213548949296E+03    0.32385E+01   -0.50826E+01  1248   0.246E+01    0.511E+01

a=20

....

```

In the above, i do not care about any text within blocks of DAV, so my program ignores it.

---

### Post by Vaphell on 2012-07-12
awk handles files by itself, it doesn't need additional loop.

**awk '<stuff>' file** will go line by line (or should i say record by record) to the very end without any external help.

**while read line** is used when you manipulate things in bash, you have $line variable in hand and you work on it with other tools.
Of course you can mix these two but this example doesn't look like it's necessary. It should be a rather straightforward job for awk.

about **if**
**if** in bash has different syntax than if in awk
bash if goes like this: ```
if <condition>; then ...; elif <condition>; then ...; else ...; fi
```
awk if is like if in C language: ```
if( <condition> ) { ... } else { ... }
```


edit: try this
```
awk ' BEGIN { a=""; }
      /^a=/             { print a$0"\n"; a="\n"; dav=0; };
     !/DAV/ && dav==0   { };
     !/DAV/ && dav>1    { };
     !/DAV/ && dav==1   { print $0; };
      /DAV/             { print $0; dav++; };' FeMnPO4.out
```

---

### Post by steeldriver on 2012-07-12
or how about

```
awk 'BEGIN { dav_state = 0; } { if ($1 ~ /a=[0-9]+/) print $1; } { if ($1 ~ /DAV/) dav_state = 1 } { if (dav_state == 1) if ($1 !~ /DAV/) dav_state = 0; else print $0 }' *yourfile*
```

---

### Post by telemaster on 2012-07-12
Vaphell, I just ran your script and it worked! Thanks so much for your time and effort.

Learned a lot from this little exercise, now I see there was really no need to concern myself with controlling the input to awk in pairs of lines, because gawk automatically stops when it reaches the end of an input!

---

