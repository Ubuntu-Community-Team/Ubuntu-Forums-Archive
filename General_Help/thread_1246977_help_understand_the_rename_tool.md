---
title: "help understand the rename tool"
date: 2009-08-22
forum: General Help
---

### Post by TheOne...more on 2009-08-22
hi, i rename and move files around frequently. and i like command line tools especially those that support regexing.

i used the rename tool a couple of times and i loved it but i can't really get it. i red the man page but the commands are ambiguous, there is a "s" command which replaces a string a single time. also there is a "y" command which is equivalent to s/string/replacement/g, but both the commands are given as examples and there is no inclusive list of commands used with this tool. also the tool has some strange behaviour with the regexes themselves.

i googled rename for source code, developers, more extensive manual and i wasn't lucky, and i would appreciate help.

thanx

---

### Post by Hendrixski on 2009-08-22
not sure I understand the question.

you're looking at the commandline tool mv
right?

If you mv old_file_name new_file_name then it renames the file

then the option in the man file are things you would add after mv
like so:
mv -f old_file_name new_file_name

---

### Post by kaibob on 2009-08-22
Look at post 2 in the following forum thread. It has a lot of useful examples.

[http://ubuntuforums.org/showthread.php?p=5210531](http://ubuntuforums.org/showthread.php?p=5210531)

The following site is also helpful:

[http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

---

### Post by ajgreeny on 2009-08-22
No, I think the OP is using **rename**, not **mv**.  rename is much better at multiple file renaming,but I agree the man is not very long or useful, but here are three examples which may help, depending on what you are trying to do.

```
rename 's/\ /_/g' *
``` To remove spaces from file names and replace with _.    or
```
rename 's/&/=/g' *
``` To remove & from file names and replace with =.        or
```
find ~/Radio -name '*.mp3' -exec rename -n 's/\ /_/g' "{}" +
```
                    To rename recursively, replacing spaces with _ in all mp3 files

---

### Post by DaithiF on 2009-08-22
Hi,
if you're looking to learn more about the expressions you can use in rename, then read up on perl regular expressions -- rename just applies whatever perl expression you provide.

---

### Post by TheOne...more on 2009-08-22
thank you all for responding.

yes that's correct the tool that i meant was /usr/bin/rename.

and thanks for the links, the first one is massivly helpful, but still no totally inclusive list of commands supported by the tool.

i know regexing from sed, and i'm a little struggling with perl regexes. but i guess there are tons of tutorials around, i'll search rather more carefully.

the thing is that i can't find a web page for this nice tool, or a developer site, or bigger man page, or anything to relate this pretty orphan.

---

### Post by DaithiF on 2009-08-22
also, you mentioned source code ...
```
vi /usr/bin/rename

```
its just a perl script :)

---

### Post by TheOne...more on 2009-08-22
oh, i thought it was a c binary because of the icon, thanks this answers the rest of my questions. i guess this thread is complete.

i found scripts with the same name but i didn't think that they were all the same thing as this tool.

thanx a lot for your help.

---

