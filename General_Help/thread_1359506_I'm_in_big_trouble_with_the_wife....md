---
title: "I'm in big trouble with the wife..."
date: 2009-12-19
forum: General Help
---

### Post by holepunch on 2009-12-19
I got a new toy (plugcomputer) that can boot from SD cards.  My wife's laptop has got an SD card reader built in so I borrowed it and booted from an Ubuntu LiveCD reassuring her nothing could possibly go wrong.

Anyway, to cut a long story short I used fdisk and ran 'mkfs.ext3 /dev/sd**a**2' instead of 'mkfs.ext3 /dev/sd**b**2' and accidentally wiped her NTFS Windows partition (boot/documents etc.).  She has no backup and I'm so not getting any Christmas presents if I don't get it sorted.

I've had a good read on the forums but wanted to ask specifically about my personal situation.  I was using a LiveCD, I didn't install anything on the formatted partition because I realised straight after and on reboot the machine says Operating System Not Found so in theory other than damage caused by the formatting process everything should still be there.

What would be the best thing for me to do in this situation?  Is it possible to restore the partition to NTFS and continue as if nothing has happened?  What exactly does fdisk do when you format to ext3?

Any advice gratefully received.

---

### Post by serpantman on 2009-12-19
You need to run recovery software using a surface scan. You can recover the important documents this way easily. Run it from another OS on the drive if you have 1. Otherwise you gotta stick it in another box. Post back if you need more help. BTW, this will only recover files, it wont make the system work again, but you can recover everything important.

EDIT: Just thought that maybe if you had a linux installed on a usb you could do it from that, since its writable you can install the proper tools np.

---

### Post by holepunch on 2009-12-19
I've got a copy of System Rescue CD that has got TestDisk on it.  Can you clarify what you mean by 'run recovery software using a surface scan'?

---

### Post by bear24rw on 2009-12-19
first thing i would do would be reboot the live cd and try to photorec the documents back to an external, im not sure how to recover the partition but im sure it can be done

---

### Post by serpantman on 2009-12-19
bear24rw is giving you examples of progs to run, I dont have expierence with that one.

 I know a prog called recovery for windows, that is freeware. And another one for windows. I've used them to recover files for other ppl that they deleted on accident, OR forgot to copy before they reformatted and reinstalled windows. Even after reinstalling windows i recovered most of the files. So dont sweat it too much. By surface scan  i mean an option that the recovery programs usually have. It ignores the FS/partition and just physically looks for files. <-- that was a guess. But it works good. Try photorec and look for more progs if that doesnt work.

What are your options? Is there another OS install on the laptop? If not run from a live disc(ubuntu), install the software, and find the files. It takes a long time. All jpg's will be labeled 000001.jpg 00002.jpg etc. in no particular order. I dont know what the perfect prog is, but just google recovery software ubuntu etc... You'll find something you can owrk with im sure.

EDIT: If you had a Backtrack live cd that probably has the tools you need.

---

### Post by Darael on 2009-12-19
Testdisk should recover your files very nicely indeed - chances are they're all still there, even the names, and you just need to recover the partition table. Boot into a live CD, install testdisk to the live session, and run it on /dev/sda - partition table type is probably "DOS". That ought to do it.

---

### Post by Leppie on 2009-12-19
there's cd images on the net that contain tools to recover partitions. a particularly handy image is Hiren's Boot CD. i've never tried to recover a formatted partition myself, but have had success undeleting one ;)

Save everything you can recover first of course

---

### Post by holepunch on 2009-12-19
Your reassurances are welcomed - I might not have to sleep outside in the snow after all.

In the morning I'm going to purchase a suitably large external hard drive then I'm going to boot System Rescue CD.  That has TestDisk installed which says something about making an image which I assume would be a sensible first step in case I accidentally cause any more damage.  Does anyone know what I can do with the image once I have it? Can I work on the image to reduce unnecessary use of the drive?

Following that I'm going to run PhotoRec to get as many original files off the disk as possible.

Finally I'm going to look into recovering partitions and Hiren's Boot CD.  Is it possible that I might be able to change it back to NTFS and avoid having to tell her she needs to hand her work laptop to the technicians to have Windows re-installed and explain that even though she isn't allowed to use it for anything other than work her loving husband accidentally reformatted it? 

Any further suggestions/pointers/specific advice based on my plan of action gratefully taken on board.

---

### Post by Leppie on 2009-12-19
> **holepunch said:**
> In the morning I'm going to purchase a suitably large external hard drive then I'm going to boot System Rescue CD.
this is an excellent start ;)

