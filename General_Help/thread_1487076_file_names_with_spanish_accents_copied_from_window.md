---
title: "file names with spanish accents: copied from windows and don't work"
date: 2010-05-18
forum: General Help
---

### Post by jadu on 2010-05-18
hello,

In the small office where I work, we have two work computers, one with windows and one with Ubuntu. We are going to change the windows computer to Ubuntu, and put them on a network. So we copied all of the documents on the windows computer to the Ubuntu computer as a first step. 
The problem is, with the documents and folders that we copied, if they have spanish accents we can't open them.
I tried looking on the forum but I didn't find anything about exactly that problem. One post suggested that the "locale" might be the problem, but our locale seems to be the correct one for our country and language.
The accents show up as white question marks inside a black diamond. If I open a file inside a folder with an accent, or a file with an accent, it tells me that the file doesn't exist.
But when I change the name of the containing folder or the file, and replace the question marks with accents, I can open the folders and files.
But we have lots and lots of documents, and it would take a really long time to change the name of all of the folders and files. How can I fix all of them at the same time?

thanks

---

### Post by luigi_mb on 2010-05-18
> **jadu said:**
> hello,

In the small office where I work, we have two work computers, one with windows and one with Ubuntu. We are going to change the windows computer to Ubuntu, and put them on a network. So we copied all of the documents on the windows computer to the Ubuntu computer as a first step. 
The problem is, with the documents and folders that we copied, if they have spanish accents we can't open them.
I tried looking on the forum but I didn't find anything about exactly that problem. One post suggested that the "locale" might be the problem, but our locale seems to be the correct one for our country and language.
The accents show up as white question marks inside a black diamond. If I open a file inside a folder with an accent, or a file with an accent, it tells me that the file doesn't exist.
But when I change the name of the containing folder or the file, and replace the question marks with accents, I can open the folders and files.
But we have lots and lots of documents, and it would take a really long time to change the name of all of the folders and files. How can I fix all of them at the same time?

thanks

Install "detox" from the repos. Then look at its man page. detox works on entire folders or on single files.

/luigi

---

