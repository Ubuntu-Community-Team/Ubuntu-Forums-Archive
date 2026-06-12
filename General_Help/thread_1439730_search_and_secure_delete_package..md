---
title: "search and secure delete package."
date: 2010-03-26
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2010-03-26
is there a package that can search a hard drive for specific file types and securely delete them? with at least 4 passes.

i was using the wipe utility but there is no way to search the hard drive with it.

---

### Post by KeyserSoze93 on 2010-03-26
find / -name "*.doc"

(or whatever type you want to shred.) If it finds the files you want, then run:

find / -name "*.doc" -exec shred -u '{}' \;

Remember the backslash semicolon at the end!

Shred will "shred" a file, overwriting it's blocks with random data a number of times. Edit to suit (-u deletes the file after it's been shredded, which may or may not be what you want.)

Obviously check the files are right first, and the command will probably need to be run as root (even if you own all the files in question), or it will throw errors when it recurses into directories you can't read.

---

### Post by darolu on 2010-03-26
You should be able to do this with the "find + xarg" commands; read this guide:

[http://linux.about.com/od/commands/l/blcmdl1_find.htm](http://linux.about.com/od/commands/l/blcmdl1_find.htm)

ie.
```
$ find -name "*.bla" -print | xargs /bin/rm -f
```

---

### Post by new_tolinux on 2010-03-26
There is a package with "srm", it does 38 passes as I remember well, can be less if configured to do less through the command-line-options.
Don't know the name of the package, but this command will give you the right package to install:
```
sudo apt-get install srm
```

---

### Post by NiGhtMarEs0nWax on 2010-03-26
> **KeyserSoze93 said:**
> 
find / -name "*.doc" -exec shred -u '{}' \;


Thanks man, worked a treat!

just one question, what's the 
```
'{}' \;
```
for? and why does the {} need to be in quotes?

cheers, it's a command ill be using a lot so best to understand it. :)

Thanks!

---

### Post by asmoore82 on 2010-03-26
> **NiGhtMarEs0nWax said:**
> Thanks man, worked a treat!

just one question, what's the 
```
'{}' \;
```
for? and why does the {} need to be in quotes?

cheers, it's a command ill be using a lot so best to understand it. :)

Thanks!

`find` replaces the '{}' with the filenames it has found.
It must be quoted to "protect" it from the SHELL, which may see it as an empty code block.

The ';' ends the `find` `-exec` statement.
The '\' "protects" ';' again from the shell.

A bare ';' interpreted by the shell will finish the command to allow you to run 2 commands back to back:
```
echo hello; echo world
```

**darolu** was right, you should avoid `find ... -exec` whenever possible.
The most robust solution is a `find -print0 | xargs -0` construct:
```
 find */some/dir* -name "*.mp3" [COLOR="Purple"]**-print0**[/COLOR] | xargs [COLOR="Purple"]**-0**[/COLOR] du -h
```^this will efficiently handle files with any special characters in them.

---

