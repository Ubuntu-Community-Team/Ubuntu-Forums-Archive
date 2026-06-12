---
title: "Quick Q - File Searching"
date: 2011-08-01
forum: General Help
---

### Post by OldManRiver on 2011-08-01
All,

Windows search let's you find a string in a file.  Do not see this in the default Ubuntu file browser.  I there and add-in that allows for this?

Thanks!

OMR

---

### Post by OldManRiver on 2011-08-05
All,

Can I get some help?

Thought I was asking an easy Q.

Thanks!

OMR

---

### Post by OldManRiver on 2011-08-14
All,

I know I can write scripts to use "find" or "locate" pipe to file or stdout and then run cat on the files with grep to find things, but personally I think this should be a default feature of the "file browser" and hope you all agree.

Please chime in if you do, and if we need to open a ticket on this with the kernel guys, I will try to lead, but need your inputs here to determine if you are all behind me here.

Thanks!

OMR

---

### Post by OldManRiver on 2011-08-23
All,

Amazed there is not at least one response or comment here!

Thanks!

OMR

---

### Post by OldManRiver on 2012-02-17
All,

I'm not good at REGEX, but think that is what I need here.  If I make a search script and pass in say ".sql" I want to find all files on my system that have the .sql extension, so guess I need to learn how to do this in REGEX.

Cheers!

OMR

---

### Post by kjohri on 2012-02-17
1. Open a command line terminal like GNOME terminal.

2. cd some-directory.

3. find . -name "*.txt" | xargs grep "some-string" | more

Modify "*.txt" in the find command as per requirement.

---

### Post by 3rdalbum on 2012-02-17
A few years ago Ubuntu shipped with programs to do this, but as with most find-by-content systems they didn't work well and were a waste of space.

I think Google Desktop is still around. Give that a try and see how you go.

---

### Post by Khayyam on 2012-02-18
> **OldManRiver said:**
> I know I can write scripts to use "find" or "locate" pipe to file or stdout and then run cat on the files with grep to find things, but personally I think this should be a default feature of the "file browser" and hope you all agree.

I've never used a filebrowser as I generally find that in order to replicate the functionality of a shell the interface will become impractical. Think of how many 'switches' a search tool would need to impliment in order to replicate the capabilities of 'find', add in the fact that the output of find can be piped to other commands, glued together with the shells programability, and its next to impossible to impliment within a GUI without it become unwieldy. While a GUI can offer 'visual clues' as to how to operate it, it is no substitute for the user interface that is the mind of the operator. The analogy I use to describe the difference between a CLI and GUI is that with the former the 'interface' is internal to the user/operator, and external to the latter. There are distinct advantages to both dependent on how the computer is used, and the skill of the user, but as the users understanding, and needs, expand there are greater advantages to nesting the interface within the user.

I could give any number of examples of where this is the case: editing every file with a certain feature, within a given part of the filesystem. If you know how, its a no-brainer, if you don't and rely on the GUI to provide some clue as to how to go about it, it can be an agonising task.

So, while finding content from within a filebrowser is something like a "default feature" (we can assume everyone using the filebrowser will need to do this at some point), a filebrowser is less than optimal for this kind of thing (for reasons outlined above).

There is a place for filebrowsers, but I think they are fairly limited in what the can enable. Many filebrowsers (OS X, and probably Windows) catalogue the contents of the filesystem in order to make file content searches. I believe there are some similar 'engines' for linux and quite possibly some filebrowsers make use of them, but again I never use them, so perhaps others will be able to point you in the right direction.

> **OldManRiver said:**
> Please chime in if you do, and if we need to open a ticket on this with the kernel guys, I will try to lead, but need your inputs here to determine if you are all behind me here.

This is not an issue that the kernel developers have any part in, so I wouldn't go bugging them with feature requests. Everything that a filebrowser does takes place in "userland" and so its an issue for those who develop "userland" applications.

