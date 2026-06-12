---
title: "Directory Order in Console"
date: 2010-08-12
forum: General Help
---

### Post by a2yt25 on 2010-08-12
Hello everyone.

I'm using 10.04 now after upgrading from 9.04. Somewhere between the two releases Ubuntu changed the order in which the contents of a directory is listed in the console. ls, for instance, now lists the contents in the same manner that dolphin already did under 9.04.

Is there any way to set the filename order in which directories are parsed?       

This may seem like a rather minor 'problem', but in fact it's a pretty major one for me. I've got (at the moment) exactly 21,153 .wav files sitting on my hardrive and they are meant to be read by moc in a very specific order - an order which has just been trashed.                  

I know that I can fairly easily automate renaming all the files with a few simple scripts. But when the sequence output by the os in a terminal contradicts - and for what reason, I can't imagine - the sequence of the actual character table, I think it's a pretty stupid thing to have to do.

So I would really appreciate any answers about this.                                  

Thanks everyone.

---

### Post by a2yt25 on 2010-08-17
Even a little commiseration would be nice at this point....

Does anybody at least have an idea whether the file sorting depends on something in Ubuntu, is a kernel feature, or whatever?

This is pretty frustrating. Ubuntu's been out for - what - six years? And the Linux kernel's just short of twenty. What exactly is the point of changing something like the file sorting for the console now?

---

### Post by spibou on 2010-08-17
I'm not completely clear what you mean "file sorting for the console". Do you use *ls* on the console to print a list of files ? If yes then the output depends only on *ls* , not on the kernel and not on whether the output goes to console or anywhere else. Can you give us an example with a few files to see how the order changed ? Try using */bin/ls* instead of *ls* to get the files and see if it makes a difference.

By the way , what is moc ?

---

### Post by a2yt25 on 2010-08-17
Hey, thanks for the response.

Sorry, I should have posted more detail from the beginning.
Here goes a directory listing:

```

-rw-r--r-- 1 a2yt25 a2yt25 2.9M 2009-09-23 20:25 &#628;&#640;.10  :  A-Dur   ·  Allegramente.wav
-rw-r--r-- 1 a2yt25 a2yt25  22M 2009-09-23 20:25 &#628;&#640;.11  :  B-Dur   ·  Andante, ma non troppo.wav
-rw-r--r-- 1 a2yt25 a2yt25  31M 2009-09-23 20:25 &#628;&#640;. 1  :  B-Dur   ·  Allegretto.wav
-rw-r--r-- 1 a2yt25 a2yt25 9.6M 2009-09-23 20:25 &#628;&#640;. 2  :  C-Dur   ·  Andante con moto.wav
-rw-r--r-- 1 a2yt25 a2yt25  18M 2009-09-23 20:25 &#628;&#640;. 3  :  D-Dur   ·  à l'Allemande.wav  
-rw-r--r-- 1 a2yt25 a2yt25  17M 2009-09-23 20:25 &#628;&#640;. 4  :  A-Dur   ·  Andante cantabile.wav
-rw-r--r-- 1 a2yt25 a2yt25  12M 2009-09-23 20:25 &#628;&#640;. 5  :  c-moll  ·  Risoluto.wav
-rw-r--r-- 1 a2yt25 a2yt25  21M 2009-09-23 20:25 &#628;&#640;. 6  :  G-Dur   ·  Andante &#8212; Allegretto.wav
-rw-r--r-- 1 a2yt25 a2yt25  13M 2009-09-23 20:25 &#628;&#640;. 7  :  C-Dur   ·  Allegro ma non troppo.wav
-rw-r--r-- 1 a2yt25 a2yt25  22M 2009-09-23 20:25 &#628;&#640;. 8  :  C-Dur   ·  Moderato cantabile.wav
-rw-r--r-- 1 a2yt25 a2yt25 7.6M 2009-09-23 20:25 &#628;&#640;. 9  :  a-moll  ·  Vivace moderato.wav       


```

That's what I'm getting out of 'ls -hal' at the moment (doing it without the options makes no difference, which in this case do not affect the file sort anyway).

Because 1 through 9 are padded with a ' ' (a space to justify them with the double digits), they would sort &#8212; under 9.04 &#8212; before 10 & 11. 