> **holepunch said:**
> That has TestDisk installed which says something about making an image which I assume would be a sensible first step in case I accidentally cause any more damage.  Does anyone know what I can do with the image once I have it? Can I work on the image to reduce unnecessary use of the drive?

Following that I'm going to run PhotoRec to get as many original files off the disk as possible.
i'd suggest to try to use PhotoRec on the created image, if it can handle that. like this, you can even make mistakes during the recovery process.

> **holepunch said:**
> Finally I'm going to look into recovering partitions and Hiren's Boot CD.  Is it possible that I might be able to change it back to NTFS and avoid having to tell her she needs to hand her work laptop to the technicians to have Windows re-installed and explain that even though she isn't allowed to use it for anything other than work her loving husband accidentally reformatted it?
as i wrote before, i've never tried to recover a formatted partition. not sure how much changes are made by creating the new partition table. but after creating the image and recovering the important files, you can always try.

usually pc's that ship with windows also have a rescue partition (often on the first partition which is hidden). this may not get your documents back, but it will set your windows partition to factory defaults.

---

### Post by Rhubarb on 2009-12-19
The easiest way to clone an image to a backup hard drive would be to use Clonezilla.
[http://clonezilla.org/](http://clonezilla.org/)

Just make sure you do a bit-for-bit clone, so it copies over everything in the partition to a new spare hard drive.

Then once you have the clone, use photorec to recover documents.
photorec actually comes with the testdisk package.
You could probably just use testdisk rather than photorec, it's just that I've found from experience that photorec is much easier to use for recovering files.
But testdisk could be the right choice for recovering partitions.

If you do manage to recover the partition, you could use clonezilla to copy the recovered partition back to the laptop.  Just make sure you've got a backup of the old partition (pre-fixed up) just in case.

You may want to play with clonezilla and testdisk on a separate computer that's been backed up first, just so you can familiarise yourself with the apps.

For backing up computers, clonezilla is the best, especially if you've got a big hard drive to store the images on (compressed images are best for backups, but a bit-for-bit copy is best for you in this specific case).

As for the wife, perhaps it's best to get some flowers for her so you won't have to sleep outside tonight ;)

---

### Post by holepunch on 2009-12-19
Thank you very much for all your advice.  I'm going to monitor this thread in case anyone has any further suggestions to add and more importantly I'll post back to let you know how it goes.

P.S. I think it's going to take more than flowers - she's had her eye on some GHD's that I've been refusing to pay out for and saying that they do nothing more than a set for twenty quid would do...

---

### Post by hachre on 2009-12-19
Damn, stuff like that sucks, hope you'll get it sorted!

---

### Post by Leppie on 2009-12-19
> **holepunch said:**
> P.S. I think it's going to take more than flowers - she's had her eye on some GHD's that I've been refusing to pay out for and saying that they do nothing more than a set for twenty quid would do...

looks like your experiment is going to cost you about 10 times that cheap thingie...

---

### Post by seeker5528 on 2009-12-19
> **holepunch said:**
> I've got a copy of System Rescue CD that has got TestDisk on it.  Can you clarify what you mean by 'run recovery software using a surface scan'?

Preferably before doing anything that would write changes back to the hard drive, you would want to have an external disk attached, with enough room to hold at least the important files if not all the files.

If you have got System Rescue CD, you should be able to scan for an NTFS partition with than, if it finds it (after the initial scan you might have to do the deep scan), you should have the option to browse the files, while you are browsing the files you should have the option to copy files, if your external disk is attached and the partition you want to copy the files to mounted, when you choose to copy files you should be given the option to browse for the location to copy to where you can can browse to the location you mounted your partition on the external drive and choose that as the destination.

At this point it would be preferred if you had another computer where you could check out the files you copied to see that things look OK, or failing that a live CD that includes software that would allow you to view enough of the important files to determine if you think thing are OK.

If test disk showed you multiple listings for the same partition you might have to try them all to figure out which one seems the best.

If everything checks out you can go back to test disk, search for the partition again, select the one that seems correct and have testdisk write the partition data.

Photorec is an option, but is kind of a last resort because none of the files will have their original names and most likely there will be many files that are incomplete because photorec doesn't deal with fragmentation well. Magicrescue is another option that should be on System Rescue CD, may or may not handle fragmentation any better than Photorec and probably still leaves you with a pile of files without their original name.