HTH ...

---

### Post by OldManRiver on 2012-02-21
All,

Here is sample of a script I'm writing to automate this. Have not tested it yet, so no "you dummy" comments please:
```
#! /bin/bash

# $1 ==> the path/file,
# $2 ==> the file search pattern, 
# $3 ==> the ext search pattern, 
# $4 ==> the oputput path/file.

if [ -z "$1" ] && [ -z "$2" ] && [ -z "$3" ]
then
    echo No parameters given.  You must give at least one of the three parameters:
    echo /n            path, filename, file-extension
    exit;
fi

if [ "$1"=="?" ]		# Test for existence of the path
then
    echo The correct syntax is:;
    echo /n     path (/mypath/), filename (myfilename), file-extension (myfile-ext with no .);
    exit;
fi

if [ -d "$1" ]		# Test for existence of the path
then
   cd "$1";
fi

if [ -z "$2" ]		# Test for existence of the filename
then
   "$2"="*";
else
   "$2"="*$2*";
fi

if [ -z "$3" ]		# Test for existence of the file-extension
then
   "$3"=".*";
else
   "$3"="*.$3";
fi

if [ -z "$4" ]		# Test for existence of the output file
then
   "$4"="/home/ff-results.txt";
else
    if [ -e "$4" ]
    then
	echo Found File "$4";
    else
        touch "$4";
    fi
fi

count=`egrep -ic "$2" "$1"`;
if [ $count -gt 0 ]
then
   find / -type f | grep "$1" | xargs grep -l "$2" | xargs grep -l "$3" >> "$4";
fi
# find /. -iname "*.sql" 
```

---

### Post by Vaphell on 2012-02-21
your find line looks extremely wasteful, care to explain what it is supposed to do exactly?
find / is definitely a bad idea, how often do you want to scan the whole system with thousands of files of no interest to you, the user? Usually you want to scan $HOME not /
locate can be of use, as it uses a database refreshed daily for fast search by name (sudo updatedb to refresh to account for recent changes)

and i think you should use descriptive variable names, instead of going with script parameters all the way.

---

### Post by OldManRiver on 2012-02-29
> **Vaphell said:**
> your find line looks extremely wasteful, care to explain what it is supposed to do exactly?
find / is definitely a bad idea, how often do you want to scan the whole system with thousands of files of no interest to you, the user? Usually you want to scan $HOME not /
locate can be of use, as it uses a database refreshed daily for fast search by name (sudo updatedb to refresh to account for recent changes)

and i think you should use descriptive variable names, instead of going with script parameters all the way.
Vaphell,

I think at this point we both need to explain ourselves.  For my part no I do not want to scan $HOME as I have an attached .5TB external drive where over 80% of my files reside and also I do not use /home for anything significant but are elsewhere on my system, such as /data contains all data and databases.

Also to eliminate long search times, I put in an argument for /path, so the search can be narrowed, if the exact directory is known.  But that is on the "grep" side so see what I think you are referring to.

Example of what I was trying to do when I started design of this, is developers on this machine have DB .sql files all over the place and they need to be moved or copied to the /data directory, with new subdirectories named after their project.  Most of their projects, over 80%, are web based off localhost so are in subdirectories under the main /var/www localhost directory, but have files scattered elsewhere.

I want to execute this script to capture the files and then read in the resulting file, create directories from the path where they were gleaned, and move them to their appropriate subdirectory under the /data main directory.

So you can see why I wanted the "/".  There may be a way to also make this a var and therefore limit searching, but will need to read more on the "find" command to make that work.  I do not use "find" often enough to know how to totally use all it's capabilities.

So now was were your objections to my syntax and/or choice of execution on the find?  Am I headed in the right direction?

Cheers and Thanks!

OMR

---

