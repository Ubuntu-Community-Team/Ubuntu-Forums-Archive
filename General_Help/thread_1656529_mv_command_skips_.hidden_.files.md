---
title: "mv command skips .hidden .files"
date: 2010-12-31
forum: General Help
---

### Post by rpaskudniak on 2010-12-31
Greetings.

I need some help with the mv command or an alternative thereto.  It's
really something I ought to know but I have usually used the mv command
for a small number of files at a time and, amazingly, never for 
"hidden" files (with names beginning with .), symbolic links and any 
lingering hard links.

It is my intention to move whole directory trees from one file system
to another, including hidden files.

Consider the following directories in /tmp:  /tmp/A and /tmp/B, noting
their contents:
```
$ ls -lA /tmp/[AB]
/tmp/A:
total 8
-rw-r--r-- 1 rasputin rasputin 74 2010-12-31 00:11 file1
-rw-r--r-- 1 rasputin rasputin 74 2010-12-31 00:11 .file2

/tmp/B:
total 0
```
That is, subdir A contains two files, one of which would not turn up in
a simple ls listing because its name starts with a dot.

Now the mv command (with verbose option), followed by the same ls
command to view my accomplishment:
```
$ mv -v /tmp/A/* /tmp/B
`/tmp/A/file1' -> `/tmp/B/file1'

$ ls -lA /tmp/[AB]
/tmp/A:
total 4
-rw-r--r-- 1 rasputin rasputin 74 2010-12-31 00:11 .file2

/tmp/B:
total 4
-rw-r--r-- 1 rasputin rasputin 74 2010-12-31 00:11 file1
```

Notice, the mv skipped moving .file2.

I may have missed something in the mv man page but I don't see an
option for including such hidden files in the move.  I also don't see 
an option in rsync for accomplishing the same function, though it's
**_really_** easy to miss something in the haystack of the 
rsync man page.

So, my question is (as usual, multi-part.  Sighhhh :-({|=  ):  
[LIST]
[*]Is there indeed an option to mv that forces it to include .files in
the move?
[*]I am assuming that mv will recursively move all subdirectories,
similar to the -pR option of the cp command.  Is this a correct
assumption?
[*]Is there an option to rsync that accomplishes what I'm up to?  (I
just found the [FONT="Courier New"]**--remove-source-files**[/FONT]
option.)
[*]Is there yet another program I can use to accomplish this move?
[/LIST]
Note: I do have an awkward workaround:  I could use [FONT="Courier
New"]**cp -pR**[/FONT] to copy the directory tree and then
[FONT="Courier New"]**rm -rf**[/FONT] /source-path/* to empty out
the original directory. I'd rather not use it because if something went
was missed in the cp, I would lose the original in the [FONT="Courier
New"]**rm -rf**[/FONT] step.

I am also worried about the godzillion options in rsync.  I want to
preserve symbolic links but they may require interpretation when the
symlink itself is moved to another file system - the target of the
symlink may or may not remain in the same relative path as it
originally was.  (Y'all may surmise that I have not used rsync much.)
I will be experimenting with mv and rsync for symlinks and hard links
but I might get my answers more quickly if someone already has the
knowledge to share.

Advice, anyone?

Thanks much.

---

### Post by kidders on 2011-01-01
Hi there,

Just a bit of background ... bear with me ...

There isn't really any such thing as a hidden file. Choosing not to display certain files by default is just a commonly observed convention, for the sake of neatness. Examples include files beginning with '.' (settings/preferences), and those ending with '~' (backups).

Commands like mv don't care about filenames. They will process any file you tell them to, however the '*' wildcard does not expand to include filenames starting with dots, so they are not processed. **mv -v /tmp/A/* /tmp/B** does not move ".file2" for the same reason that you'd expect **mv -v /tmp/A/g* /tmp/B** not to move "file1".

For example, compare ...```
ls -d /tmp/A/*             *[.files explicitly excluded]*
ls -d /tmp/A/* /tmp/A/.*   *[.files included]*
ls /tmp/A/* /tmp/A/.[^.]*  *[".." and "." excluded]*
find /tmp/A -type f        *[find does not observe the '.' convention]*

```


> **rpaskudniak said:**
> Is there indeed an option to mv that forces it to include .files in the move?No, but such an option is not necessary. Any file selected by your arguments will be moved, whether it starts with a '.' or not.

> **rpaskudniak said:**
> I am assuming that mv will recursively move all subdirectories, similar to the -pR option of the cp command.  Is this a correct assumption?Strictly speaking, mv doesn't act recursively. Think of moving a directory as detaching it from one part of your filesystem and re-attaching it to another. On most filesystem formats, an entire directory structure can be moved instantly ... it's not a recursive operation. Copying, on the other hand, involves duplicating data, which is quite a different thing.

> **rpaskudniak said:**
> Is there an option to rsync that accomplishes what I'm up to?Rsync should not be used to simply move files around. It's designed to help you mirror changes in file structures, typically between two different machines (eg a development & deployment environment).

> **rpaskudniak said:**
> Is there yet another program I can use to accomplish this move?There are lots of ways of moving things, but a straightforward 'mv' command is the one least likely to do something unexpected, and the one that will perform most efficiently.

I hope that helps.

---

### Post by NetDoc on 2011-06-23
> **kidders said:**
> There are lots of ways of moving things, but a straightforward 'mv' command is the one least likely to do something unexpected, and the one that will perform most efficiently.

I hope that helps.So, **what** is the best way to move EVERYTHING, including the . files? Answering that question would truly "help". I find that I run the mv command twice one with a * and the second with a .*. In fact, I usually use my arrow to bring up the previous command and add the ".".

---

### Post by cmthornton on 2011-07-08
> **NetDoc said:**
> So, **what** is the best way to move EVERYTHING, including the . files? Answering that question would truly &quot;help&quot;. I find that I run the mv command twice one with a * and the second with a .*. In fact, I usually use my arrow to bring up the previous command and add the &quot;.&quot;.

By `best' do you mean simpliest, fastest, most portable, etc.?


A simple way:

```
mv src/{*,.*} dest/
```Remember, the `mv' command can move multiple sources to the destination.



A simple bash specific way:

```
shopt -s dotglob
mv src/* dest/
```The `shopt -s dotglob' makes `*' include dotfiles. To turn it off use `shopt -u dotglob'.

---

### Post by NetDoc on 2011-07-23
> **cmthornton said:**
>  By `best' do you mean simpliest, fastest, most portable, etc.?


A simple way:

```
mv src/{*,.*} dest/
```Remember, the `mv' command can move multiple sources to the destination.  That works great. Thanks! 

> **cmthornton said:**
> A simple bash specific way:

```
shopt -s dotglob
mv src/* dest/
```The `shopt -s dotglob' makes `*' include dotfiles. To turn it off use `shopt -u dotglob'. Explain a bit more about shopt please.

---

