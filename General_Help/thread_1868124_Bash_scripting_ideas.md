---
title: "Bash scripting ideas"
date: 2011-10-23
forum: General Help
---

### Post by huntaz556 on 2011-10-23
I'm just starting to try bash scripting and i find that if i try to learn a language getting a project helps me learn it so can you guys give me a bash scripting idea for a beginner? thank you so much !

---

### Post by Rhizoid on 2011-10-23
How about:

A script to backup your home folder, once daily, to a folder named for the current day of the week, keeping 7 daily backups (including the current day) as history.  Either use rsync or tar to perform the actual backup.

Future Enhancements:
Have it check for disk space before attempting the backup and pause the script, email an alert to you and then wait until sufficient disk space is available.

Have it write you a report showing start time, end time and quantity of data copied.

Have it offer a choice of tar or rsync.

---

### Post by Gadgetech on 2011-10-23
Here's a little tutorial I did on using while loops in a bash script: [http://tuxtweaks.com/2009/09/bash-to-basics-the-while-do-loop/]("http://tuxtweaks.com/2009/09/bash-to-basics-the-while-do-loop/")

You can find some more ideas at: [http://tuxtweaks.com/category/bash/]("http://tuxtweaks.com/category/bash/")

---

### Post by hwttdz on 2011-10-23
Is it too late to suggest perl as an alternative?

How about a useful one, a backup script.  

And then depending on how "into it" you want to get a possible wishlist for a backup script would be 
1) accepting different compression algorithms as arguments
2) checking for the presence of different compression programs and using the "best" one it finds
3) comparing the size of today's archive to yesterdays and sending the user an email if it changed significantly
4) writing itself into the crontab if called with the correct arguments (while removing any instances of itself already in the crontab, hint: crontab -l|grep)

Rhizoid beat me to it, anyways there are lots of enhancements to this sort of script.  I might have to incorporate some of Rhizoid's into my own (checking for disk space).  But I find that mine never take more than a minute in any case, though I classify all media but pictures as expendable, and I do those through a different process.

I looked through my scripts directory (121 scripts) only a handful are written in bash and most of those are only a few lines long.

---

### Post by conradin on 2011-10-23
Have any problems you want solved, or things you like to do?
I really enjoy networking type issues, but Im on a huge network.
[http://maketecheasier.com/8-useful-and-interesting-bash-prompts/2009/09/04](http://maketecheasier.com/8-useful-and-interesting-bash-prompts/2009/09/04)
some of those look fun. 

Music conversions?
Image resizer?
file uploader?
automation?...

it really depends on what you find fun, interesting, and useful.

Something which only occurs on boomtime (see ddate command)
something which greets you merily to the celibratory Discorian holidays when they occur (see ddate command)...

---

### Post by huntaz556 on 2011-10-23
OOOHH i like the backup idea and ive never tried perl so maybe ill try it some time. im yet to click on the link you gave me so i will look at that right now thanks for the ideas ! :p

---

### Post by huntaz556 on 2011-10-23
Hi i started my backup script and with the backup i made i wanted to try to restore from it just to see how it worked but at the end i get this. 

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
your restore is complete

is this somthing to worry about?

is it a simple fix?

i dont exactly want a direct answer on what to do to fix it just tips thank you !

---

### Post by hwttdz on 2011-10-26
I think the place to start here would be familiarizing yourself with tar (both with and without compression and gzip).  Tar is your archiver, but it doesn't necessarily compress the files.  For example I use tar to archive but not compress because I'm happier with the compression speed-size tradeoff using a different compression program.  That said tar supports a bunch of common compression programs.  And I could easily use one of the ones it supports, I just think I can do slightly better.  

So, I'd start with a single folder with some random files in it, and try 
1) tarring without compression and untarring to get the original back
2) tarrring with compression and untarring to get the original back
3) tarring without and compressing independently, then using tar to both uncompress and unpack
4) tarring without and compressing independently, then uncompressing independently and untarring
5) tar to standard out and compress that then uncompress (slightly weirder and more complicated, you also have to understand some about how "pipes" work)

In every case you should be able to get the originals back, and it will familiarize you with both your archiver and independent compressor should you choose to use one.  Or at least it will make it clear exactly where your problems are occurring.  Good luck, you're definitely on the right start.

Sidenote: large text files compress well, and are easy to come by.  
[http://www.gutenberg.org/browse/scores/top](http://www.gutenberg.org/browse/scores/top)

---

