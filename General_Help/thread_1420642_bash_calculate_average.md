---
title: "bash calculate average"
date: 2010-03-03
forum: General Help
---

### Post by capybara! on 2010-03-03
Hi,

does anyone know how to calculate an average in a simple way with bash?
I've got something like this:
```
$ cat results.txt | head -10 | tr " " "\t" | cut -f13
0.23929285124
0.404716908011
0.35113102608
0.399400619547
0.387914593281
0.33136817487
0.368338808628
0.436386203306
0.386254991628
0.355122557677
```

and now I want to calculate the average of the resulting numbers. I know I could write a bash or awk or perl script and use that, but isn't there a more simple, elegant way? There is for example "sum" in the coreutils, but no "avg"...

Hope it's ok to post it in this forum, it's not really ubuntu specific...
Thanks.

---

### Post by mobilediesel on 2010-03-03
> **capybara! said:**
> Hi,

does anyone know how to calculate an average in a simple way with bash?
I've got something like this:
```
$ cat results.txt | head -10 | tr " " "\t" | cut -f13
0.23929285124
0.404716908011
0.35113102608
0.399400619547
0.387914593281
0.33136817487
0.368338808628
0.436386203306
0.386254991628
0.355122557677
```

and now I want to calculate the average of the resulting numbers. I know I could write a bash or awk or perl script and use that, but isn't there a more simple, elegant way? There is for example "sum" in the coreutils, but no "avg"...

Hope it's ok to post it in this forum, it's not really ubuntu specific...
Thanks.

You can try here: [http://nixshell.wordpress.com/2007/03/26/calculating-averages/](http://nixshell.wordpress.com/2007/03/26/calculating-averages/)
I haven't had to do averages at the command line but that link looks promising.

Awk probably would be better but I have little experience with it. Someone will probably reply with something about awk.

---

### Post by amrypma on 2010-03-03
Have a look at 'bc' it is a fairly advanced command-line calculator.

I use it in this [script]("http://fiercepredictions.eu/?p=233#more-233") I've written.

---

### Post by iponeverything on 2010-03-03
```
cat results.txt|head -10|tr " " "\t"|cut -f13|awk 'f += $1 {printf("%.13g\n",f/NR)}'|tail -1
```

---

### Post by mobilediesel on 2010-03-03
> **amrypma said:**
> Have a look at 'bc' it is a fairly advanced command-line calculator.

I use it in this [script]("http://fiercepredictions.eu/?p=233#more-233") I've written.

For being a fairly simple script, that is super-useful. I keep my download directory pretty clean anyway but now I can make the computer do it instead of me. I **really** like how the grace period for deleting is dependent on disk free space.

---

### Post by capybara! on 2010-03-03
> **iponeverything said:**
> ```
cat results.txt | head -10 | tr " " "\t" | cut -f13 |awk 'ttt += $1  {print ttt/NR}'| tail -1
```

awk is not the best thing for floating point.


Really nice short solution, that was what I was looking for!!

I found a solution using perl, which is maybe more accurate but looks dirty:

```
cat results.txt | head -10 | tr " " "\t" | cut -f13 | tr "\n" " " | perl -ne 'use List::Util qw(sum);  @arr = split(" ", $_); print sum(@arr)/@arr."\n"'
```

Thanks a lot !

---

### Post by rnerwein on 2010-03-03
hi
what ?
 awk ' { sum += $1; n++ } END { print sum/n }' file.txt
ciao

---

### Post by iponeverything on 2010-03-03
> **capybara! said:**
> Really nice short solution, that was what I was looking for!!

I found a solution using perl, which is maybe more accurate but looks dirty:

```
cat results.txt | head -10 | tr " " "\t" | cut -f13 | tr "\n" " " | perl -ne 'use List::Util qw(sum);  @arr = split(" ", $_); print sum(@arr)/@arr."\n"'
```

Thanks a lot !

I fixed up the above solution to take it out 13 digits.
```
awk 'f += $1 {printf("%.13g\n",f/NR)}'
```

---

### Post by William Shotts on 2010-03-03
Here is a script that I wrote that may address your need.  It accepts a stream of numbers from standard input (skipping over any invalid entries) and calculates the average using bc.  The script accepts one option, -s which sets the scale of the output.  If not specified, the default scale is 2.

```
#!/bin/bash

if [[ $1 ]]; then
        case $1 in
                -s|--scale)     scale=$2 ;;
                *)              echo "usage: average [-s scale]" >&2 
                                exit 1 ;;
        esac
fi
c=0
{       echo "t = 0; c = 0; scale = 2"
        [[ $scale ]] && echo "scale = $scale"
        while read value; do
                if [[ $value =~ ^[-+]?[0-9]*\.?[0-9]+$ ]]; then
                        echo "t += $value"
                        ((++c))
                fi
        done
        (( c )) && echo "t / $c"
} | bc
```

---

### Post by amrypma on 2010-03-10
> **mobilediesel said:**
> For being a fairly simple script, that is super-useful. I keep my download directory pretty clean anyway but now I can make the computer do it instead of me. I **really** like how the grace period for deleting is dependent on disk free space.

Thanks,
You're welcome.

---

### Post by marco.caminati on 2010-03-31
Here is a further approach using dc; maybe not as neat as awk-based one, but still short.
```
tee >(wc -l) | (echo 3;echo k; while read n; do echo +; echo "$n"; done ; echo /; echo p ) | dc 2> /dev/null
```
It reads numbers from stdin and prints the average on stdout. Vary the "3" hardcoded in it to adjust precision.
Cheers.

---

