---
title: "Is there a file/folder shredder for Linux?"
date: 2011-10-05
forum: General Help
---

### Post by pretty_whistle on 2011-10-05
At the moment I have a file I'd like to shred so it can't be recovered with computer forensics.  It's a privacy thing and I have the need sometimes.

I heard file shredders don't/can't work on Linux.  Is this true?

I would like a good file/folder shredder if it's possible.

I have a program called Bleachbit which says it can wipe free space which takes care of deleted files.  Problem is I'd like to shred individual files/folders and not have to wipe all the free space since it takes longer to do that.

---

### Post by meatytaco on 2011-10-05
I haven't used it, but a google search led me to this

[http://stan.wong.com/wp_stan/2008/07/18/linux-file-shredder/]("http://stan.wong.com/wp_stan/2008/07/18/linux-file-shredder/")

Was built in to mine :)

---

### Post by ubupirate on 2011-10-05
This article may also help (even though it's from 2009):

[http://techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/](http://techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/)

---

### Post by meatytaco on 2011-10-05
also try in the terminal
```
man shred
```

make sure thats what you are looking for

---

### Post by piratebill on 2011-10-05
shred -zuv always does right by me

---

### Post by pretty_whistle on 2011-10-05
> **piratebill said:**
> shred -zuv always does right by me
??

---

### Post by pretty_whistle on 2011-10-05
I tried typing this in root termminal but it failed, claiming no such file:

shred -u -z -n 3 liar handout.odt

???????? What's wrong?

---

### Post by meatytaco on 2011-10-05
were you in the correct folder? If thats the case, you'll have to either "cd" into the folder the file is in, or give it the complete path.

---

### Post by pretty_whistle on 2011-10-05
Rather than using terminal I was hoping there'd be a separate program for this - one where I could just hit a button and it would shred for me (no commands to use).

---

### Post by ubupirate on 2011-10-05
> **pretty_whistle said:**
> Rather than using terminal I was hoping there'd be a separate program for this - one where I could just hit a button and it would shred for me (no commands to use).

Bleachbit can do individual files/folders from it's GUI, but not sure how well it does it or what algorithms it uses to shred.

File -> Shred Files or File -> Shred Folders.

---

### Post by meatytaco on 2011-10-05
> **ubupirate said:**
> Bleachbit can do individual files/folders from it's GUI, but not sure how well it does it or what algorithms it uses to shred.

as long as it does "passes" i would think this would work :)

---

### Post by ubupirate on 2011-10-05
> **meatytaco said:**
> as long as it does "passes" i would think this would work :)

Tried test file using Shred Files option:

```
Delete 802.8kB /home/me/Documents/UrbanTerror/ioUrTded.i386

Disk space recovered: 802.8kB
Files deleted: 1
```Absolutely no indication if the file was actually shredded or not, no indication of passes, algorithms or zero'd out to hide the shred.

:/


@pretty_whistle: I think your best bet would be to either cd to the directory of the file and run the shred command, or provide a full path to the file in the command itself as suggested in another post.

---

### Post by meatytaco on 2011-10-05
i got this from the verbose output

```
lobos@Taquito:~$ shred -u -z -v test 
shred: test: pass 1/4 (random)...
shred: test: pass 2/4 (random)...
shred: test: pass 3/4 (random)...
shred: test: pass 4/4 (000000)...
shred: test: removing
shred: test: renamed to 0000
shred: 0000: renamed to 000
shred: 000: renamed to 00
shred: 00: renamed to 0
shred: test: removed
lobos@Taquito:~$ 

```

Edit:
-u "truncate and remove file after overwriting"
-z "add a final overwrite with zeros to hide shredding"
-v "show progress" 
just to show what the options were for

---

### Post by Bucky Ball on 2011-10-05
Bleachbit would do the trick but ***be careful***! It can do some real damage if you stuff up. ;)

It has GUI.

---

### Post by meatytaco on 2011-10-05
also you can use the -n [number] option to tell shred how many passes to make over the file

---

### Post by pretty_whistle on 2011-10-05
> **ubupirate said:**
> Bleachbit can do individual files/folders from it's GUI, but not sure how well it does it or what algorithms it uses to shred.

File -> Shred Files or File -> Shred Folders.

You're right!

Ok.... WHO has gone and filled me with Doh?!!  It was sitting right there and I didn't see it!  DUH! :o :rolleyes:#-o:biggrin:

---

