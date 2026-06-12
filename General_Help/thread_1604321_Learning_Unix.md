---
title: "Learning Unix"
date: 2010-10-23
forum: General Help
---

### Post by imotox on 2010-10-23
Ok, so I have been using Ubuntu on and off for about 2-3 years now and I'm still a "noob" when it comes to knowing much past the GUI. I'm in college and wondering if it is worth taking a Unix Course next semester or if there are other, cheaper ways that I can learn. I want to become fluent in the terminal, basic scripting (I know each programming language is different), and other areas.

Is there a book that you would recommend. If there is, how easy is it to learn from that book? Basically how easy is it for you to teach yourself with the book's help?

My goals that I want is to completely understand the desktop environment and hopefully even know how to work a server (even though I have no need for it right now, it could come in handy some day).

If you don't know a way, how did YOU "master" the Unix system?

---

### Post by lyall on 2010-10-23
get the Unix Bible or the Linux Bible

---

### Post by john77eipe on 2010-10-24
Same here.. 
Few weeks back I started using Linux (Ubuntu 10.04). 
It feels silly to bump every single question in forms.

---

### Post by sidzen on 2010-10-24
*Linux in Easy Steps* by Mike McGrath
*Linux in a Nutshell* by E.Siever,S. Figgins,R. Love and A. Robbins
*Slackware Linux Essentials*, at [http://www.slackbook.org/html/index.html](http://www.slackbook.org/html/index.html)

Suggestion:  learn to use the Command Line for Package Management, as a practical exercise.

---

### Post by krishnandu.sarkar on 2010-10-24
Ya go for Linux Bible. BTW you can also start with great reources that are available on internet.

---

### Post by efflandt on 2010-10-24
I got into Linux about 1995 when I had a SunOS dial up ISP with web space.  I got into Perl cgi scripts and it was easier to write them in Linux and simply upload then then to write Perl scripts in Windows and have to change all the paths and other things.

The Nutshell books are always good.

When trying to find your way around a text terminal two indispensable commands are **man** and **apropos**. If you are not sure what command to use, apropos can help you find commands that relate to a word, and which man pages to look at for more details.  Another useful command is **locate** to locate files.  updatedb runs from cron.daily to update the locate database.

Start with **man apropos**

man uses **less**, so you can use **/** to search for something within the man page or **q** to quit.

---

### Post by ankspo71 on 2010-10-24
Hi,
I bought the book called: "Ubuntu Linux Toolbox: 1000+ Commands for Ubuntu and Debian Power Users"
It is a book about commands that can be used in any Ubuntu/Debian based Linux distribution. It is not very difficult to read either, because it is all step by step with good explanations. It is an excellent starting point for me, I mean besides me reading the Linux support forums all the time:) 

They have some for other Operating Systems too, like other Linux Distros (Fedora, Suse, etc), BSD, Mac, etc. Here's a link to [_Amazon Search Results = Toolbox + Commands_]("http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Dstripbooks&field-keywords=toolbox+commands&x=0&y=0"). Most commands are used universally among all Linux distributions, so one book should suffice. The biggest difference in commands among different Linux distributions would be package management commands, but everything else would be typically the same. 
Hope this helps.

---

### Post by Ahava591 on 2010-10-24
**Unix Power Tools, O'Reilly**
-I use(d) the 2nd edition; I think it's in either its' 3rd or 4th edition now. The 2nd edition is kind to true beginners, those who are able to install an OS that has a graphical installer, use a keyboard, etc. (i.e., "noobs.")
It addresses a large number of situations, some common, some unlikely and provides clearly demonstrated ways of using Unix that are common to system administrators and advanced users. The 2nd edition also comes with a CD or DVD with the source code of all the scripts/programs in the book.

Relies heavily on command-line tools, (e.g. shell scripts and Perl.) Also covers both vi and Emacs. (Neither of which I use, so I don't worry about religious wars. The authors have wisely chosen to present the basics of both so that you are informed.)

**Unix in a Nutshell, O'Reilly**
-Very frequently suggested as being kind to beginners; it provides a solid overview and I recommend that it be in every Unix/Linux users' library.

**Classic Shell Scripting, O'Reilly**
-I haven't purchased this book yet. Instead, I run to the public library in my town and check it out approximately every other week when I run into a problem I haven't learned because I didn't buy the book and read it through. I believe this book is kind to beginners; if you learn the topic(s) covered in this book, you will be hard off to meet a scripting problem you're not equipped to deal with. (Which is not to say that you will never have to sit and use your imagination.) It will help you to understand why a lot of Unix/Linux scripts, commands, etc. are the way they are.

Provides thorough comparisons of commands that are treated differently by different operating systems. I think it's not even twenty pages into the book that you are shown the different ways in which "echo," is implemented.

**Learning Perl, O'Reilly**
It's on my desk as I type. Very kind to beginners of both computing and programming. I believe it should be in every Unix/Linux users' library. 

**Programming Perl, O'Reilly**
Once you finish **Learning Perl, **this book is a must. I do not believe it is kind to beginning Perl programmers; however, if you already know other scripting languages, or if you program really anything, you may be able to fly through **Programming Perl. **It should be added to your library at some point and kept there. Also, see **Advanced Perl Programming, O'Reilly. **



There's a reason why that company is behind every book I've listed so far. They have *the right stuff*.
 

See also,
"Ubuntu Linux Bible," (or any of the "Bible," series.)
and
"Beginning Ubuntu Linux."

I'm not a huge fan of Apress and Wiley books; but they provide a good base for you to learn from.

Good luck, hope to see you around.

---

