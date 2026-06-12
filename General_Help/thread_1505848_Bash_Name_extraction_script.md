---
title: "Bash Name extraction script"
date: 2010-06-09
forum: General Help
---

### Post by skula on 2010-06-09
Help i need a bash script to extact the names in a text file and output it into another text file. i need the names to be extracted and placed on each individual lines. that one name to a line.

case scenerio. i have a file called a.txt  and i need it to extract the names out of a.txt and save it into a new file say b.txt ehich the script will create in root folder. each names on a single line

names in the txt file dat need extaction looks likes this 
171. Magadur
172. Magaharan
173. Magg
174. Magle
175. Magola
176. Magoolagan
177. Magoris
178. Magris
179. Magrys
180. Magagnin
181. Magal
182. Magic
183. Magsi
184. Magua
185. Magunda
186. Magunnigal
187. Magura
188. Magain
189. Magana

help is appreciated thank you

---

### Post by BoneKracker on 2010-06-09
This ought to do it:
```

#!/bin/bash

cut -d' ' -f2 oldfile.txt > newfile.txt
```

There are several good ways to do this.  Another is to use the built-in parameter expansion features of BASH:
```
#!/bin/bash

while read line; do
  echo ${line#* } >> newfile.txt
done < oldfile.txt
```
(Note the space after the * character.)

The tradeoff between the two scripts is that the first has to call the external program 'cut', while the second has to employ a loop.  I'm not sure which would actually be more efficient, but they both are.

Another way is to use sed:
```
sed 's/^.* +//' oldfile.txt > newfile.txt
```

In this case, you don't really need the power of sed (which is more memory-expensive than the other two scripts), because the lines can be split easily at the space.  In more complex situations where complex pattern-matching and parsing is required that is beyond the capabilities of 'cut' or BASH parameter expansion, you might want to use sed.

---

### Post by TheForumTroll on 2010-06-09
Let me get this straight. You want this:

```

171. Magadur
172. Magaharan
173. Magg
174. Magle
175. Magola

```

To become this:
```

Magadur
Magaharan
Magg
Magle
Magola

```

:?:

EDIT: Ops too slow :p

---

### Post by skula on 2010-06-09
> **TheForumTroll said:**
> Let me get this straight. You want this:

```

171. Magadur
172. Magaharan
173. Magg
174. Magle
175. Magola

```To become this:
```

Magadur
Magaharan
Magg
Magle
Magola

```:?:

EDIT: Ops too slow :p

yes dat is exactly wat i want.ty

---

### Post by skula on 2010-06-09
> **BoneKracker said:**
> This ought to do it:
```

#!/bin/bash

cut -d' ' -f2 oldfile.txt > newfile.txt
```There are several good ways to do this.  Another is to use the built-in parameter expansion features of BASH:
```
#!/bin/bash

while read line; do
  echo ${line#* } >> newfile.txt
done < oldfile.txt
```(Note the space after the * character.)

The tradeoff between the two scripts is that the first has to call the external program 'cut', while the second has to employ a loop.  I'm not sure which would actually be more efficient, but they both are.

Another way is to use sed:
```
sed 's/^.* +//' oldfile.txt > newfile.txt
```In this case, you don't really need the power of sed (which is more memory-expensive than the other two scripts), because the lines can be split easily at the space.  In more complex situations where complex pattern-matching and parsing is required that is beyond the capabilities of 'cut' or BASH parameter expansion, you might want to use sed.



thanks .. dis did de work cut -d' ' -f2 oldfile.txt > newfile.txt    but this did not work

sed 's/^.* +//' oldfile.txt > newfile.txt   please could you point me to were i can read up on the commands that will allow me to do more name advance name extraction. i really want to learn. especially knoing those characters u know.

thanks for ur help. cheers man

---

### Post by BoneKracker on 2010-06-09
> **skula said:**
> thanks .. dis did de work cut -d' ' -f2 oldfile.txt > newfile.txt    but this did not work

sed 's/^.* +//' oldfile.txt > newfile.txt   please could you point me to were i can read up on the commands that will allow me to do more name advance name extraction. i really want to learn. especially knoing those characters u know.

thanks for ur help. cheers man

Ah.  I forgot something.  Sorry about that.  This should work:

```
sed -r 's/^.* +//' test.txt > newfile.txt
```

I forgot the option "-r".

