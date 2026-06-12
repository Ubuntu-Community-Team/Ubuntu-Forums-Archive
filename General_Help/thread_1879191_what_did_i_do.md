---
title: "what did i do?"
date: 2011-11-11
forum: General Help
---

### Post by liquidmonkey on 2011-11-11
just curious what this would have done?


mv officePOINTS2.bag ..

basically i tried to move a file to the directory above the one i was currently in. it didn't work and now i can't find the file :(

any ideas?

---

### Post by pr3zident on 2011-11-11
> **liquidmonkey said:**
> just curious what this would have done?


mv officePOINTS2.bag ..

basically i tried to move a file to the directory above the one i was currently in. it didn't work and now i can't find the file :(

any ideas?

try to use locate officePOINTS2.bag 
if it doesn't find the file you probably destroyed the file...
ps. use cp -v first before you use mv to make sure everything works out

---

### Post by satanselbow on 2011-11-11
Just cos I was curious... I just tried it with a throw away file and the behaviour was as expected...

ie Using your command line as an example I moved a file from ~/Desktop to ~/



What folder did you move the file from?

---

### Post by liquidmonkey on 2011-11-11
locate did not return anything :( so i guess its pooched. ah well, not a huge loss.

i was trying to move the file from my home/projects/test folder to the one above,ie home/projects folder.

---

### Post by pr3zident on 2011-11-11
> **liquidmonkey said:**
> locate did not return anything :( so i guess its pooched. ah well, not a huge loss.

i was trying to move the file from my home/projects/test folder to the one above,ie home/projects folder.

that's weird that .. didn't work smh that use to always happen to me i use to move a file to place unknown use cp -v before you do mv and press tab to make sure directories exist before you do mv

---

### Post by liquidmonkey on 2011-11-11
so if i was in this folder

projects/testing/stuff and wanted to move a file, file.txt
to
projects/testing

how would i do that in command line? is it possible to say 'move only one level up' instead of writing out the entire path?

---

### Post by Jonathan L on 2011-11-11
> **liquidmonkey said:**
> so if i was in this folder

projects/testing/stuff and wanted to move a file, file.txt
to
projects/testing

how would i do that in command line? is it possible to say 'move only one level up' instead of writing out the entire path?

Hi Liquid Monkey

You were doing it correctly.  But if you have symbolic links to directories it's frankly rather confusing, as pwd will show you what you did to get to the directory, not the "primary" name of the directory.  If you have symbolic links you might find the following ridiculous story helps.

Linux (but not other Unix operating systems) the default for pwd is to show the "logical" path: the path you used to get to a directory.  There is also a "physical" path, which is the one you get if you go up the chain of ".." parent entries in the directories.  But mv use the physical path.

To exemplify this, if we make a a directory with a symbolic link to it, we can easily "lose" our file:
```
mkdir /tmp/shallow
mkdir /tmp/shallow/deep
ln -s /tmp/shallow/deep /tmp/linktodeep
cd /tmp/linktodeep
date > thefile
ls
pwd
mv thefile ..
ls -l /tmp/shallow
cd ..
pwd
```You'll find the file is in /tmp/shallow!  This is because the parent of the directory is 'shallow':when the directory was made (mkdir /tmp/shallow/deep) it makes the setting for .. be /tmp/shallow.

The thing which behaves strangely there is cd and pwd; mv behaves "normally".  Specifically, the cd .. at the end  doesn't go to the parent of the current directory (by reading the entry for .. in the current directory); instead (and confusingly in my opinion) it strips the bottom directory off the remembered current directory name.

You can (and I've only just found this out) tell pwd which one you want!

Mine gives:
```
$ cd /tmp/linktodeep
$ pwd
/tmp/linktodeep
$ pwd -L
/tmp/linktodeep
$ pwd -P
/tmp/shallow/deep

```To find your file:
```
cd projects/testing/stuff
pwd -P
pwd -L
```If the last two are different, look at the parent of the -P result:
```
cd `pwd -P`/..
```I'll agree that seems ridiculous!  If it doesn't help, you can always try

```
find / -name officePOINTS2.bag

```Hope that's some use.

Kind regards,
Jonathan.

---

### Post by liquidmonkey on 2011-11-11
thanks very much for that explanation!
its a bit more complicated than what i can arsed to deal with so i'll continue to put the entire path in from now on, just to be sure it moves.


just curious, is this symbol ^ used at all in ubuntu?
i seem to remember it being used to up a directory, i think in DOS.

---

### Post by pr3zident on 2011-11-11
> **liquidmonkey said:**
> thanks very much for that explanation!
its a bit more complicated than what i can arsed to deal with so i'll continue to put the entire path in from now on, just to be sure it moves.


just curious, is this symbol ^ used at all in ubuntu?
i seem to remember it being used to up a directory, i think in DOS.

try this add this line in your ~/.bashrc file 
alias = "cd .."
and then try it that's how i have my set up and it works fine

---

### Post by Jonathan L on 2011-11-12
> its a bit more complicated than what i can arsed to deal with so i'll continue to put the entire path in from now on, just to be sure it moves.


Hi Again 

You might find it a good idea to always pull rather than push: get to where you want it and do
```
mv faraway/file .
```

To get rid of the "logical directory" foolishness from cd and pwd, you can do (in bash)
set -P

Kind regards,
Jonathan.

---

