---
title: "Small Basic (Microsoft)"
date: 2010-06-22
forum: General Help
---

### Post by Hosmion on 2010-06-22
Hello everyone.  I am trying to get Small Basic on Ubuntu but it isn't letting me get it.  I tried to download it, and it popped up with that install window.  But, when I hit next after I add everything I need, it stops because of an error.  Is there a version of Small Basic for Ubuntu?

---

### Post by kellemes on 2010-06-22
You have downloaded the Debian-package from the [download page]("http://smallbasic.sourceforge.net/?q=node/195")?

So what's the error you're getting?

---

### Post by bodhi.zazen on 2010-06-22
> **Hosmion said:**
> Hello everyone.  I am trying to get Small Basic on Ubuntu but it isn't letting me get it.  I tried to download it, and it popped up with that install window.  But, when I hit next after I add everything I need, it stops because of an error.  Is there a version of Small Basic for Ubuntu?

[http://smallbasic.sourceforge.net/?q=node/195](http://smallbasic.sourceforge.net/?q=node/195)

Why not learn a linux native language such as bash , perl, etc, etc ?

---

### Post by Hosmion on 2010-06-23
@Kell - Not SmallBASIC, this [Small Basic]("http://smallbasic.com/").  I have been using this for a while and I would like to continue using it.  In SmallBASIC, it saves as like .dos or something like that and that is not what I am looking for.  They aren't the same thing (or as I think) for two reasons:

1) The suffix is not .sb or .smallbasic
2) The commands of Small Basic are different.

@Bodhi - I might learn a Linux based language, I don't know just yet.

Where might I find really good Perl tutorials?

---

### Post by bodhi.zazen on 2010-06-23
> **Hosmion said:**
> @Kell - Not SmallBASIC, this [Small Basic]("http://smallbasic.com/").  I have been using this for a while and I would like to continue using it.  In SmallBASIC, it saves as like .dos or something like that and that is not what I am looking for.  They aren't the same thing (or as I think) for two reasons:

1) The suffix is not .sb or .smallbasic
2) The commands of Small Basic are different.

@Bodhi - I might learn a Linux based language, I don't know just yet.

Where might I find really good Perl tutorials?

Google search python, perl, etc ...

See also :

[http://ubuntuforums.org/showthread.php?t=1516296](http://ubuntuforums.org/showthread.php?t=1516296)

			                          			 			[Programming Tools and References]("http://ubuntuforums.org/showthread.php?t=1006662")

---

### Post by Hosmion on 2010-06-23
I'm going to attempt to learn Python.  Does Ubuntu come with Python already?  If it doesn't where can I download it because I don't see it on Python.org

---

### Post by s.fox on 2010-06-23
> **Hosmion said:**
> Where might I find really good Perl tutorials?

I always liked perl.com's introduction to the language. Some nice basics gone over in the 6 parts.  Part 1 is [here]("http://www.perl.com/pub/a/2000/10/begperl1.html").

If you decide to go down the Python route I highly recommend [A Byte of Python]("http://www.ibiblio.org/g2swap/byteofpython/files/120/byteofpython_120.pdf")

-Silver Fox

---

### Post by bodhi.zazen on 2010-06-23
> **Hosmion said:**
> I'm going to attempt to learn Python.  Does Ubuntu come with Python already?  If it doesn't where can I download it because I don't see it on Python.org

Yes python is installed by default.

---

### Post by Hosmion on 2010-06-24
What notepad should I use to write Python programs?  I don't know how to execute them and using SciTE doesn't make it easier.

---

### Post by bodhi.zazen on 2010-06-24
> **Hosmion said:**
> What notepad should I use to write Python programs?  I don't know how to execute them and using SciTE doesn't make it easier.

Graphical options include gedit and cream (graphical front end for vim).

In a terminal many people use vim, nano, or emacs.

---

### Post by Hosmion on 2010-06-24
> **bodhi.zazen said:**
> Graphical options include gedit and cream (graphical front end for vim).

In a terminal many people use vim, nano, or emacs.
You execute the program in terminal?  How do I write something in gedit and use terminal to execute what I wrote in the notepad?

---

### Post by bodhi.zazen on 2010-06-24
In general, save the program in ~/bin, you will need to make the bin directory in your home directory.

Once you do that, your program will be on your path.

You then make the program executable

```
chomd a+x ~/bin/foo
```

then run it 

[/code]foo[/code]

---

### Post by Hosmion on 2010-06-24
Sorry.  I came back to Ubuntu two days ago and I have many questions...  Where is ~/bin?

---

### Post by bodhi.zazen on 2010-06-24
> **Hosmion said:**
> Sorry.  I came back to Ubuntu two days ago and I have many questions...  Where is ~/bin?

Read my post: 

> you will need to make the bin directory in your home directory.

```
mkdir ~/bin
```

---

### Post by Hosmion on 2010-06-24
Ok I got it :).  I have hopefully one last question about the syntax.

I wrote the line:

```
print "Hello World!"
```
And I tried to execute this by hitting "Run in Terminal" when the window pops up, but as soon as it opens it closes.  I did everything in terminal and it worked but it's not working.

Thanks!

---

### Post by bodhi.zazen on 2010-06-24
> **Hosmion said:**
> Ok I got it :).  I have hopefully one last question about the syntax.

I wrote the line:

```
print "Hello World!"
```And I tried to execute this by hitting "Run in Terminal" when the window pops up, but as soon as it opens it closes.  I did everything in terminal and it worked but it's not working.

Thanks!

Your program runs in a terminal, you did not write a graphical interface.

Programs start with a header #!/path/to/interpreter 

In you case, 

```
#!/bin/python

print "Hello World!"
```

If you run the program in a terminal you will see the output in a terminal.

If you try to run it graphically, you will see a terminal open, the output will flash by, and then the terminal will close.

---

### Post by Hosmion on 2010-06-24
Still doesn't work...  I made a directory in the home folder named ~/bin, then I made a sub directory named python and copied what you told me to into gedit, saved it, and double clicked it and hit run in terminal.  Can we use Teamviewer to fix this problem?

---

### Post by bodhi.zazen on 2010-06-24
> **Hosmion said:**
> Still doesn't work...  I made a directory in the home folder named ~/bin, then I made a sub directory named python and copied what you told me to into gedit, saved it, and double clicked it and hit run in terminal.  Can we use Teamviewer to fix this problem?

Why did you make a sub directory ?

If you do so, you will need to add the subdirectory to your path or use the full path when you call the script.

~/bin/python/foo

---

### Post by Hosmion on 2010-06-24
I made the sub directory because I thought in the statement ~/bin/python, python was a sub directory.  Ok, I'll delete it.  But still doesn't work.  This is the code:

```
#!/bin/python

print "Hello World!"
```

Can we use Teamviewer?

---

### Post by bodhi.zazen on 2010-06-24
change #!/bin/python to the full path to python

If you do not know it, use

```
which python
```

It may be in /usr/bin/python

See also :

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

