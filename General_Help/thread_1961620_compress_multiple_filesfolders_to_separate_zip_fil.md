---
title: "compress multiple files/folders to separate zip files"
date: 2012-04-19
forum: General Help
---

### Post by Arunomi on 2012-04-19
Hi 

I have a folder that contains multiple folder and multiple files, 
to be exact 1862 folder and file.

I would want to, with one command, compress this so that ever folder becomes a separate zip file and ever file thats not in a folder becomes a separate zip file. 
Is this possible in ubuntu?

I have searched on google and i can only find solutions for windows and mac and I have searched this forum and found nothing. :(

So if there is same one out there that have a tip please help.

MVH Sean

---

### Post by Vaphell on 2012-04-19
test this, maybe on some smaller set first
```
for f in *; do zip -9r "$f.zip" "$f"; done
```

---

### Post by hwttdz on 2012-04-19
Here's another possibility:

```
find . -mindepth 1 -maxdepth 1 -exec tar -czf {}.tar.gz {} \;
```

I'm not sure if by zip you mean in general a compressed file format, or specifically zip file format.  Some variation could probably be used for zip, I'm just not familiar with the zip syntax.

---

### Post by papibe on 2012-04-19
Hi Arunomi.

You could use the command 'find' to get both the files on the directory and the list of directories in it.

This will get the files:
```
find -maxdepth 1 - type f
```
and this the subdirectories:
```
find -maxdepth 1 -type d -not -name .
```
where:
[INDENT]'-maxdepth 1' means to not descent looking on the subdirectories.
'-type f' means files.
'-type d' means directories.
''-not -name .' means do not include the directory itself (represented by .).[/INDENT]
You can execute a command every time 'find' finds a directory by using the exec option:
```
find -maxdepth 1 -type d -not -name . -exec zip -r '{}'.zip '{}' \;
```
where '{}' makes reference to the directory just found. For example when it finds the dir 'Music', it will run:
```
zip -r Music.zip Music
```
thus recursively scanning 'Music' and compress it into Muzic.zip

For the files you need a different approach. You don't want each file compress by it self, but all of them together in one zip.

You can also use the exec option but this time the command will be executed at the end using all files found as parameters:
```
find -maxdepth 1 -type f -exec zip localfiles.zip '{}' +
```
This time all files directly under the folder will be compress into 'localfiles.zip'.

I hope that helps, and tell us how it goes.
Regards.

BTW, you may need to install zip:
```
sudo apt-get install zip
```

---

### Post by Arunomi on 2012-04-19
```
find -maxdepth 1 -type d -not -name . -exec zip -r '{}'.zip '{}' \;
```

Workt like a sharm but it includes the folder to. 

Is there a way to not include the folder?

And I want the files in the main dir to be compresst to separat zip files and not to one big

---

### Post by Vaphell on 2012-04-19
use for loop i mentioned earlier

```
$ ls *
1.txt  2.txt
xxx:
1.txt  2.txt

$ **for f in *; do zip -9r "$f.zip" "$f"; done**
  adding: 1.txt (stored 0%)
  adding: 2.txt (stored 0%)
  adding: xxx/ (stored 0%)
  adding: xxx/2.txt (stored 0%)
  adding: xxx/1.txt (stored 0%)
$ ls
1.txt  **1.txt.zip**  2.txt  **2.txt.zip**  xxx  **xxx.zip**
```

---

### Post by papibe on 2012-04-19
> **Arunomi said:**
> Is there a way to not include the folder?
Let me see if I understand correctly. Let's say one of the subdirectories directly under the main folder is 'Music'.

I believe you want to zip Music's files as a plain file list with no reference to ever belonging to 'Music'. Is that so?

I see 2 options depending if Music has just files, or more subdirectories and files:

(1) Just files, and no subdirectories: just use the -j option (remove paths):
```
find -maxdepth 1 -type d -not -name . -exec zip -**[COLOR="Red"]j[/COLOR]**r '{}'.zip '{}' \;
```

(2) There are subdirectories under it ('Music' in my example): Here you *"may"* use the last command, but if they are repeated filenames, zip won't work properly.

I can't think of anything simpler that this to compress all the subtree but excluding 'Music':
```
find -maxdepth 1 -type d -not -name . -exec bash -c 'cd "$1";  zip -r '../{}'.zip .' _ '{}' \;
```


> **Arunomi said:**
> And I want the files in the main dir to be compresst to separat zip files and not to one big
Find files, but use the exec part as in the directories example (but without recursion):
```
find -maxdepth 1 -type f -exec  zip '{}'.zip '{}' \;
```
Regards.

---

### Post by Arunomi on 2012-04-19
It works wonderfully.
Tanks

Now just one more thing how do you know how to make this commands?

---

### Post by papibe on 2012-04-19
> **Arunomi said:**
> It works wonderfully.
Tanks

:) Great! Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.

> **Arunomi said:**
> Now just one more thing how do you know how to make this commands?
I started like you ;), asking questions, and then with time I've learned a few tricks.

This is a very good place to learn cool stuff! Have fun and come back often!

Regards.

---

### Post by hwttdz on 2012-04-20
A good place to start for something like that is the man page for the find command, just type "man find" at the terminal and you'll get a bunch of documentation for the find command.  

The loop is kind of a bash-ism, and reading the documentation for bash is a little harder...

There are also a bunch of clever bash-ism's, like back-ticks, and loops, and apparently zsh is even more clever, but I've never learned it through and through.

---

### Post by SeijiSensei on 2012-04-20
> **Arunomi said:**
> Now just one more thing how do you know how to make this commands?

[http://www.google.com/search?q=bash+tutorial](http://www.google.com/search?q=bash+tutorial)

---

### Post by Arunomi on 2012-04-22
Sorry for sounding like a n00b but how do i change to solved?

---

### Post by SeijiSensei on 2012-04-22
Click [this](http://ubuntuforums.org/showthread.php?t=1961620) to go to the top of your thread, then open the Thread Tools menu and choose Mark as Solved.

---

### Post by andriansah on 2012-10-18
> **Vaphell said:**
> test this, maybe on some smaller set first
```
for f in *; do zip -9r "$f.zip" "$f"; done
```

You safe my life :)
Thank you very very very much

---

