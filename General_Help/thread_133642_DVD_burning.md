---
title: "DVD burning"
date: 2006-02-20
forum: General Help
---

### Post by jasrog on 2006-02-20
Is there a command available to install something in ubuntu that decrypts dvd's so I can back-up my dvd movies?

---

### Post by ardchoille on 2006-02-20
I just spent two weeks going through this. My experience showed me that yes there are a number of apps to rip/backup/copy DVD movies. However, they all only work right less than half of the time. I tried acidrip, dvd::rip, xdvdshrink, K3b, dvdbackup and I even installed wine so I could run the Windows version of dvdshrink. I found that none of them worked as advertised more than half of the time. It's all simply a waste of blank DVD's.

---

### Post by wargames on 2006-02-20
[QUOTE=jasrog]Is there a command available to install something in ubuntu that decrypts dvd's so I can back-up my dvd movies?[/QUOTE]

Install dvdbackup from the repository.

Then insert your DVD movie in the drive and type this in the terminal:

dvdbackup -i /dev/dvd -M -o dir/

This will backup the whole DVD movie with extras and menus, etc. You might want to have a Dual layer burner for this too. It will put the backup in the directory that you put in place of dir/. example: dvdbackup -i /dev/dvd -M -o backupmovie/

After it finishes this then insert your blank DVD disc into the drive and type from terminal:

growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video dir/

example using the backupmovie/ directory that contained my backup would be:
growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video backupmovie/

The dvdbackup command will put into the backupmovie/ subdirectory the disc title of the movie. So be sure to include that at the end of the growisofs command. Such as:
growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video backupmovie/GHOST/

This works great, and I can backup my DVD movies with way even dual layer movies.

---

### Post by ardchoille on 2006-02-22
OK, I don't know what I was doing wrong, but I followed the above tutorial by wargames and successfully copied 13 of my purchased DVD's without a single problem or coaster. Maybe the problem was that I was not running everything with sudo, I don't know.. but it works as wargames described.

@wargames:  Thanks for posting that tutorial, it works perfectly.. much appreciated :)


EDIT: I automated the whole process and wrote a bash script for it. You can find my Easy DVD copy script in [this thread]("http://www.ubuntuforums.org/showthread.php?t=134976").

The script works quite well and I would like to learn how to make it even better.. so take a look and post any ideas you may have :)

---

### Post by Abandon on 2006-02-23
[QUOTE=jasrog]Is there a command available to install something in ubuntu that decrypts dvd's so I can back-up my dvd movies?[/QUOTE]
There are several way' s:

1. install vobcopy. And use it like: vobcopy -m and that copies the content of the entire dvd (without encryption) on you're harddisk. Burn it on a DL dvd with K3b

2. use xdvdshrink: google for the .tar.gz. It works very good, although it was made for Mandriva .

3. Use Wine of Crossover Office with dvdshrink (windows)

---

### Post by seanmc42 on 2006-04-01
I don't get it - I just used this exact technique to create 3 DVD backups - the fourth one failed.
I am using Memorex Dual-layer media (Media ID: Ritek/D01) in an Hp dvd640 lightscribe burner.
I have DMA enabled.

My command-line was: 
"sudo growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video dir/"
executed from the parent directory of dir.
growisofs indicated its write speed was  2.5x1385KBps.

The error, @ 0.81% (right at the beginning), was 

