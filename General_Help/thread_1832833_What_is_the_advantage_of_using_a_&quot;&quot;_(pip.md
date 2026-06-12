---
title: "What is the advantage of using a &quot;|&quot; (pipe) when more arguments will do the job?"
date: 2011-08-25
forum: General Help
---

### Post by bjackman on 2011-08-25
Firstly, I apologise for the terrible thread title. I did try, but nothing better came to me.

Now.  I've been reading Linux Format Magazine's "School of Linux" (sorry, no  link. if you have any of the CDs from recent issues you will find PDFs  of the series on there). Basically it's an introduction to Linux with a  target audience of people who have been computer enthusiasts for a long  time but haven't used linux much. If anyone requests it I can upload the  PDFs. 

So I'm currently working on getting used to Bash and I've  noticed that the author will use the | character alot more often than  you'd expect, for example:

```
cat words.txt | cut -c 5-7
```where this works just as well so far as I can see:

```
cut -c 5-7 words.txt
```.

From  experience I know that normally when an expert does something like this  it's for some reason that will come into play at higher levels, i.e.  "to get into a good habit".
Does anyone have any idea what reason that might be?

---

### Post by sanderd17 on 2011-08-25
A pipe is easy to see when you are used to it. You just see that the main input of the right part comes from the left part, and the arguments are just "setings". If you work only with arguments, than it's not so clear what the input is and what the settings are.

The pipe also can be extended more, like say if you want to use the cut command on something that comes from grep first.

```

grep "123" file.txt | cut -c 5-7

```

will work, but there is no way to do it with arguments. Here you also see that the start input file is a bit hidden in the code, so this one is more clear:

```

cat file.txt | grep "123" | cut -c 5-7

```

You can follow the flow very easy: the file goes through grep into the cut. The main input just goes from left to right, like you would read it.

---

### Post by sisco311 on 2011-08-25
Maybe the author wants to win the [Useles Use of cat]("http://partmaps.org/era/unix/award.html") award?

If you want to learn Bash, then check out the BashGuide at [Greg's Wiki]("http://mywiki.wooledge.org/") alongside with BashFAQ & BashPitfalls on the same site.

*This guide aims to be a starting point for people interested in learning to work with BASH. It aspires to **teach its readers good practice techniques** for developing scripts for the BASH interpreter, and to educate them about the internal operation of BASH.*

---

### Post by Vaphell on 2011-08-25
in general it's considered a bad practice to call cat to read file when the first command that actually does things can read files just fine. Granted, it increases readability and modularity of the expression and it is helpful to use cat when building the expression.

Often i test the chain with echo that prints out test cases and it's easier to replace echo part with cat to do a quick and dirty check if the input file is processed correctly than adding/removing segments and moving file names around. When it works i remove the initial part and move file names to their proper place.

```
echo $'some stuff\nsome other stuff' | grep <some expression> | <whatever>
cat file.in | grep <some expression> | <whatever>
grep <some expression> file.in | <whatever>
```

---

### Post by bodhi.zazen on 2011-08-25
> **bjackman said:**
> From  experience I know that normally when an expert does something like this  it's for some reason that will come into play at higher levels, i.e.  "to get into a good habit".
Does anyone have any idea what reason that might be?

This happens when people are learning. It is considered best practice not to pipe commands unless needed

The most common is "cat file.txt | grep regex" rather then

grep regex file.txt


> **sisco311 said:**
> Maybe the author wants to win the [Useles Use of cat]("http://partmaps.org/era/unix/award.html") award?

LOL indeed

> **Vaphell said:**
> in general it's considered a bad practice to call cat to read file when the first command that actually does things can read files just fine. 

```
echo $'some stuff\nsome other stuff' | grep <some expression> | <whatever>
cat file.in | grep <some expression> | <whatever>
grep <some expression> file.in | <whatever>
```

You are correct.

The general learning curve is (IMO)

echo
cat
grep
sed
awk
perl 

with each command being more complex.

If you are not already familiar with awk, I am encouraging people to learn it.

---

### Post by Habitual on 2011-08-25
I did "cat file | grep <string> for years.

now it's grep <string> file

Less typing is a GOOD thing. :)

---

### Post by lykwydchykyn on 2011-08-25
> **bodhi.zazen said:**
> This happens when people are learning. It is considered best practice not to pipe commands unless needed


Other than less typing, is there an actual concrete reason for this?

---

### Post by Grenage on 2011-08-25
> **lykwydchykyn said:**
> Other than less typing, is there an actual concrete reason for this?

Yes; it's a superfluous process.

---

