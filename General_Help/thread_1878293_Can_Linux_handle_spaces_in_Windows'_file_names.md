---
title: "Can Linux handle spaces in Windows' file names?"
date: 2011-11-09
forum: General Help
---

### Post by Randy Schilling on 2011-11-09
I'm running Ubuntu 11.10 on one hard drive and Windows 7 on another hd.
W7 was installed first, then U11.10 with grub2 going to the W7 hd, which is 
my default boot drive.

I've installed TeXLive under U11.10 (and W7).  As part of the installation, you have to define
an environment variable called TEXINPUTS in the file ~/.profile; this so you can input
your TeX macro files into your primary TeX file.


My problem is this. Some of my TeX macros are located on my W7 drive under the folder
Documents and Setting and I think Linux does not like the spaces in my entry; namely,
export TEXINPUTS=.:/media/8A467EB6467EA29D/Documents and Settings/Randy/texmf/tex/plain/generic,
to my ~/.profile file.
When I try to update my current bash terminal with the command source ~/.profile, bash complains
saying "not a valid identifier".

What do I have to do to make this work?  I don't want to duplicate copies of my TeX macro files;
that can be confusing, can't always remember to update changes from one drive to the other,
especially because W7 can't see my Ubuntu hard drive.
It would be better if Linux could deal with blank spaces in names like Documents and Settings.  
Is that possible?

I could move the macros on my W7 drive to a location whose name contains no blanks spaces.
But I'd still like you to tell me if Linux can handle spaces before I do that. 

Many thanks and regards - Randy

---

### Post by SamusAran on 2011-11-09
Hi Randy, Im new to the forums, but I have a suggestion. Its been my experience in ubuntu that if you delimit a space with a \ in a file name this works rather well, and ubuntu seems to understand it. for instance, I have a folder in my home directory called Rise Against - End Game. if I want to cd into this folder and look at my music files, i type cd /home/samus/Downloads/Rise\Against\-\End\Game.  I hope this helps. 
Good luck, Samus.

---

### Post by 1clue on 2011-11-09
Spaces are handled differently depending on what "application" you're using.

Generally speaking, you can quote the filename.

cat 'hello world.txt'

you can also escape the spaces:

cat hello\ world.txt

Those both work from bash.

---

### Post by Seb71 on 2011-11-09
I do not kow what the problem is, but it is not spaces in file or folder names.

In Windows XP at least, you can not have a file name or a folder name starting with . (dot).

---

### Post by jocko on 2011-11-09
> **Seb71 said:**
> I do not kow what the problem is, but it is not spaces in file or folder names.

In Windows XP at least, you can not have a file name or a folder name starting with . (dot).
No-one here has said anything about trying to make a filename with a leading dot in windows (which works perfectly well in windows XP, vista and 7, you just can't create the file from the gui... the command line have no problems with it.). The ~/.profile file is in Randy's home folder (~/) in his linux system, and leading dots in filenames are very well supported in linux. The problem is that bash (or any other shell) have no way to know that the path "media/whatever/Documents and Settings/bla" (when written without the quotes) is one path and not three different paths ("media/whatever/Documents", "and" and "Settings/bla")...

@Randy: The question has been answered, but I repeat the solution here just to make it clear:
Either just put the whole path in quotes:
```
export TEXINPUTS=.:[COLOR=Red]**"**[/COLOR]/media/8A467EB6467EA29D/Documents and Settings/Randy/texmf/tex/plain/generic**[COLOR=Red]"[/COLOR]**
```Or escape the spaces:
```
export TEXINPUTS=.:/media/8A467EB6467EA29D/Documents[COLOR=Red]**\**[/COLOR] and[COLOR=Red]**\**[/COLOR] Settings/Randy/texmf/tex/plain/generic
```

---

### Post by Randy Schilling on 2011-11-09
Hey that works and its simpler then I had hoped.
Thanks all.
Thanks Jocko, I appreciate the detailed follow-up on my example.

Many thanks and regards - Randy

---

### Post by dcstar on 2011-11-12
> **jocko said:**
> No-one here has said anything about trying to make a filename with a leading dot in windows (which works perfectly well in windows XP, vista and 7, you just can't create the file from the gui... the command line have no problems with it.).
.........

NTFS **cannot** have any file descriptor with a leading ".", that is an illegal character in NTFS.

Linux filesystem do not have this restriction, this is why so many people have problems trying to use NTFS with Linux applications.

If this thread is **Solved** then mark it as such.

---

### Post by 1clue on 2011-11-12
> **dcstar said:**
> NTFS **cannot** have any file descriptor with a leading ".", that is an illegal character in NTFS.

Linux filesystem do not have this restriction, this is why so many people have problems trying to use NTFS with Linux applications.

If this thread is **Solved** then mark it as such.

If that's true then it's remarkably easy to break the restriction.  I do it all the time at work.

The restriction is in the GUI tools that let you choose filenames.  It's convention, not a rule.

---

### Post by jocko on 2011-11-12
> **dcstar said:**
> NTFS **cannot** have any file descriptor with a leading ".", that is an illegal character in NTFS.

Linux filesystem do not have this restriction, this is why so many people have problems trying to use NTFS with Linux applications.

If this thread is **Solved** then mark it as such.
This is way of topic, but there is no such restriction in the NTFS file system. As I said, the windows command line have no problem creating files or folders with leading dots in their names. The problem is that the graphical interface in windows is set to interpret everything before the first dot as file name and whatever comes after the dot as file extension, so it will not let you create a file starting with a dot, since it looks like you forgot to add a file name before the extension... But the windows gui has no problems whatsoever *opening* files or folders with leading dots. I guess it's really just a feature designed by Microsoft to prevent people from mistakenly saving files with only an extension and no proper file name...

---

### Post by Morbius1 on 2011-11-12
The only "illegal" filename characters I am aware of are these:
> ” * / : < > ? \ | And you can prevent Linux from saving file names with those characters by adding the "windows_names" option in fstab.

---

### Post by Matti L on 2011-11-12
GIMP and VirtualBox store their settings in .gimp-2.6 and -.VirtualBox folders instead of AppData in Windows, but there seems to be no problems with using them. I've also used filenames starting with dot so I could hide them in both Windows and Linux.

---

