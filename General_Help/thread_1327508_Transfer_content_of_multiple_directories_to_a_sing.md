---
title: "Transfer content of multiple directories to a single directory"
date: 2009-11-15
forum: General Help
---

### Post by LorenG on 2009-11-15
Hello all,
I am new to linux (so please be patient if I don't know much) but I am enjoying using Karmic Koala, and I find this version of Ubuntu very good to use, so that I am actually preferring it to Windows 7 and have installed it on 3 machines at home. I have had a problem with an external drive recently so that it became unreadable. Tried to fix it with TestDisk but it couldn't find or fix the MFT, so have then used PhotoRec to recover the files. I have now hundreds of folders located on my desktop, each containing hundreds of files, that I would like to transfer into a single folder called "Recovered", so that I can then sort them by file type and try and manually organise them (the name of the recovered files is no longer what it was before and I now need to open them to know what they are).
My question is, do I have to do this manually or is there a command that I can use that will transfer all these files from the various recovery folders into a single folder? All the folders' names are formed by the same string + a sequential number.
Thanks for your reply if you can help

---

### Post by Baelus on 2009-11-15
There's a way to do it with some terminal commands. Don't worry, I'll go through each step.

Open the menu and click Accessories > Terminal. That will get you a terminal window.

First, make a directory as the destination folder like this:

```
mkdir recovered
```

Now you can copy this and paste it into the terminal and hit return:

```
find ~/Desktop -mindepth 1 -type d -exec mv "{}" ~/recovered \;
```

The 'find' command will look on your Desktop for all items of the type d(irectory). After it has found all the directories it will exec(ute) the command that follows. 

It should:

mv (move)

"{}" (all the folders that 'find' has found)

~/recovered (and place them in the destination folder called recovered that you made in your home directory).


That will move all the directories from your Desktop to the folder called recovered sitting in your home folder.

If you want to move them back, you can do that using this:

```
mv ~/recovered/* ~/Desktop
```

Let me know how it turns out.


Also, if you want just the files from the folders on your desktop, you can use this:

```
find ~/Desktop -mindepth 2 -type f -exec mv "{}" ~/recovered \;
```

This time you can't 'undo' the move like before. It's now one big list of files that can't be separated back into its own folders as before.

If you want some safety, you can copy the files instead of moving them. This can be done by changing it to this:

```
find ~/Desktop -mindepth 2 -type f -exec cp "{}" ~/recovered \;
```

That will leave the source files and folders alone while copying the contents into ~/recovered. But... it will take a lot longer to complete.

---

### Post by LorenG on 2009-11-16
Many thanks Baelus,

I used 
```
find ~/Desktop -mindepth 2 -type f -exec mv "{}" ~/recovered \;
```I should have specified all the recovered folders where already contained within a folder on my desktop so I replaced 
~/Desktop with the path to the specific folder. This worked very well.

I also, before that, tried to use the part of the code that does a copy of the files,
```
find ~/Desktop -mindepth 2 -type f -exec cp "{}" ~/recovered \; 
```without realizing that I had already 60GB of recovered data on my 90GB Ubuntu Hard drive and that once it started copying the files I would have quickly ran out of space on my disk.
In that circumstance I found myself wondering how to stop the copying. In the end I shut down the machine, not knowing how to tell it otherwise to stop copying the files.

Again many thanks for your help.

---

### Post by Baelus on 2009-11-16
Glad you got it to work.

Sorry about the runaway copying. I should've also said ctrl+c will cancel a running command. It's kind of automatic and didn't occur to me.

If you're up for diving into the terminal you can get some help with this:

```
man *command*
```

This will give some documentation on how to use it. It may seem overwhelming at first, but after a while things will start to fall into place.

Have fun. :)

---

### Post by 905jay on 2010-09-21
> **LorenG said:**
> Many thanks Baelus,

I used 
```
find ~/Desktop -mindepth 2 -type f -exec mv "{}" ~/recovered \;
```I should have specified all the recovered folders where already contained within a folder on my desktop so I replaced 
~/Desktop with the path to the specific folder. This worked very well.

I also, before that, tried to use the part of the code that does a copy of the files,
```
find ~/Desktop -mindepth 2 -type f -exec cp "{}" ~/recovered \; 
```without realizing that I had already 60GB of recovered data on my 90GB Ubuntu Hard drive and that once it started copying the files I would have quickly ran out of space on my disk.
In that circumstance I found myself wondering how to stop the copying. In the end I shut down the machine, not knowing how to tell it otherwise to stop copying the files.

Again many thanks for your help.

Many Thanks. This worked as expected :)

---