:-[ WRITE@LBA=8720h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
builtin_dd: 34592*2KB out @ average 0.8x1385KBps
:-( write failed: Input/output error

Why does this work so inconsistently?

---

### Post by ubuntukid on 2006-04-19
I know this is an old post but I thought I would just post this incase someone is having problems using this program.

Before you run the dvdbackup command, let the dvd play for a few seconds in totem or something like that. Then pause the film and start the dvdbackup program. It should now work without a problem. When I don't do this it usually only gets halfway and then stops telling me it can't read a file but if I leave totem paused on the main title, or one of the main titles, it works every time. I don't know why.

---

### Post by az on 2006-04-19
If you right-click on the dvd icon, you can select "copy" and make an image of it and burn it (if you have a dual-layer burner you can do it straight)

If you want something like dvdshrink, install k9copy.

xdvdshrink is old and abandoned.

---

### Post by ubuntukid on 2006-04-19
You can't just copy a dvd using normal methods (maybe gnome doesn't use normal methods) because the css encryption will kick into action. The movie checks to see if the css encryption is present on a disk before playing on a dvd player. On blank dvd's this area is filled with 0's so you don't get this info copied over. The dvd will then refuse to play and simply spit out the disk. Tools designed for copying a dvd movie on the other hand uses toll like DeCSS to remove this security check and gives you and iso file you can actually use.

Of course if it's not encrypted these programs won't be needed and you can simply use regular copying methods.

---

### Post by airtonix on 2006-04-23
umm wheres the script dude?

---

### Post by Coruba67 on 2006-05-06
I have gnome installed and used apt-get to install K9Copy... anyone know how I can now access this program... can't seem to find it anywhere!?

---

### Post by Brandel Valico on 2006-06-08
Just wanted to say thanks to Wargames for posting this. Not being able to back up the DVD's I own was one of the biggest issues I had with ditching windows. With that problem solved thanks to this post by you and the addition of Wine and DVDShrink to convert them down to dvd5 I'm one happy guy. 

Though a script to copy compress and burn them would be a great thing. If I ever get more knowledgable at writing them. I might just work on it.

---

### Post by geetarista on 2006-07-16
So...does anyone have a copy of this script or know where to find it?

And does anybody know how long it typically takes for this process to take?

---

### Post by Brandel Valico on 2006-11-07
Actually if you have K3B and K9Copy installed on Edgy for sure. You have no need for it. Just stick the DVD into the drive and open it in K9 set it to burn an ISO image and make sure to set it to burn with K3B in the Settings of K9. It will copy it to a folder condense it down to fit the size of a normal disk and then automatically open K3B and be ready to burn. So take out the DVD and put in a Blank and let it burn away. 

It's a perfect method and I have had more success with it then the method above which I used until finding out about this method. Both do work well though.

As for how long.... Depending on the movie it is actually around 5 to 10 minutes quicker then it would be on a windows machine. (Tested this several times) It comes out to around 15 minutes for me. Less if it doesn't have to compress it to fit on a standard disc. The DVDShrink and such method usually took me around 25 to 30 minutes. 

But time well spent when it saves your originals from the fate of having your 4 year old cousin deciding your movie collection is shiny and he needs to rub them all over the carpet and any other surface he wants to. Instead of killing him I simply went and dug out the originals and reburned them and stuck them back on the shelf where I keep the ones I watch.

---

### Post by SloYerRoll on 2008-03-04
How can I get to the DVD Backup preferences? I'd like to change where the file writes to so all my DVD's are copied to an external HD.

---

### Post by harvodan on 2008-03-17
The option you want is under /settings/preferences in the menu, but you should be prompted for the location you want to use when you start copying a dvd.

---

### Post by dan_james6_6 on 2008-05-30
You guys should try Total Video2DVD.  I never have any problems with it.  I've made quite a few AVI to DVD conversion with no problems and the program is quick too.  It can convert more than just avi to DVD.  Check out [www.effectmatrix.com](www.effectmatrix.com) and get the free download there.

---

### Post by MikeCheck on 2008-06-08
> **Brandel Valico said:**
> Actually if you have K3B and K9Copy installed on Edgy for sure. You have no need for it. Just stick the DVD into the drive and open it in K9 set it to burn an ISO image and make sure to set it to burn with K3B in the Settings of K9. It will copy it to a folder condense it down to fit the size of a normal disk and then automatically open K3B and be ready to burn. So take out the DVD and put in a Blank and let it burn away. 

It's a perfect method and I have had more success with it then the method above which I used until finding out about this method. Both do work well though.

As for how long.... Depending on the movie it is actually around 5 to 10 minutes quicker then it would be on a windows machine. (Tested this several times) It comes out to around 15 minutes for me. Less if it doesn't have to compress it to fit on a standard disc. The DVDShrink and such method usually took me around 25 to 30 minutes. 

But time well spent when it saves your originals from the fate of having your 4 year old cousin deciding your movie collection is shiny and he needs to rub them all over the carpet and any other surface he wants to. Instead of killing him I simply went and dug out the originals and reburned them and stuck them back on the shelf where I keep the ones I watch.

I realize this is a pretty old topic now, but I attempted this method and received an error message when I played new DVD.
"The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

How do I set K3B and K9Copy to decrypt the DVD?

---