### Post by Khayyam on 2012-02-29
> **OldManRiver said:**
> [...]  For my part no I do not want to scan $HOME as I have an attached .5TB external drive where over 80% of my files reside and also I do not use /home for anything significant but are elsewhere on my system, such as /data contains all data and databases.

OK, but if you use "/" then /home is included in the find.

> **OldManRiver said:**
> Also to eliminate long search times, I put in an argument for /path, so the search can be narrowed, if the exact directory is known.  But that is on the "grep" side so see what I think you are referring to.

You may have thought you're optimising but the script uses "find /" ... which is what vaphell is refereing to. Basically it is "wasteful" because you first 'find /' and then grep $1 | grep | grep'. As 'find' can search on any number of criteria, from a stated directory tree, it can also --exclude, so grepping out a path is un-necessary and wasteful.

> **OldManRiver said:**
> Example of what I was trying to do when I started design of this, is developers on this machine have DB .sql files all over the place and they need to be moved or copied to the /data directory, with new subdirectories named after their project.  Most of their projects, over 80%, are web based off localhost so are in subdirectories under the main /var/www localhost directory, but have files scattered elsewhere.

I want to execute this script to capture the files and then read in the resulting file, create directories from the path where they were gleaned, and move them to their appropriate subdirectory under the /data main directory.

So you can see why I wanted the "/".  There may be a way to also make this a var and therefore limit searching, but will need to read more on the "find" command to make that work.  I do not use "find" often enough to know how to totally use all it's capabilities.

OK, but from your previous posts its seemed like you were trying to write an all purpose script "to automate this" (namely a "default feature of the file browser"). When I look at your script I think, ummm no, because I can see all kind of reasons why its either wasteful or not going to work as an all purpose tool. Now the focus has shifted and I think, ok, this is the first time your doing this kind of thing and so are probably not aware of some of the pitfalls and/or what tools might exist that would best suit the task at hand. Coupled with this I'm given pause to think with your comment "open a ticket on this with the kernel guys" WRT a "feature of the filebrowser", which leaves me a little awed that you are a sys admin. Thats not to say your not capable, I'm simply presenting the situation as I see it.

> **OldManRiver said:**
> So now was were your objections to my syntax and/or choice of execution on the find?  Am I headed in the right direction?

I would say no, for a start, rather than 'find | grep | grep | grep' you should be using a tool like [ack]("http://betterthangrep.com/"), you'll find some useful examples on [Perl Monks - Top 10 reason's to start using ack]("http://www.perlmonks.org/?node_id=586862"). If you compare 'find | grep' with ack you will see why most of your parsing *.sql could be much less wasteful.

Anyhow, I don't mean to sound nitpicky, I'm seriously trying to suggest a better approach, and where your current example is less than optimal.

HTH & best ... khay

---

### Post by Vaphell on 2012-02-29
just like khay said, it's wasteful because no matter what your find command will look into every corner of your harddrive(s) only to throw most of it away. That basic find / operation takes n seconds (where n can be non-trivial if you got tons of stuff) so you might want to limit directories to $HOME, /media and whatever dir you have your stuff in.
I doubt you want to scan all those shared libraries, icons, program settings and whatever happens to be located under / in system directories.
Granted, you may need to search them from time to time, but more often that not you don't as you care only about userspace stuff, so you really want to have a way to cut down the search space (eg. **find $dir1 $dir2 $dir3 <criteria>** will look into the listed dirs and list only stuff that matches). My $HOME suggestion was only an educated guess and if you want to extend that list, that's fine.

Piping output to input of another command is not free and shouldn't be done when one command can achieve the same effect by itself. You should take such things into consideration when you design your scripts, especially when they can take a lot of time to run because such inefficiencies add up.

If you list your desired functionality with greater detail, we will be able to suggest solutions and show you weak spots in the ones you concocted.
Either way *find <list of dirs> <criteria>* seems to cover at least half of your use cases so learn it. It doesn't make much sense to reinvent the wheel.

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #17 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

