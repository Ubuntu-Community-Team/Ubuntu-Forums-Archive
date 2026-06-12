---
title: "Make Nautilus Actions show Terminal Window?"
date: 2010-03-15
forum: General Help
---

### Post by qyot27 on 2010-03-15
So, I have the action I want to use set up correctly and it does work, but I really want the Terminal window to appear so that the progress meter for the program is visible - as it is right now, it doesn't show up, and therefore if the work is going to take a long time there's no indication of that.  I'd ideally like the Terminal to open automatically, and when the process/script is done, close.  Is there any way to make this work with Nautilus Actions?

---

### Post by Devport on 2010-03-15
I have not tested it but maybe it is as easy as using "gnome-terminal -e YOURCOMMAND". This should launch a gnome-terminal which will terminate after the command has been executed.

---

### Post by qyot27 on 2010-03-15
Unfortunately it seems it isn't conducive to that.

If I specify *gnome-terminal -e [path_to_executable]* in the Path area, then the Terminal does indeed show up, but it immediately disappears, and the operation fails.  The parameters to specify where the input files are is elsewhere.  Maybe it'd work how I want it if I put the gnome-terminal command in a shell script.  I need to write one anyway, since I'm going to expand the scope of what this command does.

EDIT: Nope, seems trying to do it from a shell script didn't work.  I'll explain more of what I'm doing in the next post.

---

### Post by Devport on 2010-03-15
Try these settings :

Path :
```
/usr/bin/gnome-terminal
```
Parameters :
```
-x YOURCOMMAND YOURPARAMETERS_EG_%f
```

Edit : I meant -x not -e, see man gnome-terminal

---

### Post by qyot27 on 2010-03-15
Nevermind.  It works, but apparently Nautilus Actions doesn't like using $HOME as a synonym for /home/username

---

### Post by qyot27 on 2010-03-15
So now, I have a second question:
How can I fix a shell script to do this and generate a custom text file so that %d/%f are interpreted as the filename I gave the shell script, and not actually as %d/%f?  Currently, I have this in a file called mkvindex.sh:
```
# !/bin/bash -x
gnome-terminal -x /home/qyot27/ffms2_build/bin/./ffmsindex %d/%f
echo FFmpegSource2\("%d/%f"\)>"%f".avs
```
But if I run, say,

./mkvindex.sh videofile.mkv

It fails because it's interpreting the %d/%f inside the script as %d/%f and not replacing it with videofile.mkv's path/filename.  The generated .avs file is also rendered as %f.avs instead of videofile.mkv.avs.

---

### Post by Devport on 2010-03-15
You cant use the variables inside a script with %f etc. The parameters are passed to the script as command line parameters. The first parameter ( e.g. %f ) will be referred to as $1 in the shell script. $2 is the second parameter, $@ are all parameters passed to the script. For more details on this I would recommend to read the advanced bash scripting guide.

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
[http://tldp.org/LDP/abs/html/internal.html#ECHOPARAMS](http://tldp.org/LDP/abs/html/internal.html#ECHOPARAMS)

It may be enough to use $1 instead of %f and $2 instead of %d - but put the variables in quotation marks ( e.g. %d/%f -> "$1/$2" ) since the variables / file names and paths may contain white spaces and would be interpreted as separate parameters otherwise.

---

### Post by qyot27 on 2010-03-15
In the script:
```
# !/bin/bash -x
#gnome-terminal -x 
ffmsindex "$1"
#echo FFmpegSource2\(\"$1\"\)>"$1".avs
```

What it returned:
```
Indexing, please wait... 0% 

'ndexing error: Can't open 'videofile.mkv
```

On the plus side, though, if the echo line is not commented out, the .avs file is generated correctly.  So at least I know that part's right.

If I'm interpreting the rest correctly, if I give on the Terminal:
./mkvindex.sh videofile.mkv

Then the $1 references in the script are replaced with 'videofile.mkv' (and considering that echo line, it strongly looks like that's the case).  Shouldn't this be good enough if you're only working with relative paths?  Doing $2/$1 or $1/$2, with or without double-quotes around them resulted in similar errors about not being able to open the file.

---

### Post by mc4man on 2010-03-18
Don't know if this would work or what you had in mind at all (r.click on file, execute in a terminal..?, does something like this do any better?


```
#!/bin/bash 
gnome-terminal -e  "ffmsindex "$1""
echo FFmpegSource2\(\"$1\"\)>"$1".avs
```

---

### Post by qyot27 on 2010-03-18
> **mc4man said:**
> Don't know if this would work or what you had in mind at all (r.click on file, execute in a terminal..?, does something like this do any better?


```
#!/bin/bash 
gnome-terminal -e  "ffmsindex "$1""
echo FFmpegSource2\(\"$1\"\)>"$1".avs
```
I actually just figured out the issues.  The above might work correctly now, but even if I had copied it and attempted before I got onto the issue, it would have failed too.  See point B)

A) I had neglected to remember not to put a space between the # and !, so the -x parameter (which shows the individual commands in the script instead of making the output run together) wouldn't work correctly.

B) The other, immediate problem for the ffmsindex line, is the fact that apparently gedit hadn't eliminated all the carriage returns in the file as I was editing it.  The ffmsindex line still had CRLF, whereas all the others were just LF - as I'd initially just copied the script over from Windows, this was the problem (I'd even attempted to figure out what was wrong by trying it in my MSys environment, which worked fine because MSys recognizes both CRLF and LF line endings).

So I simply used fromdos and the script began to work as expected.



Then, all I had to do was amend the Nautilus Action to point at the script rather than the programs.  So it all works as expected now.

---

