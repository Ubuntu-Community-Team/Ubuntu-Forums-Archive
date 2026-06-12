---
title: "Good command-line calculator?"
date: 2009-08-26
forum: General Help
---

### Post by gldearman on 2009-08-26
Hi, all,

Does anyone know a good calculator that can be used directly from the command line?  I'd like to be able to enter a calculation at the prompt in some easy syntax and have the answer returned to standard output.  I'd rather not have to enter and exit a calculator shell.

As is, when I am at the command-line and have to do math, I have to either open a new window for gnome-calculator, do my calculation, and switch back to the command line; or craft some bizarre and arcane syntax for bc.

Does anyone have any suggestions?  I had heard that speedcrunch could be used this way, but from perusing its home page, I appear to have heard incorrectly.

Thanks for any suggestions you may have!

---

### Post by Simian Man on 2009-08-26
I use Python for that.  It is easy, always available, and you can create subroutines for calculations using familiar syntax.

---

### Post by gldearman on 2009-08-26
Not such familiar syntax to me, since I don't know Python.  I would have to write my own subroutines for calculations? Or is there some built-in Python command?

<aside>
Hey, you're in Tallahassee, too!  Nice to meet you!
</aside>

---

### Post by Bachstelze on 2009-08-26
```
firas@itsuki ~ % echo $((2+2))
4
firas@itsuki ~ % echo "2+2" | bc
4

```

---

### Post by lykwydchykyn on 2009-08-26
> **gldearman said:**
> Not such familiar syntax to me, since I don't know Python.  I would have to write my own subroutines for calculations? Or is there some built-in Python command?


If all you want to do are math calculations, learning the necessary syntax should take about 2 minutes.

How complicated is the math in question?

EDIT: then again, you didn't want to have to enter a shell, so python would not be what you're looking for.

---

### Post by Simian Man on 2009-08-26
```
[finlayso@splinter ~]$ python
Python 2.6 (r26:66714, Jun  8 2009, 16:07:29) 
[GCC 4.4.0 20090506 (Red Hat 4.4.0-4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 2+2
4
>>> 7.0 * 12.5
87.5
>>> 12 ** 2
144
>>> def square(x):
...     return x * x
... 
>>> square(12)
144
>>> x = 1+2+3+4
>>> x * 2
20


```

For simple calculations, you wouldn't even need to know you were writing Python code.  But if you have a repetitive calculation you want to plug several numbers into, you can create a function for it (like square in the example above) pretty simply.

There are probably better options that aren't full programming languages, this is just what I use.

BTW that's cool you're in southern Alabama.  I haven't been there, but I guess it is pretty close huh?

---

### Post by gldearman on 2009-08-26
> **lykwydchykyn said:**
> If all you want to do are math calculations, learning the necessary syntax should take about 2 minutes.

How complicated is the math in question?

EDIT: then again, you didn't want to have to enter a shell, so python would not be what you're looking for.

Well, the math is not complicated, mostly simple multiplication and division to 2 or 3 decimal places.  And I really should learn python, at least a little.  But I had been hoping that there was something already written for this.

> **HymnToLife said:**
> ```

firas@itsuki ~ % echo "2+2" | bc

```

Yep, that would be bizarre and arcane.  That's how I'm doing it now.  Stuff like:

```
echo "scale=3; 850/1333" | bc
```

Not exactly intuitive.  Thanks, though.

---

### Post by Bachstelze on 2009-08-26
> **gldearman said:**
> Not exactly intuitive.  Thanks, though.

Define "intuitive"... Were you thinking you could just type "2+2" at your shell? The two ways I told you are the most simple ones.

---

### Post by gldearman on 2009-08-26
> **Simian Man said:**
> ```
[finlayso@splinter ~]$ python...

```

For simple calculations, you wouldn't even need to know you were writing Python code.  But if you have a repetitive calculation you want to plug several numbers into, you can create a function for it (like square in the example above) pretty simply.

Well, that does look pretty easy.  Answer me one question, though.  When I exit the python shell, the things I typed into that shell will remain on my screen, right?

<aside>
> **Simian Man said:**
> ```
[finlayso@splinter ~]$ python...

```
BTW that's cool you're in southern Alabama.  I haven't been there, but I guess it is pretty close huh?

No, I'm in Tallahassee, too.  You've never heard it called "LA?"  Usually by people who have just moved here, in the context of, "I thought Tallahassee was in Florida, but it turns out I moved to LA -- Lower Alabama."
</aside>