I assumed (both mistakenly and stupidly) at first that what had changed at some point is that the sorting algorithm went from what some programmers call 'lexical' to 'natural'. This is incorrect: '1', '10', '2' is the order ls outputs. This is lexical order (so-called 'natural' would be 1, 2, 10). But even though ls is still sort of using lexical sorting, leading spaces are ignored (among other differences): hence, the new sorting order is no longer properly lexical either. I have no idea what it is.
 
MoC is Music on Console &#8212; an amazing ncurses music player: try it if you listen to music on your computer. MoC only reads the file order in whatever way &#8212; (this is the part I don't understand) Ubuntu? the kernel? the shell? I don't know &#8212; reads it. This is now a problem because the way whatever is sorting the directory contents has changed, and created the above problem. Under 9.04, moc read the above directory in the order: 1-11. Now, it reads: 10, 11, 1-9. This obviously has nothing to do with moc, because moc can't change the filename sort: it just accepts it from whatever is responsible for the sort.

Now, I've yet to try any other shell (I'm using bash &#8212; which I like). Perhaps that will solve the issue. I don't know. But I was hoping somebody here might have an idea about why the sort is different and if it can be changed. 

In any case, thanks for following up with me on this.

---

### Post by spibou on 2010-08-17
> **a2yt25 said:**
> 
That's what I'm getting out of 'ls -hal' at the moment (doing it without the options makes no difference, which in this case do not affect the file sort anyway).
I suggested trying */bin/ls* instead of *ls*  .Have you tried it ?

> Because 1 through 9 are padded with a ' ' (a space to justify them with the double digits), they would sort - under 9.04 - before 10 & 11. 

I assumed (both mistakenly and stupidly) at first that what had changed at some point is that the sorting algorithm went from what some programmers call 'lexical' to 'natural'. This is incorrect: '1', '10', '2' is the order ls outputs.
Actually in the output you posted the order is 10 , 1 , 2.

> This is lexical order (so-called 'natural' would be 1, 2, 10).
I would call the latter numerical rather than natural.
> But even though ls is still sort of using lexical sorting, leading spaces are ignored (among other differences): hence, the new sorting order is no longer properly lexical either. I have no idea what it is.
You are 100% certain that the file names have not changed , yes ? And that the output of *ls* in the same directory has changed between the 2 versions of Ubuntu ?
> MoC is Music on Console - an amazing ncurses music player: try it if you listen to music on your computer. MoC only reads the file order in whatever way - (this is the part I don't understand) Ubuntu? the kernel? the shell? I don't know - reads it.
Without seeing the source code for MOC it's impossible to tell. If it is written in C it likely uses the function *readdir()* .The order *readdir()* returns entries is dependent on the way the kernel organises the filesystem internally and in general will not correspond to any "everyday life" order like lexical , numerical or whatever.
 > This is now a problem because the way whatever is sorting the directory contents has changed, and created the above problem. Under 9.04, moc read the above directory in the order: 1-11. Now, it reads: 10, 11, 1-9. This obviously has nothing to do with moc, because moc can't change the filename sort: it just accepts it from whatever is responsible for the sort.
Actually it has everything to do with moc. A programme can read all the filenames for a directory , store them in an array or something and then sort them with whatever method it chooses ; it is not constrained by the order the operating system sorts the filenames internally. That's what *ls* does and that's why it can print the filenames using different ordering criteria depending on the command line options.
> Now, I've yet to try any other shell (I'm using bash - which I like). Perhaps that will solve the issue.
I doubt it , *ls* is a separate executable not a shell built-in and furthermore it is doubtful that moc uses *ls* to get the files.

So let me see if I understand. Under Ubuntu 9.04 both *ls* and moc sorted the files in some way A and under Ubuntu 10.04 both programmes use a new way B.

Are you sure that the spaces in the file names are really spaces i.e. that they have code 32 ?

---

### Post by a2yt25 on 2010-08-17
Sorry - yes, I tried /bin/ls. Same thing. 

I am also positive that the file names haven't changed, and yes, they are definitely decimal 32 spaces and not any other blank space. So: the output of ls in the same directory has definitely changed between the two versions of Ubuntu.

Since I wasn't too clear about exactly what was going on in my two posts above, below is a directory I created under 10.04:

```

-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 1
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 10
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 2
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 3
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 30
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 22:10  4

```

Under 9.04 the '4' would be at the top because of the leading space. And that's where I'm having the problem (besides a few other changes that are not as problematic for me as this one).

In any case, here's the punchline, and the joke's on me. In midnight commander, the sort is still done according to 9.04. So you are probably right that it is moc (and ls). It was dumb of me not to check the two against a third program, but it seemed inconceivable to me that both programs would change like that at the same time.