Search the web for "sed tutorial".  Here is one:
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

Regarding "those characters", you may want to first learn about "regular expressions", which are used to define patterns (like "^.* +" above, which meant "select everything from the beginning of the line up to the end of any spaces").  A good way to learn about and experiment with regular expressions is by playing with the 'grep' command (which is extremely useful to know anyway).

So here is a plan:

1.  learn how to use grep
2.  practice writing regular expressions and test them with grep (use grep to select a line in a file having certain text)
3.  learn sed, write some scripts that use sed
4.  later, learn awk
5.  if you do a lot of work like this, you may want to use perl instead of bash for the work

---

### Post by nemilar on 2010-06-09
The previous posters already pointed out that there are a dozen ways to do this in the command line.  It'd be good to learn the tools; but in this specific case, this should work:

```
 cat your_file | awk '{print$2}' 
```

Simply takes the file and prints the second column.

---

### Post by BoneKracker on 2010-06-10
> **nemilar said:**
> The previous posters already pointed out that there are a dozen ways to do this in the command line.  It'd be good to learn the tools; but in this specific case, this should work:

```
 cat your_file | awk '{print$2}' 
```

Simply takes the file and prints the second column.

Awk is a great and often useful tool, but it's not really the right tool for the job in this case.

**1.  Less-powerful tools that use less RAM can get the job done**; using awk here is inefficient unless you are already using it in the script or otherwise know it to be loaded in RAM.

It's always best to try first to get something accomplished using the built-in capabilities of the shell (e.g. BASH "parameter expansion", demonstrated earlier, or BASH's 'printf' built-in).  You've already got the shell loaded just by virtue of running the system, so this is the most efficient way to go.

If that fails or is excessively inconvenient, then call a _small_ utility that can easily get the job done (e.g. 'cut'), or a utility known to be already loaded or cached in RAM because it's already in use or has recently been used.

If that fails, then call the smallest tool that that will do the job (in this case, that would be sed long before awk).  On my system, their sizes in bytes are:
```
cut  38096
sed  58976
awk 350040
```
As you can see, cut and sed are relatively small compared to awk, which is _an order of magnitude larger_. While a program's size is not equivalent to its memory usage, it comprises part of its memory usage and is a good indicator.

So, while awk is a great tool that's often needed, I wouldn't use it in this case (especially since I can't even argue that it's syntactically easier than using the much tinier 'cut' command.)


**2. In terms of performance, awk is the slowest of these alternatives.**  There is not really an appreciable difference over a single iteration, but 'awk' is actually about twice as slow as the other alternatives (with 'cut' being the fastest), and this would matter if you were running it on lots of files.  For the purposes of our discussion, this mainly serves to reinforce the value of picking the right tool for the job.
```
~ $ time cut -d' ' -f2 test.txt > newfile.txt

real	0m0.003s
user	0m0.002s
sys	0m0.001s

~ $ time while read line; do echo ${line#* } >> newfile.txt; done < test.txt

real	0m0.004s
user	0m0.004s
sys	0m0.000s

~ $ time sed -r 's/^.* +//' test.txt > newfile.txt

real	0m0.004s
user	0m0.002s
sys	0m0.001s

~ $ time cat test.txt | awk '{print$2}' > newfile.txt

real	0m0.008s
user	0m0.002s
sys	0m0.004s
```

**3. "cat <somefile>" into a pipe is a telltale sign you're probably doing something wrong.**  There is usually (not always, but usually) a better way to do things.

In this case, seeing "cat <somefile> |", we check out awk's options and... *voila*, guess what, awk takes a filename as a parameter, allowing us to avoid unnecessarily calling the external program 'cat' and unnecessarily opening a pipe redundant redundant to stdin. So instead of:
```
 cat your_file | awk '{print$2}' 
```
... one should do:
```
awk '{print $2}' oldfile.txt
```
Additionally, the output needs to go to a new file, not stdout, so it would be:
```
awk '{print $2}' oldfile.txt > newfile.txt
```

---

### Post by DaithiF on 2010-06-10
> **BoneKracker said:**
> 'awk' is actually about twice as slow as the other alternatives
```

~ $ time cat test.txt | awk '{print$2}' > newfile.txt

real    0m0.008s
user    0m0.002s
sys    0m0.004s
```

Hi, 
you should probably time awk without the extra cat & pipe to get a true picture of its performance ... it won't be as bad as twice as slow.