If testdsik doesn't get the job done and you have a windows computer you can attach the drive to and run the recovery from, the next best solutions I have personally seen in action are [ GetDataBack ](http://www.runtime.org/data-recovery-software.htm) or [ R-Studio ](http://www.r-studio.com/).

GetDataBack you can download and try out and get a pretty good idea if it will work for you or not.

Theoretically you could do the same with R-Studio, but in trial mode you can not recover files bigger than 64k, which doesn't give you much to go on, but maybe the previewer works well enough to see what you need, it does have the option to create an emergency disk to boot and run it from, but you still need a windows machine to install it on to be able to create the emergency disk. 

Later, Seeker

---

### Post by holepunch on 2009-12-20
> **seeker5528 said:**
> If everything checks out you can go back to test disk, search for the partition again, select the one that seems correct and have testdisk write the partition data.

I got a 1TB drive which when mounted in System Rescue couldn't be written to because it was formatted as NTFS so I plugged it in to another machine and reformatted at FAT32.  Then I've spent the rest of the day trying to image the laptop drive before I do anything else to it but the 4GB limit for FAT32 kept getting in the way.  I discovered instructions part way down this page: [http://www.softpanorama.org/Tools/dd.shtml]("http://www.softpanorama.org/Tools/dd.shtml") that describes how to split files and recombine them using dd.  This is currently doing its thing so fingers crossed.

When I have my images stored safely I'm going to use photorec to get as much off the drive as possible before attempting what Seeker describes in the quote.

Can anyone offer any further clarification/notes/experience/pointers with that stage in particular?

---

### Post by eltama on 2009-12-21
I'm having a similar problem and unfortunately, I am starting to loose my faith.
Yesterday I was sleepy and while trying to reinstall Windows I misclicked the partition table and reformatted the partition with all my personal files.

I've tried gparted, gpart and testdisk but they are not helpful because the partition is not deleted, it has been reformatted, so it's there, but empty. testdisk has an option Rebuild BS which I hoped could work, but it didn't (see [http://ubuntuforums.org/showthread.php?t=1359466&highlight=formatted+partition]("http://ubuntuforums.org/showthread.php?t=1359466&highlight=formatted+partition").

I've tried photorec, but it's not useful for me. I have hundreds of gigabytes with all kind of files and photorec tries to recover them putting all files together in a ramdom order with auto-generated file names. Most of the files are useless or broken (lots of txt with bits of text, corrupt videos and mp3s, etc). After running it for hours, I could only pick some files, mostly photos.

Even if photorec could recover all the files correctly (which it doesn't), it is useless if you have a huge amount of data. I think it's useful if there are only few files of the same type (like the photos in a camera) or if there are a few specific files that are worth one or two days of cherry picking.

I will try Hiren's boot cd and maybe some other tool, but as I said, I don't have much expectations.

---

### Post by Grenage on 2009-12-21
If you're working with windows (or NTFS), I personally recommend "get data back for NTFS".  It's one of the best out there, and it doesn't cost much.

---

### Post by eltama on 2009-12-21
According to [https://www.runtime.org/ccform_eu.htm]("https://www.runtime.org/ccform_eu.htm") GetDataBack for NTFS costs 94 euros. That's too much for me but may be worth for some people.

Oddly, it also costs 79 dollars. Shouldn't it be the other way round?

---

### Post by Leppie on 2009-12-21
> **eltama said:**
> According to [https://www.runtime.org/ccform_eu.htm]("https://www.runtime.org/ccform_eu.htm") GetDataBack for NTFS costs 94 euros. That's too much for me but may be worth for some people.

Oddly, it also costs 79 dollars. Shouldn't it be the other way round?

GetDataBack is included in Hiren's boot cd (both fat and ntfs versions).

---

### Post by eltama on 2009-12-21
After 2 hours of looking at web pages of many programs to see what they offer, I decided to start with Hiren's cd and I saw that it includes GetDataBack :)

I've just burnt the image. I keep my finger crossed :)

---

### Post by seeker5528 on 2009-12-21
> **holepunch said:**
> I got a 1TB drive which when mounted in System Rescue couldn't be written to because it was formatted as NTFS so I plugged it in to another machine and reformatted at FAT32.

If you use NTFS-3g to mount the partition, you should not have problems writing to an NTFS partition.

The text you see when you boot System Rescue CD should show an example, something like:

```
ntfs-3g /dev/sdXX /mnt/windows
```

Later, Seeker

---

### Post by eltama on 2009-12-21
I am recovering my data!

I am using GetDataBack from Hiren's cd. Note that the program is not on the command line version (kind of DOS) but on the graphical version (a Windows XP livecd).

It's taking really long, but I am happy anyway. It took more that 2 hours to rebuild the tree structure and I've been copying files for several hours now.
I haven't been able to check the integrity of most of the files, but they look fine.

Now you know what to try, I hope you can get your files too. The only problem with this method is that GetDataBack and many of the tools included in Hiren's cd are cracked (they assume that you have a valid licence). I am considering buying the program just to support it.

---

### Post by rlvarcoe on 2009-12-21
somewhere in my old windows brain I recall doing something similiar and had to restore the MBR but sorry I can't give futher details...

---

### Post by stinger30au on 2009-12-21
u want one of these
[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

and one of these
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

piece of cake

u should also be able to boot from ubuntu live cd with external hadd plugged in and backup data to it from internal hdd so long as u aint wiped the data on internal hdd

---

### Post by Grenage on 2009-12-22
> I am considering buying the program just to support it

The software will ultimately be a lot cheaper than making it up to your other half. ;)

---

### Post by iponeverything on 2009-12-22
I have to say that I cringed when read original post.

I double, triple and even quadruple check when running mkfs.. But I find that when I am in the middle of trying to solve a problem, and I have spent several hours on it, I make mistakes. Luckily -- I have not gotten burned yet..

The other week I was trying to fix a database issue and I kept having to run the same command, so I was just using the up arrow to find it in my history. After about the 20th time of running the command, I accidentally ran it form the wrong directory. I dodged a bullet because the effect from that location was benign. If I had ran from one directory up, it would have been quite bad.

---

### Post by holepunch on 2009-12-22
> **iponeverything said:**
> I have to say that I cringed when read original post.

I did a little more than cringe when I realised what I had done.

Although I was being careful I was rushing and also partly lulled in to a false sense of security because I was using a Live CD.  I know Live CD's can be used for reformatting whole drives but the general message that stuck in my mind was "use a Live CD to do things because then it doesn't touch the contents of your HD".

I suppose it's just one of those things.

---

### Post by audiomick on 2009-12-22
> **holepunch said:**
> ...but the general message that stuck in my mind was "use a Live CD to do things because then it doesn't touch the contents of your HD"...
yeah, unless you tell it to... ;)

---

### Post by holepunch on 2010-01-14
Now the dust has settled I thought I would post a final reply and see if I could mark the thread as solved.

Here's a general summary of what I did:

[LIST]
[*]Borrowed wife's laptop to use the in built card reader and typed one letter wrong with a formatting command that wiped her primary drive.
[*]Went out the next day and bought an extremely large backup drive and an expensive pair of hair straighteners.
[*]Used dd to image her whole drive then recreate it on a test machine (initially I played with single partitions but seeing as I had a test machine decided it was easier to work with).
[*]Experimented with TestDisk but was unable to 'fix' the problem which based on reading is probably something to do with how the process of formatting as ext 3 sets the drive up.
[*]Used PhotoRec to recover all files but got a whole load of useless files as well (DLL's etc) and a lot of the documents were corrupted and I had quite a job sorting through everything.
[*]Used GetDataBack on Hiren's boot CD to recover some useful files. Initially tried using the NTFS version because that's what the drive was originally but it didn't find anything so used the FAT/EXT version.
[*]Did lots of washing up and cup of tea making.
[*]Learnt a lot, fast, about data recovery.
[/LIST]

The place that she works at contract out IT support who said it will cost £130 to rebuild the machine which seems a little steep considering I could stick the install disks in myself.

I think she has forgiven me but she certainly won't be letting me go anywhere near her computer ever again. However, the irony is that I regularly back up all machines that I use and because I was never allowed near it I left back up to her. I have now purchased a large memory stick for her to keep a copy of important files on. 

Ending on a slightly more positive note, her My Documents was synchronised with her work server as part of the log in process so she was able to access them from another machine.  She couldn't find the contents of her Desktop but they were the only files I was actually able to recover intact.  

Apart from the major inconvenience of having no work laptop for a while (and possibly having to foot the bill for a rebuild) I seem to have come through relatively unscathed.

Phew.

---

### Post by nothingspecial on 2010-01-14
Ouch!!

I constantly tell my wife to back up her data, to which she shrugs and says "yeah, yeah"

I do it anyway.

The thing is, if you are the family "IT person", it`s going to be your fault if anything goes wrong.

Infact, I have a "wife looses all data from her laptop plan".

I have an old netbook, which we use as a tv. It`s a bit past it`s best but it works. Connected to it is an external drive, to which I back up my wife`s college work, photos and music. If anything ever happens to her laptop, I can copy this stuff across and give her a working computer while I sort out her normal one.

****To all you kids on here - if you have grown up believing you will be "the man of the house" - forget it****

(when my oldest son was just 3 years old he said to me -

Daddy, you`re in charge of cds aren`t you?

I said "Yes"

Then he said

"And Mummy is in charge of everything else"

Wise before his years)

---

### Post by audiomick on 2010-01-14
hey, great to hear your still alive!
glad you got things more or less painlessly sorted out. Would be nice if the wife took it as an omen to back up instead of to forbid you from touching her machine...;)

---

### Post by holepunch on 2010-01-14
Thanks for all the support.

I've toyed with the idea of trying to set up some sort of flow chart type guide (e.g. if this has happened, try this else move on to this step etc.) just to point people in the right direction.

I found various useful guides for specific processes (i.e. how to use PhotoRec or how to restore partitions using TestDisk) but it took a lot of reading and experimenting to establish what part they could each play.

However I speculate that it's a bit of a minefield with no way of pinning down a procedure to follow should you experience data loss?

---

### Post by audiomick on 2010-01-14
I think your right. In the situation you were in, I think there is a lot of pot luck involved.;)

---

### Post by lisati on 2010-01-14
> **audiomick said:**
> hey, great to hear you**'**r**e** still alive!
glad you got things more or less painlessly sorted out. Would be nice if the wife took it as an omen to back up instead of to forbid you from touching her machine...;)

+1
Mrs Lisati & I appreciate some of the challenges!

---

### Post by Leppie on 2010-01-14
> **audiomick said:**
> hey, great to hear your still alive!
glad you got things more or less painlessly sorted out. Would be nice if the wife took it as an omen to back up instead of to forbid you from touching her machine...;)
i actually agree with audiomick, with a good backup system restoring without much loss can be achieved in very little time. it's usually fear of what might happen and overprotectiveness that make these "mishaps" a big problem.