Still, I don't really understand why it's changed at all, but that's neither here nor there. I'd still like to know what exactly is going on at least as far as ls is concerned. (I've googled this on and off for the last few days and come up with practically nothing.)

Thanks a lot for all your help (and knowledge). I really appreciate it. I got the answer - or some kind of answer anyway - as soon as I read your reply.

---

### Post by spibou on 2010-08-17
Try ```
LC_ALL=C ls -hal
```and see if it makes a difference. If it does, post the output of```
echo $LC_ALL
```

---

### Post by spibou on 2010-08-18
Try also```
POSIXLY_CORRECT= LC_ALL=C ls -hal
```

---

### Post by a2yt25 on 2010-08-18
Okay - this is interesting:

```
% ls -hal

total 8.0K
drwxr-xr-x 2 a2yt25 a2yt25 4.0K 2010-08-17 23:18 .
drwxr-xr-x 5 a2yt25 a2yt25 4.0K 2010-08-17 22:08 ..
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 1
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 23:18  1
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 10
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 2
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 23:18  2
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 3
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 23:18  3
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 30
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 23:18  30
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 22:10  4

% LC_ALL=C ls -hal

total 8.0K
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 23:18  1
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 23:18  2
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 23:18  3
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 23:18  30
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 22:10  4
drwxr-xr-x 2 a2yt25 a2yt25 4.0K Aug 17 23:18 .
drwxr-xr-x 5 a2yt25 a2yt25 4.0K Aug 17 22:08 ..
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 20:17 1
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 20:17 10
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 20:17 2
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 20:17 3
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 20:17 30

% echo $LC_ALL

%

```

So then midnight commander is forcing the old order, and something else has really changed? 

Output of locale:

```
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

I should set the empty variables? Tomorrow: I'm done for the night.

But let me know where you're going with this, because all of this is still fairly vague to me (I'm not a programmer and learn only as I go along, like I'm doing now) but also really interesting.

Thanks.

---

### Post by a2yt25 on 2010-08-18
And:

```
% POSIXLY_CORRECT= LC_ALL=C ls -hal

total 8.0K                                                                                                       
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 23:18  1                                                                  
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 23:18  2                                                                  
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 23:18  3                                                                  
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 23:18  30                                                                 
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 22:10  4                                                                  
drwxr-xr-x 2 a2yt25 a2yt25 4.0K Aug 17 23:18 .                                                                   
drwxr-xr-x 5 a2yt25 a2yt25 4.0K Aug 17 22:08 ..                                                                  
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 20:17 1                                                                   
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 20:17 10                                                                  
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 20:17 2                                                                   
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 20:17 3                                                                   
-rw-r--r-- 1 a2yt25 a2yt25    0 Aug 17 20:17 30

```

---

### Post by a2yt25 on 2010-08-18
Alright, so this morning I've changed the LC_COLLATE variable to C.  It worked. Everything sorts according to the character table as before.

```

-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 23:18  1
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 23:18  2
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 23:18  3
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 23:18  30
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 22:10  4
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 1
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 10
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 2
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 3
-rw-r--r-- 1 a2yt25 a2yt25    0 2010-08-17 20:17 30

```

I really couldn't understand where the problem might even be: the application, the shell, the kernel, something else. Googling "sort order" "file order", etc., etc., turned up nothing, and the locale settings didn't even occur to me.

You've been a big help, and I really appreciate it.

Thanks!

---

### Post by spibou on 2010-08-20
Great , I'm glad you solved it but I think it's a kludgy solution. Having filenames which begin or end in space is an accident waiting to happen and in the long run I think you'd be better off renaming the files. Even better, use some notion of playlists from within the music player although I realise that with as many files as you've got this may not be practical.

> **a2yt25 said:**
> 
So then midnight commander is forcing the old order, and something else has really changed?
My best guess is that you somehow changed your internationalisation settings between the 2 versions of Ubuntu. Perhaps it was done automatically. Different processes can have different environmental variables (and of course may also differ on how they use them or even whether they use them at all) which is why *ls* was doing sorting differently than midnight commander.
> But let me know where you're going with this, because all of this is still fairly vague to me (I'm not a programmer and learn only as I go along, like I'm doing now) but also really interesting.   
You can get some more information on what locale variables are supposed to do [here](http://www.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap08.html#tag_08_02).

---

