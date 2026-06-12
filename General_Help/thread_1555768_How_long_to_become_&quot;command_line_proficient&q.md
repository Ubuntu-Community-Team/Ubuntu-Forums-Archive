---
title: "How long to become &quot;command line proficient&quot;"
date: 2010-08-18
forum: General Help
---

### Post by Raptors on 2010-08-18
Hi, I'm new to this forum and linux but have been reading a book on linux.  Anyway, I want to run a ecommerce website powered by Magento.  I've been looking into hosting and contacted Rackspace about there cloud server plan.  The rep said they advise that for me to be "command line proficient" in linux.  So I was wondering how long you think it would take for me to become "command line proficient".   Any help would be much appreciated.

---

### Post by gdonwallace on 2010-08-18
Well dude, that is quite a loaded question.

There are lots of books and online information on how to use the Command Line.  But it really just comes down to doing it.  I have used Linux for 3 years and Unix for 7, and don't consider myself "Command Line Proficient" 
To give an example, from the command line type man tar and press enter.  This is basically a "manual" page on the tar command and all the different options it has and how to use it.  Each command in Linux has a man page and some are just ginormous.  

Not to rain on your parade, but it takes time and usage to become comfortable using the command line.  Be proficient is a personal call.  I consider myself pretty good with the command line, but thats just me.

Check out [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/) for a list of linux commands and the MAN pages to go with them, then just get down and dirty and start using it.  Thats the only way.

---

### Post by Vaphell on 2010-08-18
not that long, of course it depends on what the criteria are :-)
Try to solve majority of your problems with command line: learn how to navigate/copy/move/delete, how to use tab key autocompletion to speed it up greatly, generally familiarize yourself with what is where in linux, learn how to fix permission issues, what is sudo/gksudo for, how to write your own scripts to automate your frequently repeated tasks...

**man <command>**
or **<command> -h** / **<command> --help**
to check what is the syntax and what options that command has to offer

