---
title: "Matching and returning a part of file name on bash"
date: 2011-04-25
forum: General Help
---

### Post by hojjat on 2011-04-25
Hello. If I have files named like this:

abc_one.c
egx_two.c
tsf_two.c
aiq_one.c
...

How can I get a list of the last three chars in the file name on bash? I think there should be a way to pipe the output of ls to grep, but I don't know how. To clarify, the desired output should be like:

one
two
two
one

---

### Post by btindie on 2011-04-25
Try this
```
$ ls -1 | sed -e 's/\.c//' -e 's/[^_]*_//'
```It removes the extension and everything up to and including the underscore.

---

### Post by DaithiF on 2011-04-25
there are many ways of doing something like this ... using sed as in the previous post, or heres one using awk:
```
ls -1 | awk -F '[._]' '{print $2}'

```
this says, use either . or _ as the field delimiter, then print the 2nd field.

---

### Post by hojjat on 2011-04-25
Both excellent answers. However, I was looking for a regexp based solution. This is because in the real case, my file names have many underscores in them, and I the last part is not the only part I'm interested in. So instead of asking a separate question on how to extract the part of file name between second and third underscore, I'd be grateful if you could give me a generic solution I could use.

---

### Post by conradin on 2011-04-25
too bad with your xgrep desires, I thought about it and decided an array is the way to go, assuming all the file names are have the same pattern or 4 characters then 3 desired characters.Write a function to integrate the code below:
```

#!/bin/bash
Unix[1]='abc_one.c'
echo ${Unix[1]:4:3}

```

who knows you might like this solution.

---

### Post by hojjat on 2011-04-25
I actually like it! Can you please explain how it works, or direct me to an easy to understand reading?

---

### Post by matt_symes on 2011-04-25
Hi

> echo ${Unix[1]:4:3}

It's parameter substring extraction. Have a read of this.

[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)

At the bottom of the page.

You can just type this in the terminal.

```
Unix='abc_one.c' && echo ${Unix:4:3}
```

Check the other parameter expansion types as they will also do what you require.

Kind regards

---

### Post by conradin on 2011-04-26
I'm not sure about some of programing desire, as in, will you ever have things like: 
acb_three.c
abcd_one.c

 Im comming at this from the c++ perspective, doing it in bash seems a bit forienge to me. Still if I wanted to read three digits 2 characters back from the end of an array, I would think subtracting 2 from the array index and decrementing a counter 3 spaces before doing a forward read would give me the same data no matter what the file name would be. Why only 3 characters? perhaps your using a code on the last 3 digits.  