---

### Post by holepunch on 2010-01-14
I have to say I agree about the whole backing up as opposed to being over protective.

I keep trying to tell her hard drives fail, laptops get dropped, cups of tea get spilt...

I'm always installing various distros, breaking them, reinstalling them, having hard drives fail or trying different machines. Thus I tend to keep important data backed up and separate because I see data loss as inevitable instead of something I can avoid by wrapping my machine up in cotton wool.

---

### Post by Leppie on 2010-01-14
> **holepunch said:**
> However I speculate that it's a bit of a minefield with no way of pinning down a procedure to follow should you experience data loss?
data loss normally doesn't involve changing the filesystem :P
deleted files can usually be restored quite easily in ntfs and even restoring a deleted partition isn't too difficult if no other modifications have been made.
i haven't played around with testdisk much yet, but it should be able to restore or change the partition table of a filesystem.

---

### Post by holepunch on 2010-01-14
> **Leppie said:**
> 
i haven't played around with testdisk much yet, but it should be able to restore or change the partition table of a filesystem.

TestDisk was able to change the partition table of the filesystem back to NTFS but unfortunately the process of formatting as EXT3 doesn't mix well with an existing NTFS partition.

I can't remember specific technical details but from my research it goes something like this:

NTFS keeps a phone book record of what is stored where in the MFT and it has a backup copy at the end of the drive.  TestDisk can do some form of restoration magic if it finds a corrupted MFT because it can cross reference with an un-corrupted MFT back up at the end of the drive.

Formatting as EXT3 pops copies of it's phone book at various points along the drive so that access is quicker or something because the disk heads don't have to travel as far.

In my case, I reckon formatting as EXT3 partially wrote over the backup NTFS phone book because TestDisk found the original and backup but said they were both corrupted.

Please don't take that Noddy guide to the EXT3 file system as 100% accurate because I'm not an expert but if there is someone reading this that can confirm what I have written or correct me I'd appreciate it.

---

### Post by audiomick on 2010-01-14
> **holepunch said:**
>  because I see data loss as inevitable instead of something I can avoid by wrapping my machine up in cotton wool.

so do I. All one can do is postpone the inevitable indefinitely (or as long as possible). You can't trust machines. They break.;)

---

### Post by chillicampari on 2010-01-14
> **audiomick said:**
> hey, great to hear your still alive!
glad you got things more or less painlessly sorted out. Would be nice if the wife took it as an omen to back up instead of to forbid you from touching her machine...;)

Backing up more just in case my spouse got some urge to start breaking my machine would probably work on me as an incentive. :P

---

