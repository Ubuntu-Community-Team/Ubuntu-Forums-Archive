---
title: "how to type spaces in filenames in terminal?"
date: 2010-03-18
forum: General Help
---

### Post by Nazaroo on 2010-03-18
I'm trying to access a file and copy it to another location, but the drive name has a space. I'd like to rename that too.

Can anyone help?  I know that a % sign is sometimes used, but this didn't seem to work in terminal...

---

### Post by LoneWolfJack on 2010-03-18
add a backslash before the whitespace

---

### Post by a.walker on 2010-03-18
You can escape them with a \ but I typically just begin typing the name of the file and press the "tab" key. This has ubuntu automatically fill out the rest of the file name, which will show you how to put spaces in file names

---

### Post by howefield on 2010-03-18
Place a backslash before the spaces, eg

```
xxxx@lucid:~$ cd example\ command\ line 
```

Or I think you can enclose with quotations marks eg,

```
xxxx@lucid:~$ cd "example command line" 
```

---

### Post by Nazaroo on 2010-03-18
Thank you everyone:

Naturally I have two more questions now:

(1) How can I get ls to show hidden files, or conversely just have hidden files accessible?
I'm trying to repair a hidden file from the LiveCd, namely the xorg.conf file in /etc/X11 for my nvidia cards.

It was edited with some problem results... Now I can't seem to re-copy or delete it or edit it with a text editor.

(2) How can I get on as root to fix this machine generally from the Live CD?

...signed, frustrated and embarrassed.

---

### Post by ultimatelinux on 2010-03-18
if the name of file is my file
just type 2 to 3 characters of filename then hit tab
ex:
type my and then hit tab the rest of file name will be autocompleted.
to rename use mv command.
mv filename newname.;)

---

### Post by ultimatelinux on 2010-03-18
```
mv filename newfilename
```

---

### Post by Nazaroo on 2010-03-18
okay trying to rename file in terminal generates this error:

# rename xorg.conf xorg.conf.screwed
Bareword "xorg" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "conf" not allowed while "strict subs" in use at (eval 1) line 1.


what the hell does that mean?...

---

### Post by Nazaroo on 2010-03-18
Here's another attempt to fix the name of the 2nd hard-drive:

/media# rename Secured\ 02 Secured-02
Number found where operator expected at (eval 1) line 1, near "Secured 02"
(Do you need to predeclare Secured?)
syntax error at (eval 1) line 1, near "Secured 02"

/media# (prompt returns)

---

### Post by Nazaroo on 2010-03-18
Trying to rename with mv command does this:

mv xorg.conf xorg.conf-stupid

mv: cannot stat 'xorg.conf': No such file or directory


I think this means the hidden file can't be accessed by mv.

So how can I get root going or get hidden files visible in terminal?


there doesn't seem to be a "show hidden files" command, even in ls.

Like there should be something like:

ls -h (for hidden)

---

### Post by Ryan Dwyer on 2010-03-18
Hidden files are files that start with a dot. xorg.conf is not a hidden file - it probably doesn't actually exist. I don't think Ubuntu 9.10 has an xorg.conf.

ls -a will show hidden files. There's an option in Nautilus as well (View > Show hidden files).

---

### Post by Nazaroo on 2010-03-18
ok  one mystery solved maybe...

When I typed cd /etc/X11 it didn't go to the folder on the drive, but probably the folder on the LiveCD...oops...

Now I have to figure out the command to access the real folder.

but all other questions are still hanging open:

(1) How can I modify files on my Harddrive?

(2) How can I be ROOT in terminal?

(3) How can I access hidden/locked files?

The whole point of booting with LiveCD is that I need to edit the other system on harddrive.

---

### Post by Nazaroo on 2010-03-18
Okay just figured out that the real system is some impossibly long random number string in /media.

It shows up as "9.8 GB Filesystem" in the File Browser (booted from live CD).

