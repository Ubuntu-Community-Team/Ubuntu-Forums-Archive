---
title: "Backup Solutions (Very Specific)"
date: 2010-05-05
forum: General Help
---

### Post by grnorris on 2010-05-05
I realize there's probably quite a few post about backup solutions but I'm looking for something in particular:

I'm looking for a backup utility that:
Works under linux (Ubuntu)                   [Required]
Can back up an entire hard drive           [Required]
Stores the backup as regular files          [Required]
Stores partition and boot data               [Optional but, highly preferred]
Runs Portably                                      [Optional]

If I can't get something that runs portably then any solutions for booting some version of Linux of an external hard drive with simple GUI and support for said backup program.

EDIT:  To be clear I'm looking to backup my 250GB internal Hard Drive to my 1TB external Hard Drive.

---

### Post by dino99 on 2010-05-05
goto synaptic, you find there several choices (search: backup)

---

### Post by grnorris on 2010-05-14
> **dino99 said:**
> goto synaptic, you find there several choices (search: backup)

I did a search in Synaptic but, I couldn't find anything that really matched what I was looking for other than possibly a couple that were for tape backups.  Since I have a 1TB EHDD and no tape such a thing wouldn't make any sense.

To further clarify:  My current backup solution is to use Windows Sync Toy to backup specific drives.  What I like about this is that I can replace a file simply by finding it on my EHDD, also if a friend wants something off of my internal I just connect my external and it's there (usually).

The problems are:  1.) It doesn't backup linux (Windows can't read ext4 and I'm not about to reformat just to switch to an older system), 2.) Since Windows doesn't have sleeping programs in the sense of linux I can't back up any 'running' files (Such as those in Program Files).  3.) I still have to rely on the built in backup system for the boot record which recently got screwed up and I had to do a lot of searching to figure out how to fix it.

---

### Post by Kobalt on 2010-05-14
Did you take a look at [Déjà-dup]("http://live.gnome.org/DejaDup/") (it's in the repos)? 
I'm using it to backup my eeePC and it's been working like a charm so far ...

---

### Post by grnorris on 2010-05-24
> **Kobalt said:**
> Did you take a look at [Déjà-dup]("http://live.gnome.org/DejaDup/") (it's in the repos)? 
I'm using it to backup my eeePC and it's been working like a charm so far ...

It's not quite clear if I can use this the way the I wanted.  As I said in my initial post I want something that can store the files to my external hard drive in a format I can easily use without the software.  In other words if I use this program to make a backup then later on need to access a file from my backup in Windows I need to be able to just plug in my hard drive and copy the file.

The site for the this DejaDup seems to suggest it might not work like that.

---

### Post by bumanie on 2010-05-24
Is dd commands what you are looking for? [See here]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/") + there are many more pages on the internet.

---

### Post by John Bean on 2010-05-24
For file backup rsync is ideal. There are several graphical front-ends for rsync if you don't like the command line - look at grsync for example.

Reliable, standard, hard to beat.

---

### Post by grnorris on 2010-09-07
I realize it's been quite a while since I posted in this thread but, I wanted to update my findings.  Admittedly I stopped looking for a while, while I took care of other more pressing issues but, having gone back to my searching I found the following:  [http://www.jupiterbroadcasting.com/?p=2649](http://www.jupiterbroadcasting.com/?p=2649)

I found my way to there forums and asked a similar question to the one I made here and they suggested I try Mondo Rescue.  Since I've been quite busy with College starting back up I've yet to actually try it but, I've finally booted back into Ubuntu and have downloaded the program.  With any luck I'll get a chance to test it soon.  When I do I shall post back here as well as there site.

---

### Post by lbrty on 2010-09-07
> **grnorris said:**
> I realize it's been quite a while since I posted in this thread but, I wanted to update my findings.  Admittedly I stopped looking for a while, while I took care of other more pressing issues but, having gone back to my searching I found the following:  [http://www.jupiterbroadcasting.com/?p=2649](http://www.jupiterbroadcasting.com/?p=2649)

I found my way to there forums and asked a similar question to the one I made here and they suggested I try Mondo Rescue.  Since I've been quite busy with College starting back up I've yet to actually try it but, I've finally booted back into Ubuntu and have downloaded the program.  With any luck I'll get a chance to test it soon.  When I do I shall post back here as well as there site.

I use FreeFileSync. In my opinion, I think it works the best and is the simplest to use.

[http://sourceforge.net/projects/freefilesync/](http://sourceforge.net/projects/freefilesync/)

---