but to mis-quote donald knuth, don't worry about performance until you need to worry about performance.  For a trivial bit of text processing thats going to take micro-seconds whatever tool you use, i wouldn't give much thought to the relative efficiencies of different approaches, just use one and move on to a better use of your time.  Spending seconds/minutes of your time to save microseconds of your computers processing time is not usually a positive cost/benefit transaction :)

---

### Post by BoneKracker on 2010-06-10
> **DaithiF said:**
> Hi, 
you should probably time awk without the extra cat & pipe to get a true picture of its performance ... it won't be as bad as twice as slow.

but to mis-quote donald knuth, don't worry about performance until you need to worry about performance.  For a trivial bit of text processing thats going to take micro-seconds whatever tool you use, i wouldn't give much thought to the relative efficiencies of different approaches, just use one and move on to a better use of your time.  Spending seconds/minutes of your time to save microseconds of your computers processing time is not usually a positive cost/benefit transaction :)

Yeah, I know what you're saying, but the flaw in that is that we are talking about _learning_ here.

The real cost-benefit equation is that investing minutes of time now to understand how and why to pick the best tool pays off for the rest of someone's programming "life".

As I said: > There is not really an appreciable difference over a single iteration, but 'awk' is actually about twice as slow as the other alternatives (with 'cut' being the fastest), _and this would matter if you were running it on lots of files. For the purposes of our discussion, this mainly serves to reinforce the value of picking the right tool for the job_.

In reality, the easiest of the few things that first come to mind is what you're going to do.  But if you take the time now to become familiar with things like BASH parameter expansion, cut, and sed, you won't go through life solving every problem you encounter with awk or perl because they are all you know and the only thing that first comes to mind.  Be your own "swiss army knife".

---

### Post by DaithiF on 2010-06-10
just to be clear, I agree 100% on the importance of learning, so I'm not saying its not worth learning all the tools mentioned.  In fact quite the opposite, I would encourage anyone interested in the command line to get proficient in all the methods talked about.  

My only point is that I wouldn't use their relative efficiency in memory usage / processing time as the primary motivation for learning them.  For me its their different capabilities, and the elegance with which some tools can handle a particular task vs. others that is the main reason.  That and of course the inherent value of learning *any* new skill.

---

### Post by BoneKracker on 2010-06-10
> **DaithiF said:**
> just to be clear, I agree 100% on the importance of learning, so I'm not saying its not worth learning all the tools mentioned.  In fact quite the opposite, I would encourage anyone interested in the command line to get proficient in all the methods talked about.  

My only point is that I wouldn't use their relative efficiency in memory usage / processing time as the primary motivation for learning them.  For me its their different capabilities, and the elegance with which some tools can handle a particular task vs. others that is the main reason.  That and of course the inherent value of learning *any* new skill.

I agree.  Which tool would you choose in this case?

---

### Post by BoneKracker on 2010-06-10
> **DaithiF said:**
> just to be clear, I agree 100% on the importance of learning, so I'm not saying its not worth learning all the tools mentioned.  In fact quite the opposite, I would encourage anyone interested in the command line to get proficient in all the methods talked about.  

My only point is that I wouldn't use their relative efficiency in memory usage / processing time as the primary motivation for learning them.  For me its their different capabilities, and the elegance with which some tools can handle a particular task vs. others that is the main reason.  That and of course the inherent value of learning *any* new skill.

I agree, although to me "elegance" has a lot to do with efficiency, in addition to degree of fit with the requirement.

Which tool would you choose in this case?  (This isn't about there being a "best choice", it's a discussion about why and how to consider alternative ways of doing something -- because, as we all know, there are often many alternative ways.)

---

### Post by DaithiF on 2010-06-10
> **BoneKracker said:**
> I agree.  Which tool would you choose in this case?

probably sed, something like 
```
sed 's/^[0-9. ]*//' somefile > newfile 
```

---

### Post by BoneKracker on 2010-06-10
> **DaithiF said:**
> probably sed, something like 
```
sed 's/^[0-9. ]*//' somefile > newfile 
```

When I first responded to this thread, I slapped down a quick sed expression.  Bam.  Problem solved.  :lol:

Then I went back and added the others.  I'd use cut if I thought of it, but that would depend on whether I spent 5 seconds or 10 seconds thinking about it.

---