### Post by jadu on 2010-05-18
thanks for the reply. I installed detox. I actually couldn't figure out how to run it. But still, from what I read online, detox only works to replace every instace of X character with Y character. For instance, ñ to n. But I need to get it to read how the names were originally written-- in some cases the missing character is an ñ, others is an é, etc.
I found this that seems to be what I need:
[http://forum.ubuntu-fr.org/viewtopic.php?id=347517](http://forum.ubuntu-fr.org/viewtopic.php?id=347517)

(it's in french).
But I can't figure out what to do with it. In the forum, the creator of the Lapogne71 script says that in order to get it to work, you have to:

> 1. copy the script in the folder containing the files to rename.
- 2. open a terminal and place it in this folder
- 3. execute the command:

bash convmv-for-utf-8_0.03.sh


unfortunately, I'm still pretty basic with computers in general and Ubuntu, so I don't know what 1. or 2. mean. If it's a text file, how do I copy the script and put it in the folder? just copy the text file itself? And how do I open a terminal inside a folder, what's that mean?

thank you!

---

### Post by CharlesA on 2010-05-18
It kinda sounds like it is missing a font for that language. You could try installing ubuntu-restricted-extras or just the MS fonts.

[http://embraceubuntu.com/2005/09/09/installing-microsoft-fonts/](http://embraceubuntu.com/2005/09/09/installing-microsoft-fonts/)

---

### Post by jadu on 2010-05-19
thanks for the reply. I installed the fonts that you recomended, but it still doesn't work. The problem that I have is with the file and folder names, but inside the documents everything is fine. Any ideas about the script I asked about before?

---

### Post by Vaphell on 2010-05-19
this looks like an issue with the default encoding. Ubuntu uses utf8 for file names, windows apparently does not. You'd have to force ubuntu to mount stuff with different encoding to be compatible or convert names en masse, but i think windows would object.

---

### Post by CharlesA on 2010-05-19
Ah ok. You would need to download the script and place it in the folder with the problem files. Then double click it and select "run in terminal."

Make sure it has execute permission set.

---

### Post by jadu on 2010-05-19
I'm getting closer, I think.
I read online to find out what scripts are and how to make them work.
I found these two tutorials:

[https://help.ubuntu.com/community/Nautilus_Scripts](https://help.ubuntu.com/community/Nautilus_Scripts)

[https://help.ubuntu.com/community/NautilusScriptsHowto](https://help.ubuntu.com/community/NautilusScriptsHowto)

I copied the script into the folder I need to fix, but when I double clic on the script it doesn't give me an option of run in terminal-- it just opens it as a text file.

I also pasted the script here, because one of the tutorials said to do that:
~/.gnome2/nautilus-scripts/ 

but when I right click like it says, I don't get a "scripts" option to follow the instructions.

For the permissions, I gave it "read and write" permission (it didn't give me the option of "execute") from nautilus--properties-permissions.

how can I make the script run?
thanks

---

### Post by CharlesA on 2010-05-19
You'd need to right click on it, select properties, permissions tab > Allow executing file as program.

EDIT: If you cannot give it rwx permissions from the GUI, you can always use this:```
chmod 770 file
```

---

### Post by jadu on 2010-05-19
well, I think I'm learning some, but it's not working yet.
Your last advice let me run it in terminal.
But it doesn't fix the problem yet.
I also tried running in terminal

> bash convmv-for-utf-8_0.03.sh 

following what I understood of the instructions on the script page. But it tells me "no file or directory". 

if you'll see the instructions on how to run the script from the other site, the stage I seem to have skipped is 
> - 2. open a terminal and place it in this folder
though I don't know what this means

any more ideas?

---

### Post by luigi_mb on 2010-05-19
> **jadu said:**
> thanks for the reply. I installed detox. I actually couldn't figure out how to run it. But still, from what I read online, detox only works to replace every instace of X character with Y character. For instance, ñ to n. But I need to get it to read how the names were originally written-- in some cases the missing character is an ñ, others is an é, etc....
thank you!

Detox should be able to do what you want. Study the man pages

```

$ man detox
$ man detox.tbl

```

/luigi

---

### Post by Vaphell on 2010-05-19
```
sudo apt-get install convmv
```
this installs convmv package from repo
convmv --help to see available options

```
cd /dir/with/your/stuff/to/convert
ls
```
go to the files in question, check if you are in proper place

```
convmv -f cp1252 -t utf8 *
```
i assume spanish windows uses codepage cp1252, this will perform a dry run without actual changes

```
convmv -f cp1252 -t utf8 --notest *
```
actual renaming all files in a dir from cp1252 to utf8

---

### Post by CharlesA on 2010-05-19
Could you post the contents of the script?

---

### Post by jadu on 2010-05-21
I was very excited to see that the command

> convmv -f cp1252 -t utf8 --notest *

seemed to work!

But it doesn't change the files and folders that are in sub-folders. How can I do that?

I realized that the script that I asked about earlier wasn't working because I didn't know how to enter the folder in terminal, thanks for explaining that (the cd command).
When I tried that other script I realized it was basically the same thing, it just took me through a menu of possible codepages first. The other difference was that the command is slightly different, in the location of the asterix:

> convmv -f cp1252 -t utf-8 * --notest

But it doesn't change the names of subfolders either.

Can someone tell me how to apply this command to subfolders? and I will be very happy to have managed to fix this.

also, a note, when I use the command that you recomended to me, it gives me this message, in addition to fixing the file names:
> Your Perl version has fleas #37757 #49830 
from what I saw online this seems like it's not a problem, right?

---

### Post by CharlesA on 2010-05-21
Try running this:

```
convmv -f cp1252 -r -t utf8 --notest * 
```

---

### Post by jadu on 2010-05-22
that worked!!!
thanks so much, this was a great help that made it much easier for us to transition to Ubuntu, if we had needed to change every folder name individually it would have been a lot of time and also it would have made my coworkers much more skeptical about the shift to ubuntu.
thank you for the advice!!!

---