the tutorial I ripped that sample from is here:
[http://www.thegeekstuff.com/2010/06/bash-array-tutorial/](http://www.thegeekstuff.com/2010/06/bash-array-tutorial/)

basically what happens is the array  called Unix has 9 spaces in it. 
As Matt put it, echo ${Unix:4:3}, the number 4 represents the starting index, and the next parameter, 3 is the number of spaces to count up from. 
I wonder if I could put a negative sign there and tell it to decrement...

Anyways Im sure theres dozens of ways to approach this.

---

### Post by matt_symes on 2011-04-26
Hi

>  Anyways Im sure theres dozens of ways to approach this.

Yep :popcorn:. 

Here's another one :P Like Conradin, I also prefer the bash built in methods where possible and where they will suffice. In this case they do, otherwise i will use sed or awk. However all suggestions here have been valid and work :)

```
matthew@matthew-laptop:~$ Unix='abc_one.c' && Unix=${Unix##*_} && Unix=${Unix%%.*} && echo $Unix
one
matthew@matthew-laptop:~$ 
```

```
matthew@matthew-laptop:~$ Unix='**abc_one_two_three.c**' && Unix=${Unix##*_} && Unix=${Unix%%.*} && echo $Unix
three
matthew@matthew-laptop:~$
```

Kind regards

---

### Post by hojjat on 2011-04-26
I'm still surprised that there is no command one can use to pipe in some string, match part of it and received the matched part in stdout. Apparently awk or sed should do that, but I find their documentation cryptic.

---

### Post by matt_symes on 2011-04-26
Hi

> I think there should be a way to pipe the output of ls to grep, but I don't know how

Well ls and grep wont do what you want, although you could use grep to filter invalid file names.

Both the sed and awk examples will work and display to stdout. Have you not tried them.

```
matthew@matthew-laptop:~/tmp$ ls
abc_one.c  def_two.c
matthew@matthew-laptop:~/tmp$ ls -1 | sed -e 's/\.c//' -e 's/[^_]*_//'
one
two
matthew@matthew-laptop:~/tmp$
```

```
matthew@matthew-laptop:~/tmp$ ls
abc_one.c  def_two.c
matthew@matthew-laptop:~/tmp$ ls -1 | awk -F '[._]' '{print $2}'
one
two
matthew@matthew-laptop:~/tmp$
```

> How can I get a list of the last three chars in the file name on bash?

This was a bit confusing as it seemed to quote using bash. The bash parameter examples will work if you add a small amount of code to loop over the files in the directory(s).

For completeness. It's only a simple script.

```
#!/bin/bash
for FILE in ~/tmp/*
do
FILE=${FILE##*_} 
FILE=${FILE%%.*}
echo $FILE
done
```

```

matthew@matthew-laptop:~$ ls tmp
abc_one.c  def_two.c
matthew@matthew-laptop:~$ ./bash
one
two
matthew@matthew-laptop:~$
```

Is this not what you wanted ?

Kind regards

---

### Post by nothingspecial on 2011-04-27
A good introduction to sed here

[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

### Post by hojjat on 2011-04-27
> **matt_symes said:**
> 

Is this not what you wanted ?



Well, the awk one worked for me, after I modified it to meet my needs:

```
 ls -1 | awk -F '[._]' '{print $6}' | sort | uniq -c | sort -nr
```

However, this is not regex based; it splits the string and then returns part of it.

In other words, my original question is answered :) However, this had led me to the second question of "isn't there a way to match a pattern within a string, and only return the matched part?"

An example I made up is this: Suppose that my files are named like this:

1322_2323_23-17-55_10091_14
2975_13-12-23_10091_47
4326_2323_1442_01-19-00_10094

And all I'm interested in, is the part that appears like dd-dd-dd; the parts before and after it may or may not include underscores, digits etc. All I know is that there is always a section like dd-dd-dd. How can I match that and fetch it? (Definitely needs regex)

---

### Post by DaithiF on 2011-04-27
well technically the '[._]' field separator in the awk example is a regular expression :)

but to answer your question, something like this:
```
$ cat file
1322_2323_23-17-55_10091_14
2975_13-12-23_10091_47
4326_2323_1442_01-19-00_10094

$ sed -r 's/.*([0-9]{2}-[0-9]{2}-[0-9]{2}).*/\1/' file
23-17-55
13-12-23
01-19-00

```

---

### Post by nothingspecial on 2011-04-27
For your example


```
$ cat blah.txt
1322_2323_23-17-55_10091_14
2975_13-12-23_10091_47
4326_2323_1442_01-19-00_10094
$ grep -o [0-9][0-9]-[0-9][0-9]-[0-9][0-9]  blah.txt
23-17-55
13-12-23
01-19-00

```

---

### Post by hojjat on 2011-04-28
> **nothingspecial said:**
> ```
...
$ grep -o [0-9][0-9]-[0-9][0-9]-[0-9][0-9]  ...

```

There you go! That's what I've been thinking of all the time! I can simply do something like

```
ls | grep -o PATTERN
```

EDIT: But weight a minute .. if there are two parts of the string that match the pattern, this will give me both of them, right? What if I only want the first match?

---

### Post by DaithiF on 2011-04-28
> **hojjat said:**
> EDIT: But weight a minute .. if there are two parts of the string that match the pattern, this will give me both of them, right? 

Yes
> What if I only want the first match?
then you're back to the sed solution i gave above.

---

