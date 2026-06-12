---
title: "script to capitalize words"
date: 2010-06-13
forum: General Help
---

### Post by miak on 2010-06-13
Hi,

I am trying to write organize songs on my computer and ran out to the problem that some songs had names with underscores instead of spaces(which I had no problems removing, using awk). But i had some troubles with capitalizing first letters of the words. I think that it is not a big problem, but I don't know how to do it. 
Can anyone help?

Thanks,
miak

---

### Post by tom.swartz07 on 2010-06-13
Yup Yup.

If you want to work in a python callout, you could use this;
```
python -c "print raw_input().capitalize()"
```

Example output would be like this:
```
tom@tardis:~$ echo "astring"  | python -c "print raw_input().capitalize()"
Astring
```

There are other methods, but that is the easiest.
Cheers!

---

### Post by tom.swartz07 on 2010-06-13
Like I said, there are other methods, I just had to look them up..
You could use sed, but its really ugly looking.

```
sed 's/\([a-z]\)\([a-zA-Z0-9]*\)/\u\1\2/g'
```
That will chew through any file piped to it and capitalize the first letter.

Since youre already using awk, you might find this interesting; Im just copying it (I dont have hardcore experience with awk)

```
awk '{ for ( i=1; i <= NF; i++) 
           {   sub(".", substr(toupper($i),1,1) , $i)  }  
            print }' file
```

---

### Post by miak on 2010-06-13
Thanks very much, I used one with awk which worked fine. But I got really interested in python example, though I didn't figure out the way how to use it for files with multiple names like "one two". Is there an easy way to do it with python? Also can you call outside functions from inside of awk?

---

### Post by tom.swartz07 on 2010-06-13
> **miak said:**
> Thanks very much, I used one with awk which worked fine. But I got really interested in python example, though I didn't figure out the way how to use it for files with multiple names like "one two". Is there an easy way to do it with python? Also can you call outside functions from inside of awk?

I suppose you could format the script in such a way that it parses each word individually, I would use an array and a do loop, but thats just me. I suppose there are quicker ways of doing it.

I cant say for sure, but I dont think that you could call a script or program from one language while in the middle of another program

---

### Post by kaibob on 2010-06-13
The other answers are easier, but it's interesting to note that bash now has the ability to do what you want.

> $ var="this is a test" ; echo ${var~}
This Is A Test

This actually changes the case of the first letter of each word, which can lead to undesirable results.

> $ var="My name is Kaibob" ; echo ${var~}
my Name Is kaibob

This can be fixed with:

> $ var="My name is Kaibob" ; var=${var,,} ; echo ${var~}
My Name Is Kaibob

REFERENCE:
[http://wiki.bash-hackers.org/syntax/pe#case_modification](http://wiki.bash-hackers.org/syntax/pe#case_modification)

---

### Post by tom.swartz07 on 2010-06-13
> **kaibob said:**
> The other answers are easier, but it's interesting to note that bash now has the ability to do what you want.



This actually changes the case of the first letter of each word, which can lead to undesirable results.



This can be fixed with:



REFERENCE:
[http://wiki.bash-hackers.org/syntax/pe#case_modification](http://wiki.bash-hackers.org/syntax/pe#case_modification)

WOW! thats something I never knew!

Thanks for that

---

### Post by miak on 2010-06-13
Thanks guys,

this was really helpful. I just have one more small question not related to the topic.
How can you specify multiple constraints for for loops?
for example if i want to iterate over all files that end with .mp3 or .flac or something else.
It's straightforward with one constraint, i just write "for file in *.mp3", but I had some trouble with multiple constraints.

---

### Post by tom.swartz07 on 2010-06-13
> **miak said:**
> Thanks guys,

this was really helpful. I just have one more small question not related to the topic.
How can you specify multiple constraints for for loops?
for example if i want to iterate over all files that end with .mp3 or .flac or something else.
It's straightforward with one constraint, i just write "for file in *.mp3", but I had some trouble with multiple constraints.

You could use brace expansion:

```
bash$ echo a{d,c,b}e
     ade ace abe
```

in your case, 

```
for file in *.{mp3,flac}
```

---

### Post by miak on 2010-06-13
Thank you very much.

That solves all my problems for now :)

---

### Post by tom.swartz07 on 2010-06-13
> **miak said:**
> Thank you very much.

That solves all my problems for now :)

Amazing!  You're welcome! :D
If you could mark the thread as solved, I would greatly appreciate it!

Also, if you want to share, maybe you would like to submit your scripts to a Launchpad project that I have?
We specialize in small, one off scripts that make life easier than doing things by hand.
[https://edge.launchpad.net/codemonkey/](https://edge.launchpad.net/codemonkey/)

Take a look, if youre interested, PM me! :D

---