But I don't think I can change folders using that name in the terminal....

any ideas?

---

### Post by Nazaroo on 2010-03-18
Okay I just tried to change to the folder using the long name:

root@ubuntu:/media#   ls -1

3dcd063f-ed58-4b12-ac72-ae04e54df683
Secured 01
Secured 02
 
root@ubuntu:/media# cd /3dcd063f-ed58-4b12-ac72-ae04e54df683
bash: cd: /3dcd063f-ed58-4b12-ac72-ae04e54df683: No such file or directory

root@ubuntu:/media# 

This is what happens.  Seems the long name is not a valid name for commands...?

---

### Post by Ryan Dwyer on 2010-03-18
Remove the slash at the start of the gibberish. The slash makes it look from the top level rather than in the current directory.

---

### Post by Nazaroo on 2010-03-18
> **Ryan Dwyer said:**
> Remove the slash at the start of the gibberish. The slash makes it look from the top level rather than in the current directory.

Thanks! I'll try that!

any ideas about deleting or renaming files from LiveCD?

is there a way I can boot LiveCD and then get on as ROOT?

---

### Post by Nazaroo on 2010-03-18
Okay I was able to get into the folder:  I tried changing the name of the file with:

```
 mv xorg.conf xorg.conf.screwed
mv: cannot move `xorg.conf' to `xorg.conf.screwed': Permission denied

```

At least that message makes some sense.
How can I get permissions to alter this file?

---

### Post by Ryan Dwyer on 2010-03-18
sudo mv xorg.conf xorg.conf.screwed

---

### Post by tho. on 2010-05-06
Hello there I was not sure where to post this question and these seemed like suitable location.

I am attempting to make my life easier when moving files to a location containing a space (cannot be renamed), as this is a regular task.

Currently I type:

```
mv file ~tom/WhiteRabbit/"Shared Pictures"/some/file/location/.

```

I have attempted to set variables in .bashrc with

```
set PICTURES=/home/tom/WhiteRabbit/"Shared Videos"

```
and
```
set PICTURES=/home/tom/WhiteRabbit/Shared\ Videos

```

with the aim to type

```
mv file $PICTURES/some/file/location/.

```
but each time I try to cd $PICTURES as a test it attempts to take me to /home/tom/WhiteRabbit/Shared
Could anyone provide me with the correct syntax required here?

tom

---

### Post by WorMzy on 2010-05-06
EDIT: Misread your question. Try ```
cd "$PICTURES"
``` likewise, to move things use ```
mv "$PICTURES/place/"
```

---

### Post by tho. on 2010-05-07
thanks, problem solved :)

---

### Post by Emmtor on 2010-08-27
```
set PICTURES=/home/tom/WhiteRabbit/"Shared Videos"

```

I thought that this thread would be suitable for my simple question.
Why use 'set' instead of just typing:

```
PICTURES=/home/tom/WhiteRabbit/"Shared Videos"

```

I've been wondering for a while now.

---

### Post by DaithiF on 2010-08-27
> **Emmtor said:**
> ```
set PICTURES=/home/tom/WhiteRabbit/"Shared Videos"

```I thought that this thread would be suitable for my simple question.
Why use 'set' instead of just typing:

```
PICTURES=/home/tom/WhiteRabbit/"Shared Videos"

```I've been wondering for a while now.

You don't need to use set.  In the old days of the c-shell you had to use set to create variables, bourne & related shells don't need it.  some habits die hard i guess.

---

### Post by bilkay on 2010-08-27
> **Nazaroo said:**
> Trying to rename with mv command does this:

mv xorg.conf xorg.conf-stupid

mv: cannot stat 'xorg.conf': No such file or directory


I think this means the hidden file can't be accessed by mv.

So how can I get root going or get hidden files visible in terminal?


there doesn't seem to be a "show hidden files" command, even in ls.

Like there should be something like:

ls -h (for hidden)
ls -a

---

