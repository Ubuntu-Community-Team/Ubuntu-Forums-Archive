---
title: "Script to change value in a text file"
date: 2009-11-17
forum: General Help
---

### Post by dardack on 2009-11-17
So I want to create a script (much like i did for WoW and the repeating keys thing) for Dragon Age: Origins.  Basically, when AA is on when the game loads, you can't use FBO, but if AA is off when the game loads, you can use FBO.  Also, once the game is running, turning AA on removes flickering for me.

Sometimes I forget to turn AA off in the configure menu before clicking play.  So what I want is to have some command to look in the .ini settings file and look for:

AntialiasingLevel=#

and change it to:

AntialiasingLevel=0

Then run the game. Is this possible?

---

### Post by Bjalf on 2009-11-17
Something like this?
```
sed -i 's/\(AntialiasingLevel\)=.*/\1=0/' settings.ini
```Try it without -i first.

---

### Post by dardack on 2009-11-17
needed the -i, but thanks works great.

---

### Post by dardack on 2009-11-18
I really appreciate it, i've tried looking at the man page for sed, but i still don't understand it.

Can you explain what's going on here so I can use this in the future?

---

### Post by geirha on 2009-11-18
Some links to get you aquainted with sed (taken from the topic of ##sed on irc.freenode.net).

[http://sed.sf.net/sedfaq.html](http://sed.sf.net/sedfaq.html)
[http://xrl.us/sedintro#uh-0](http://xrl.us/sedintro#uh-0)
[http://xrl.us/sedstd](http://xrl.us/sedstd)
[http://www.gnu.org/software/sed/manual/](http://www.gnu.org/software/sed/manual/)

---

### Post by Bjalf on 2009-11-18
The -i means that the file is edited "in place", it's just prudent to test **thoroughly** before committing.

The s/// is a substitution command. It searches for AntialiasingLevel=*whatever*, remembers *AntialiasingLevel* with \(\) as something to be used later with \1, and replaces the rest of the line with =0. Easy!   :p

Never mind the man pages, this is where I get most of my stuff from: [http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

It's quite well explained here: [http://www.catonmat.net/blog/sed-one-liners-explained-part-one/](http://www.catonmat.net/blog/sed-one-liners-explained-part-one/)

Sed is awesome, and regular expressions are awful.  ;)

---

### Post by dardack on 2009-11-18
What are regular expressions?

And thanks for the links, trying to wrap the brain around it now.

---

### Post by dardack on 2009-11-18
> **Bjalf said:**
> Something like this?
```
sed -i 's/\(AntialiasingLevel\)=.*/\1=0/' settings.ini
```Try it without -i first.

so so s/// is the replacing command, ie sed 's/foo/bar/' replaces 1 instance, the \( \) is like a place marker once it finds what your looking for, the =.* captures everything after the =, the \1
says replace the mark placer with itself?

than replace the =whatever with =0?

---

### Post by Bjalf on 2009-11-19
> **dardack said:**
> What are regular expressions?

> A regular expression (regex or regexp for short) is a special text string for describing a search pattern. You can think of regular expressions as wildcards on steroids. You are probably familiar with wildcard notations such as *.txt to find all text files in a file manager. The regex equivalent is ```
.*\.txt$
```
[http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression)
[http://www.regular-expressions.info/](http://www.regular-expressions.info/)

---

### Post by Bjalf on 2009-11-19
> **dardack said:**
> so so s/// is the replacing command, ie sed 's/foo/bar/' replaces 1 instance, the \( \) is like a place marker once it finds what your looking for, the =.* captures everything after the =, the \1
says replace the mark placer with itself?

than replace the =whatever with =0?
You got it. More accurately, the **s///** replaces the first instance *in each line*.

The **\** character is an escape character, which means that the next (single) character should be treated in a special way. The **()** marks groups. Everything inside the **()** is marked as a group, and they're numbered from 1 to 9. The **\1** means the first group, **\2** means the second, and so on. Perversely, this is where we need to escape the **()**, because else it would just look for regular **()** as text. In other versions of regexp, it is of course the other way around. :roll:

I could have used **/\(AntialiasingLevel=\).*/** and **/\10/**, but that confuses some regexp engines that interprets it as the 10th group, instead of group 1 followed by a zero. And **\0** doesn't mean the character zero.  :roll:

If there were more than one **AntialiasingLevel=**, like **SpecialAntialiasingLevel=**, then I would have said **^AntialiasingLevel=**, the **^** means beginning of line, so it would not match **SpecialAntialiasingLevel=**.

Or if the line went something like this:
```
AntialiasingLevel=6 ; this is an important comment
```I would use something like this:
```
/\(AntialiasingLevel\)=[0-9]+\([ ]*.*\)/\1=0\2/
```The **[0-9]+** means one or more digits, and the **[ ]*.*** means zero or more spaces, followed by zero or more of any character.

Confused yet?     :biggrin:   I use these a lot:
[http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression)
[http://docs.python.org/library/re.html#module-re](http://docs.python.org/library/re.html#module-re)


Regexps are programmed for power, not to be user-friendly. This is why it's so very important to test, test and test again to make absolutely certain that the expression is correct before releasing the monster into the wild.


> Some people, when confronted with a problem, think "I know, I'll use regular expressions."  Now they have two problems.[http://www.codinghorror.com/blog/archives/001016.html](http://www.codinghorror.com/blog/archives/001016.html)

---

### Post by dardack on 2009-11-20
Awesome man, thank you so much.

---

### Post by dddanmar on 2009-11-20
*Any script* I write that involves reading and writing to config files includes sed.

Even without knowing regular expressions its a manageable program to utilize.

[http://anaturb.net/sed.htm](http://anaturb.net/sed.htm) is a good cheat sheet for the commands, and for examples these forums are littered with them.

---

