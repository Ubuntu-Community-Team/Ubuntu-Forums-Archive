---
title: "Help making a module"
date: 2010-12-18
forum: General Help
---

### Post by NeMewSys on 2010-12-18
Hi, im learning to make my first module!
First of all avoid answers like "read this huge book that weights 20 pounds" or "learn the basics first" or "you need to install alot more than what you need". Because that's the type of answers i've been getting in places where people are suppose to help.

Note: I know about the book linux dev driv 3rd edition, and it has the same problem as the tutorial im following: doesnt explain nothing to newbies...

Now my situation:
Im following this tutorial: [http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0,0](http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0,0)
My point is to learn exactly what it teaches, play with a paralel port (yes i know for you there are thousands of funnier and "simpler" ways to do this, but i want this one).

But now im stuck on page 2, where the author says:
> Since the release of kernel version 2.6.x, compiling modules has become slightly more complicated. **First, you need to have a complete, compiled kernel source-code-tree.** If you have a Debian Sarge system, you can follow the steps in Appendix B (towards the end of this article). In the following, I&#8217;ll assume that a kernel version 2.6.8 is being used.He doesnt tell how do i do that. :(
So i went to kernel.org, downloaded the one thats similar to me (my ubuntu has 2.6.31-19-generic so i downloaded the 2.6.31 version of the kernel).

Then i extracted it, and did make config, pressed ENTER key all the way down choosing default options, then i did make and waited all night.

Now i was hoping to make this work (little i knew that this hell was just beginning).
So i inputed the following line like the authour tells:
**$ make -C ../Desktop/kernel-source-2.6.31 M=pwd modules**

But he gives me errors like /Desktop/kernel-source-2.6.31/pwd/modules not found or something like that.

Yes, i dont know how to mess with the kernel, no i dont want to become a linux hacker, yes just wanna make the damn module compiling right... :(

Please, tell me what to do *just to this situation* step by step very, but very slowly to compile this stuff. Please take a look at the page 2 of that tutorial to understand what i need to do.

**Thank you all that will really help**, and no thanks for those that will link to books, blame me because i dont understand such a simple task, tell me that i need to learn 343721892 things just to do that or ask me to install interminable stuff just to do that step... etc.


A little about why i want to learn this:
I learned about operating systems in college, but on the theorical part, so i know alots of theory about this stuff, but im a zero when it comes to really use this things, so, i would like to learn this cool part that is, connecting the computer to the "outside world" trought the paralelport in this case.
I think that after i learn this, even knowing that it can be a bit hard, like it is being right now, it will help me to improve more my skills using linux.
Ps. Yes, i know there are alot of other things that i can learn, but now, im on with this one, no changing mind here.



**EDIT:**
Its easier to show a picture of the problem:

[IMG]http://gyazo.com/ce00a13d22a62fb7d8a5a3859fb7c652.png[/IMG]

The yellow underlined line on the terminal says "File or directory not found!"
The next line are the normal makefile errors:
"make[1]: No rule for target ' ... '
/Makefile . Stop."

Inside the folder *linux-2.6.31.14* its the compiled kernel i wanna use in that tutorial (the author uses 2.6.8).
Inside the folder *modules *are 2 files as you can see in the terminal, i'll *cat* the files here:

Makefile:
[PHP]obj-m: nothing.o
[/PHP]nothing.c:
[PHP]#include <linux/module.h>

MODULE_LICENSE("GPL");
[/PHP]
As you see, its just the code the author asks us to use in those files for the first example.

---

### Post by NeMewSys on 2010-12-18
Anyone?? :(

---

### Post by katykat on 2010-12-18
generic so i downloaded the 2.6.31 version of the kernel).
then
**$ make -C ../Desktop/kernel-source-2.6.8 M=pwd modules**
But he gives me errors like /Desktop/kernel-source-2.6.8/pwd/modules not found or something like that.
------------------------------------------------------------------

If you downloaded 2.6.31 probably best not to  use 2.6.8....

Just a thought.

The author is working off a different kernel.
Substitute

---

### Post by NeMewSys on 2010-12-18
> **katykat said:**
> generic so i downloaded the 2.6.31 version of the kernel).
then
**$ make -C ../Desktop/kernel-source-2.6.8 M=pwd modules**
But he gives me errors like /Desktop/kernel-source-2.6.8/pwd/modules not found or something like that.
------------------------------------------------------------------

If you downloaded 2.6.31 probably best not to  use 2.6.8....

Just a thought.

The author is working off a different kernel.
Substitute
Yes i wont use 2.6.8.
Im trying to use 2.6.31, but im having the problem i reported.

EDIT: Oh sorry, its a typo in the post i made, i was using the commands:

* $ make -C ../Desktop/kernel-source-2.6.**31** M=pwd modules*

not 2.6.8, but the error is correct, the error is something  like */Desktop/kernel-source-2.6.**31**/pwd/modules not found*.

---

### Post by NeMewSys on 2010-12-18
I edited the first post to insert a screen that may help probing the problem.
Thanks for your help so far.

---

