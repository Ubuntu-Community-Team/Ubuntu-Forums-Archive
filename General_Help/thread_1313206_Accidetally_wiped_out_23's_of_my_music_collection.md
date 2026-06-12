---
title: "Accidetally wiped out 2/3's of my music collection"
date: 2009-11-03
forum: General Help
---

### Post by blur xc on 2009-11-03
Well, it's all pretty much my fault.  

[LONGSTORY]
Well, My wife and I have been spending a pretty fair amount of time ripping our CD collection over to the computer, to eventually put on the ipod.  Now, I noticed that compilation albums were coming in as a separate instance for each artist on the album, and that annoyed me.  It made it impossible to listen to an entire soundtrack or album in one shot.  So, in nautilus, I merged all instances of each compilation album under the "Various Artists" folder in my music directory.  I should note most was ripped in Rhythmbox, but I just started dabbling in Banshee, which I kind of like better.  But, when I opened Banshee, it didn't re-sync with my music folders, which I thought was odd.  I seem to recall Rhythmbox would do that each time you opened it.  So, not finding a "sync folders" menu option or button anywhere, I clicked import music.  But, stupid me, didn't notice the "copy to location" option in edit -> preferences.  So, I duplicated my whole music collection, 1300 songs, now 2600...  Now I'm frustrated, some music was duplicated in the same folder as the originals, other music was copied to new directories.  I guess Banshee tries to look up the correct album/artist names and name the folders correctly.  If the folder was already named correctly, it'd duplicated the files to the same directory, if it wasn't, it'd make a new folder...  So great...

Now, at this point, I REALLY should have consulted the forums.  I'm trying my hardest to learn the command line, and thought I could tackle this one on my own.  I realized I could execute a find command to find all the recently created files, and remove them.  Now, I'm not a complete idiot, so first I ran my find command to just display the result on stdout.  When that "looked" good, I added -exec mv '{}' /home/shared/deletme \; to move them to a quarantine folder, and then if it all looked good, I could then delete all of them.  Smart, right?

Well, I probably should have checked my test run a bit more carefully.  Apparently, some of the artist folder names got a new time stamp, even though there were files in it's sub-directories were ones I wanted to keep.  So, it moved the parent folders, child folders, and random files with the recent time stamp, but the sub directories with the old time stamp went off to la la land...  Purgatory, maybe?  Either way, they flat out disappeared.  

thinking back, I really should have ran the command to find files only, and not directories.  then maybe I should have ran a 2nd command to remove all empty folders, if that's possible, which I'd be surprised if it wasn't, since just about anything is possible at the command line.

So, now only about 500 songs of the original 1300 remain...  :(
[/LONGSTORY]

Anyway, lesson learned.  When in doubt, ask on the forums first.  

BM

---

### Post by Random-penguin on 2009-11-03
Also, when in doubt do a backup first!!!! But I guess that's just rubbing salt into your wounds!! Hope the wife has forgiven you and you're not still banished to the naughty stair?

---

### Post by howefield on 2009-11-03
> **Random-penguin said:**
> Also, when in doubt do a backup first!!!!

(S)he does have a backup, the music was ripped from CDs. Just means a lot of work ripping `em again.... :(

---

### Post by zorrofox on 2009-11-03
At least you've still got the original CD's mate, things could have been a lot worse. I have some 56,000ish tracks here, losing a third of that would be like a death in the family :lolflag:

Gordon.

---

### Post by Random-penguin on 2009-11-03
That's true! It's quicker to not have to re-rip half your CD collection, though. I remember when my hard-drive failed and I wasn't on the internet.... It was a nightmare retyping all those albums.... [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]  In fact it nearly drove me insane!!!

---

### Post by zorrofox on 2009-11-03
I'm old enough (and sad enough) to remember typing up all the details of my record and tape collection back in the very early 8o's(b.c.)* Being something of a perfectionist even back then I would get to around 'F' and decide the format wasn't right and rip it up and start again :-k

Gordon.

* - before computers

---

### Post by blur xc on 2009-11-03
Thanks for the support.  Actaully, and surprisingly, she was a lot less upset than I was/am...


So- back to ripping!  Better now than when we were done, since we've only ripped about 1/3 of the collection so far..  maybe...  There are still a lot of cd's we can't find.  They got put somewhere in storage many, many years ago, throw in a couple of moves, and they haven't turned up yet...

BM

---

### Post by mrpeachy on 2009-11-03
theres a program called photorec [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) which can recover lost data and run on linux.  i used it recently to recover some lost jpg's, but it can also recover mp3's and alot of other file formats.

---

### Post by Saprissa on 2009-11-03
I like FSlint to find duplicate files.

 sudo apt-get [install fslint]("apt:fslint")

More here...[http://www.pixelbeat.org/fslint/](http://www.pixelbeat.org/fslint/)

---

### Post by Random-penguin on 2009-11-03
Photorec is a good program. I've used it to recover files off a corrupted SD card. The poor owner of said card was really upset as it contained only copies of family photos and was over the moon when I recovered them.If you are recovering data you really don't want the drive mounted as this will increase the chances of the files being written over. So use the live System Rescue CD, which is really light on resources (thus fast) and can be sourced via Distrowatch.

---

