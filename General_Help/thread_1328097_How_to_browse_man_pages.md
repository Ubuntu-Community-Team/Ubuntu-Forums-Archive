---
title: "How to browse man pages?"
date: 2009-11-16
forum: General Help
---

### Post by OldGrantonian on 2009-11-16
I would be grateful for instructions on how to browse the man pages. Here is what I do:

1)  In the Firefox search engine tool, select "Ubuntu Manpage Search"
2)  Enter a command (for example, "ps")
3)  In the column for Karmic, click ps(1)

I get the page:
[http://manpages.ubuntu.com/manpages/karmic/en/man1/ps.1.html](http://manpages.ubuntu.com/manpages/karmic/en/man1/ps.1.html)

The page contents are:

----------------------
karmic (1) - ps.1.gz
Provided by: procps_3.2.8-1ubuntu3_i386 bug

Powered by the Ubuntu Manpage Repository generator
Maintained by Dustin Kirkland 
---------------------

Now, what am I supposed to do? If I try to open ps.1.gz using Archive Manager, I get something that looks like an nroff or troff file :)

---

### Post by emigrant on 2009-11-16
if you want to browse a man page of a particular command,
open a terminal and type:

```
man <command>
```

eg:

```
man ps
```

is that what you were looking for?

---

### Post by megamania on 2009-11-16
or try this:

[http://linux.die.net/man/](http://linux.die.net/man/)

---

### Post by OldGrantonian on 2009-11-16
> **emigrant said:**
> if you want to browse a man page of a particular command,
open a terminal and type:

```
man <command>
```eg:

```
man ps
```is that what you were looking for?

That's useful, but on the following web page:
[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)

why does it say "web-browsable"?:
> 
Traditionally, [manpages]("http://en.wikipedia.org/wiki/Manpage") are browsed on the command line.  This project renders all such manuals included in Ubuntu in an HTML, web-browsable format.
> **megamania said:**
> or try this:
[http://linux.die.net/man/](http://linux.die.net/man/)

Very useful link :)
.

---

### Post by t0p on 2009-11-16
The OP's right, I went to [http://manpages.ubuntu.com]("http://manpages.ubuntu.com/") and searched for the manpage of 'ps' for Karmic... it eventually took me to a link to download ps1.gz - which is not the same as browsing the ps manpage online.

I've never tried this site before.  I look at manpages in the terminal, and tbh I prefer the terminal service.  But if you're like the OP and want to browse manpages online, the Ubuntu online manpage project needs to sort its site out a touch.

---

### Post by sgosnell on 2009-11-16
Beside the search box, there are 3 buttons.  Click on the Text button to see the actual man pages, which show up in the same format as a Google search.  The Title button, which for some reason seems to be the default, isn't the one you want.  The third button lets you select the language.

---

### Post by martinkingsley on 2009-11-17
I am getting the same behaviour, end up with .gz file rather than the man page displayed in firefox. **This has changed in the last few weeks**, it used to display the man page as described.

I tried pressing the Text button and white space is displayed.

So I think something has broken...

---

### Post by sgosnell on 2009-11-17
I get what I expect, not whitespace.  That's all I can say.

---

### Post by crazy ivan on 2010-01-08
Hey guys. Making use of the power of a *search function* with highlighting, a *percentage bar* and lots of other things make sense..

So please check out the incredibly easy solution by ushimitsudoki

[http://meandubuntu.wordpress.com/2007/12/28/using-firefox-to-view-html-man-pages/]("http://meandubuntu.wordpress.com/2007/12/28/using-firefox-to-view-html-man-pages/")

This saves traffic compared to using any online repository and is way nicer than FireMan

[https://addons.mozilla.org/en-US/firefox/addon/8709]("https://addons.mozilla.org/en-US/firefox/addon/8709")

---

### Post by crazy ivan on 2010-01-08
yeah.. and don't miss out on nice features like "fulltext man page search", when you click on "Return to Main Contents" ;)

---

### Post by Leppie on 2010-01-08
i am getting the normal man page as well (with at the top the link to download ps.1.gz)

---

### Post by luigi_mb on 2010-01-08
> **Leppie said:**
> i am getting the normal man page as well (with at the top the link to download ps.1.gz)

There is also a much simpler way. In a console just type

```

man -H man

```

Replace the second 'man' with the name of the command you are interested in.

Your default browser will display the output. You can also create an alias--say, "manh"--in your ~/.bashrc :

```

alias manh ='man -H'

```


/luigi

---

### Post by Leppie on 2010-01-08
Some other sites hosting man pages:
[http://swoolley.org/man.cgi](http://swoolley.org/man.cgi)
[http://man.he.net/](http://man.he.net/)
[http://linuxmanpages.com/](http://linuxmanpages.com/)
[http://www.kernel.org/doc/man-pages/online_pages.html](http://www.kernel.org/doc/man-pages/online_pages.html)

---

### Post by kc8hr on 2010-05-21
When I type 'man man' I get the following error:

man: can't execute /usr/X11R6/bin/most: No such file or directory

What is going on here?

---

### Post by sgosnell on 2010-05-21
There is no man page for 'man'.  It tries to run the 'man' command on itself, and that gives the error. Try 'man woman'.  You only get a man page for commands for which there is a manual entry.

---

### Post by kc8hr on 2010-05-22
> **sgosnell said:**
> There is no man page for 'man'.  It tries to run the 'man' command on itself, and that gives the error. Try 'man woman'.  You only get a man page for commands for which there is a manual entry.
Sorry, but there most certainly *is* a man page for the 'man' command:

> <tim@dojo|/home/tim>$ man man

MAN(1)                        Manual pager utils                        MAN(1)



NAME
       man - an interface to the on-line reference manuals. . .


The 'man' command is broken in the default Lucid installation. Here is the problem:

> man: can't execute /usr/X11R6/bin/most: No such file or directory

The solution is:

sudo mkdir /usr/X11R6/bin
ln -s /usr/bin/most /usr/X11R6/bin/most

For some reason the directory structure was changed from earlier releases of Ubuntu.

Later--
Tim

---

### Post by sgosnell on 2010-05-22
Well I'll be.  I never thought to try reading the man page for man.  On my installation, there was no need to do anything, it just worked.  I have no /usr/X11R6/bin directory, but the 'man man' command runs fine, without any tweaking.

---

### Post by kc8hr on 2010-05-22
> **sgosnell said:**
> Well I'll be.  I never thought to try reading the man page for man.  On my installation, there was no need to do anything, it just worked.  I have no /usr/X11R6/bin directory, but the 'man man' command runs fine, without any tweaking.

lol, beats me--guess I just upgraded on a bad day.

Later--
Tim

---