[http://bharatikunal.files.wordpress.com/2008/10/linux-wallpaper-for-beginners.jpg](http://bharatikunal.files.wordpress.com/2008/10/linux-wallpaper-for-beginners.jpg) this is a good start :-)

---

### Post by scorp123 on 2010-08-18
> **Raptors said:**
> So I was wondering how long you think it would take for me to become "command line proficient".  I have had IT apprentices (around 19 years old, fresh out of school) who were able to understand an incredible lot of it in less than a week ... And a few months later it is me --their "godfather" tutor-- who has to ask them for advice!! :lolflag:

And then I have had other apprentices whom we have trained for three or four years and they still don't get it. They still ask me things for which they could easily find the answers if only they remembered the "man" command to get to the manual or if only they simply used Google ...

In other words and to second what the poster above me already said: It so totally depends on you.

Best thing is to use Linux day and night on lots of machines and learn how to install things via the console ... that's where and how you get "proficient": by using it, day and night.

---

### Post by Vrroom on 2010-08-18
Try clicompanion...its a GUI for terminal....it comes with many presets and you can define your own too. Go here: [https://launchpad.net/clicompanion](https://launchpad.net/clicompanion)

---

### Post by wyliecoyoteuk on 2010-08-18
If you are using it all the time, not long.
If like me, you use it now and again, just remember <command> --help, (works most of the time for me), followed by man <command> followed by Google <command>+Linux.

Practicing on a machine without a GUI helps :)

This, although a little dated, is a good start:

[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

---

### Post by Zorgoth on 2010-08-18
If you are trying to learn the command-line (or any piece of software) without having a real-world problem to apply it to, it will take a long time.  But you will find that doing real world problems you will figure things out much faster I think.

Best tricks for learning the command line:

<command> --help
man <command>
For bash specific commands and bash syntax, use "man bash" or "help command" - e.g. there is no "man bg" because that is part of bash - but there is a "help bg"

Type an initial segment of what you think a command might be and type <Tab> once to autocomplete up to hte next place where there is more than one match and once more to display all matches.

My favorite CLI tool its probably "find."

For example, let's sat you have 1000 files named ck1.mat through ck1000.mat in a folder with 5,000 other files.  This is a kind of situation I meet regularly because of the kind of problems I deal with.

Let's say you want to sftp this to another copmuter.  sftp has a very minimal interface and copying 1,000 files would be difficult.

But with find:
```

mkdir ckdir //create a directory called ck where you are
find -name 'ck*' -exec cp {} dirck \; //this finds everything in the directory whose name matches ck* (* is any string), and the -exec option executes the command 'cp {} dirck' where {} is a shortcut for the name of the file you are acting on - so this will copy all the files from ck1.mat to ck1000.mat to the directory ./dirck.
  
// you can also use -execdir instead of exec to execute from a files parent directory (find searches all subdirectories and returns complete paths relative to the target directory, which in my example is unspecified and therefore is just ., the current working directory)
tar -cf ck.tar dirck //create an archive of dirck

```

Then all you have to do to upload ck.tar to another computer is:

```

sftp remote_user@remote_computer.remote_domain
<enter password>
put -P /full/path/to/ck.tar /remote/destination/for/ck.tar
exit

```

In the time it would take you to execute all these command, nautilus would likely not have even finished loading the current directory.

I would also recommend learning regular expressions.  They are described pretty well in "man grep."  grep and sed are two very useful commands that use them regularly.

Also make sure you understand piping (|), command substitution (`<command>`), parameter expansion ($<variable>), bash arithmetic 
($(( 1 + 1 )) is 2!), bash conditionals (e.g. [[ $myvariable == '' ]] tests for whether a variable is empty - use it after an if or while command), and bash if, for, and while loops.

EDIT: lol if is not a loop

EDIT2:  Changed ./ck to ./dirck, since find -name 'ck*' would match the directory ck, which we do not want.  It does not match dirck - find -name '*ck*' would match dirck, but simply find -name 'ck*' will not

---

### Post by mamohamedali36 on 2010-08-18
It took me just one week, cheer up

---

### Post by Renderd on 2010-08-18
Hello, new user here... but i have to say that the best way to learn is defiantly the man <command> and <command> -help, those save me and when im stuck i grab google and pretend to be its best friend for a moment hugging it and loving it... until i find what im looking for then i push it away make sure everything runs right then close it till i need it again... what can i say... the google cant resist

:P

---

### Post by wesg on 2010-08-18
You never quite know everything, but that's what the internet is for. 

I'd say if you can handle things like software installs, compiling from source, vi, directory navigation and file manipulation (copy, move, rename, etc.) you're good to go.

---

### Post by uRock on 2010-08-18
Grab an Intro to UNIX/Linux book from a library or book store and have at it.

---

### Post by Zorgoth on 2010-08-18
> **wesg said:**
> You never quite know everything, but that's what the internet is for. 

I'd say if you can handle things like software installs, compiling from source, vi, directory navigation and file manipulation (copy, move, rename, etc.) you're good to go.

If you know vi, then you have to take all the time to unlearn vi and learn emacs :o

- so vi is negative proficiency

---

### Post by scorp123 on 2010-08-18
> **Zorgoth said:**
> - so vi is negative proficiency Strongly disagree.

If there is one editor in the Unix world you *_DEFINITELY_* *_WILL_* encounter on *_ANY_* Unix-like OS ... then it's stupid old "vi".

Sun Solaris 9? => vi
Sun/Oracle Solaris 10? => vi
FreeBSD? => vi
most Linuxes? => vi
IBM AIX? => vi
HP-UX? => vi

If you learn "vi" (just a few basic things will do tip top) then this will at least make sure you will definitely be able to edit files, no matter what Unix-like OS gets thrown at you.

Emacs? Sorry, but in my entire career I have not a single time encountered a server installation with Emacs on it. But "vi" definitely will be there "out of the box".

---

