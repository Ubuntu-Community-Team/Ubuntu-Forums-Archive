---
title: "chmod -R doesn't work"
date: 2010-04-11
forum: General Help
---

### Post by motoperpetuo on 2010-04-11
or at least, it doesn't seem to. for some reason, my .txt, .doc, .rtf, and other files that shouldn't have the execute bit set often seem to (i think i know why, but that's not important). it's my understanding that this command should, for example, remove the execute bit from all .rtf files recursively (that is, from .rtf files in subdirectories too):
```

chmod -R 666 *.rtf

```
i've read help and the man page for chmod, and it seems that -R switch should make chmod work recursively, but it only alters files in the present working directory. could someone point out what i'm doing wrong? i'd greatly appreciate it, because this is driving me quite mad.

---

### Post by Sin@Sin-Sacrifice on 2010-04-11
```
sudo chmod -R -x *.txt
```

---

### Post by motoperpetuo on 2010-04-11
i tried this:
```

chmod -R -x *.rtf

```
and got exactly the same result. that is, the executable bit is removed from .rtf files in the present working directory, but not in subdirectories.

does anyone have any idea what's going on? seems like the -R switch should make these changes recursively, but it also just doesn't seem to work. i've tried this in jaunty and mint 7, for what it's worth.

---

### Post by darolu on 2010-04-11
Try:
```
$ chmod a-x <Directory>/*.rtf
```
If you want to use "-R" it would have to be:
```
$ chmod -R a-x <Directory>/*.rtf
```
This would remove execution rights to the actual directory too, which may cause conflicts with some apps and processes.

---

### Post by jamesisin on 2010-04-11
I'm a little confused myself.  I created a test directory with a test sub-directory, each containing 2 rtf files.  I then tried each of these commands:

```
chmod -R -x *.rtf

find *.rtf -type f -exec chmod -x {} \;
```

Which ever I use I still only see the x bit removed from the files in test and not in test/test.

I feel pretty good that *both* of these should do the same thing and that that thing is recursively remove the x bit.

(I tried specifying the directory as darolu suggests as well.  Same results.)

---

### Post by motoperpetuo on 2010-04-11
at least it's not just me. i'm reluctant to do anything that might remove the executable bit from directories too, because as darlou rightly pointed out, that could cause other problems.

if anyone out there has figured out how to recursively remove the executable bit from files with a certain extension, please let me know.

---

### Post by sisco311 on 2010-04-11
```
find /path/to/dir -iname "*.rtf" -type f -exec chmod -x '{}' +
```

EDIT:

*.rtf matches the rtf files from the directory. The recursive option is futile because rtf files (usually) don't have sub-directories. :)

It's like:
```
chmod -R -x 1.rtf 2.rtf 3.rtf
```

EDIT2:
In bash, if you enable globstar, you can run something like:
```
shopt -s globstar
chmod -x **/*.rtf
```

```
man bash | less +/globstar
man bash | less +2/globstar
```

---

### Post by jamesisin on 2010-04-11
> **sisco311 said:**
> ```
find /path/to/dir -iname "*.rtf" -type f -exec chmod -x '{}' +
```

This works.  (I was in the test directory and so /path/to/dir was left out.)

sisco311 - Could you explain the difference between your line of code and mine?  Why quote the search term?  What is the bracket-pair doing and why quote it?  What's the difference between \; and + in this case?

---

### Post by KeyserSoze93 on 2010-04-11
* is a commonly used glob operator, found in regex, the shell and the find command. When the shell sees something like "*.rtf", it automatically expands it to match all the rtf files in the current dir. The find command is searching for files which match "*.rtf", and bypassing the shell's glob.

To do this, you need to quote the "*.rtf", so that the shell does not expand it, but instead passes it verbatim to the find command, which then manages the task of globbing with it.

I'm not really sure about quoting the '{}' (which expands to each of the files the find finds.) I always do it, but it may not be necessary, if find's -exec performs shell quoting already.

With either the zshell (which I use), or bash (as a previous poster mentioned), the quickest and most intuitive way to do this kind of thing is: chmod 644 **/*.rtf

---

### Post by motoperpetuo on 2010-04-11
thanks for all the help with this, everyone. i had the best success with this:
```

find ./ -name '*.rtf' -type f -exec chmod 666 '{}' +

```
it finds every .rtf file in the current directory and all subdirectories that has the executable bit set and unsets it.

i didn't realize that a wildcard like * can only apply to the current directory (as much as i hate to admit it, even two years after ditching microsoft completely, my mind is still windows-centric sometimes). out of curiousity, could someone explain to me what the -R switch for chmod is supposed to do? as a test, i created a file called one.rtf in my current directory, in a subdirectory, and a subdirectory beneath that. i tried this:
```

chmod -R 666 one.rtf

```
it still only removed the executable bit from the one.rtf in my current directory, not in the subdirectories.

---

### Post by jamesisin on 2010-04-12
If you just used chmod -R 666 it would behave recursively from the current directory.  The problem arose because you wanted to specify a (group of) file(s) with *.rtf.  This caused chmod to seek out specific files and behave recursively *on those files*.  We had to sort out a way to get recursion on the *folders* and then filter out the interesting files.

---

### Post by prodigy_ on 2010-04-12
> **jamesisin said:**
> If you just used chmod -R 666 it would behave recursively from the current directory.  The problem arose because you wanted to specify a (group of) file(s) with *.rtf.  This caused chmod to seek out specific files and behave recursively *on those files*.  We had to sort out a way to get recursion on the *folders* and then filter out the interesting files.

I understand why that's so but I really don't think that in 2010 recursive file operations **should** treat wildcards like this. When someone specifies "*" and "-R" he obviously wants "*" to be re-evaluated for every folder (by default at least).

Again Linux developers in their arrogance don't want to learn from MS, even though in this case MS did the job better.

---

### Post by sisco311 on 2010-04-12
> **jamesisin said:**
> This works.  (I was in the test directory and so /path/to/dir was left out.)

sisco311 - Could you explain the difference between your line of code and mine?

You missed the -name (or -iname case insensitive) option before the search pattern, so in your command  *.rtf is the search path.


> **jamesisin said:**
> 
Why quote the search term?


To escape special characters like spaces in filenames.


> **jamesisin said:**
> 
What is the bracket-pair doing and why quote it?  What's the difference between \; and + in this case?


```
man find | less +/"-exec command ;"
```

EDIT:
For differences between the single & double quotes see the QUOTING section in man bash:
```
man bash | less +/QUOTING
```

---

### Post by sisco311 on 2010-04-12
> **prodigy_ said:**
> I understand why that's so but I really don't think that in 2010 recursive file operations **should** treat wildcards like this. When someone specifies "*" and "-R" he obviously wants "*" to be reconsidered for every folder (by default at least).


Just to clear things up. chmod doesn't interpret wildcards, it only accepts valid file names. The wildcard expansion is done by the shell.

---