---

### Post by Bachstelze on 2009-08-26
> **gldearman said:**
> Well, that does look pretty easy.  Answer me one question, though.  When I exit the python shell, the things I typed into that shell will remain on my screen, right?

Yes. But you could've tried yourself and found out. ;)

---

### Post by gldearman on 2009-08-26
> **HymnToLife said:**
> Define "intuitive"... Were you thinking you could just type "2+2" at your shell? The two ways I told you are the most simple ones.

```
bc 2+2
```

Would be intuitive.  But bc don't work that way.  Echoing a string and piping it to bc is a bit cumbersome, which is why I had hoped for something better.

I had kinda hoped for something worked more like:

```
$calc 2+2
4
$
```

Assuming that the command is "calc."  And, now that I think about it that way, and do a package search for "calc" there [does actually appear to be something in the repos]("http://packages.ubuntu.com/jaunty/apcalc") that does that. At least, it does if I'm reading the man page right. So, I think you just solved my problem just by making me think about it in a different way!  Thanks!

Has anyone here tried apcalc?

---

### Post by gldearman on 2009-08-26
> **HymnToLife said:**
> Yes. But you could've tried yourself and found out. ;)

Sadly, I'm at work, and my employer only uses WinXP, despite the fact that all of the IT staff recommend a switch to Linux wherever possible.  So it would've been 6 or 7 hours before I could get home and try it.

---

### Post by Bachstelze on 2009-08-26
> **gldearman said:**
> 
Has anyone here tried apcalc?

Seems to do just that:

```
firas@iori ~ % calc 2+2
        4
firas@iori ~ % calc 24000/1001
        ~23.97602397602397602398

```

---

### Post by gldearman on 2009-08-26
Awesome!  Thanks!

---

### Post by Simian Man on 2009-08-26
Oh I see what you are after now.  You can write yourself a script that would just pipe all your calculations into bc:

```

[finlayso@splinter ~]$ cat calc 
#!/bin/bash

echo $@ | bc
[finlayso@splinter ~]$ calc 2 + 2
4

```

The only trouble with that is that any eg. variables you create wouldn't be preserved across calls.

---

### Post by XCan on 2009-08-26
Octave? That should suit all your calculation needs. Easy syntax, 'clone' of Matlab.

---

### Post by gldearman on 2009-08-26
> **Simian Man said:**
> Oh I see what you are after now.  You can write yourself a script that would just pipe all your calculations into bc...
The only trouble with that is that any eg. variables you create wouldn't be preserved across calls.

Yeah, that was going to be my next step.  But I figured I oughta see if it had already been done.  That would've been a lot of trouble, and I'd rather the trouble of coding that belong to someone else, even if it is just a simple script.

> **XCan said:**
> Octave? That should suit all your calculation needs. Easy syntax, 'clone' of Matlab.

Easy syntax? Really?  I had looked at Octave, and using it for my purposes seemed like using the space shuttle to pick up milk from the corner store.  Maybe it's just that the project homepage is intimidating.  I'll give it another look.

---

### Post by XCan on 2009-08-26
Hehe, well I didn't know how advanced stuff you wanted to do. Octave and Matlab are of course designed to be able to handle quite advanced scripts, which I suspect is a huge focus on their homepage. But even for simple stuff, defining variables, arrays, matrices and running operations on them just can't get any simpler.

---

### Post by kaibob on 2009-08-26
You could use bc (as previously suggested) and add something like the following to the bashrc file. You could dress up the output with printf if desired. 

```
tcalc ()
{
   calc=$(echo "scale=2; $1" | bc -q 2>/dev/null)
   echo "$calc"
}
```

---

### Post by Dullstar on 2009-08-26
I wrote this one.

[http://www.mediafire.com/download.php?psymbm1hd0x](http://www.mediafire.com/download.php?psymbm1hd0x)

It has a bit of an interface.

You MIGHT need to follow the directions in the quote.  I don't know the fact that I ran it on MY machine is going to work for everyone else.

This quote helped me get it working.

Quote from **OutOfReach**
> 
Ok the #!/usr/bin/env python is in the right place, but I meant inserting the command

```
chmod +x my_file.py

```
into the command line, not into the file, sorry about the confusion.

Remember to give the CLI the path to the file as well.  It *might* not need it, I don't remember, but it probably does need it.

---

### Post by Dullstar on 2009-08-26
I forgot to mention that it does run in the command line!

---

