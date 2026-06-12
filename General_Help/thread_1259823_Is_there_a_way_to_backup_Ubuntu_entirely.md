---
title: "Is there a way to backup Ubuntu entirely?"
date: 2009-09-06
forum: General Help
---

### Post by knowndarkness on 2009-09-06
:confused: Hi i'm kind of confused... after reading about backups and restoring Ubuntu as images and whatnot. I was looking at things like hubackup, sbackup, partimage, and things like that.

I don't want to make this very confusing so i'll get to my point:

What I am wondering: 
Is it at all possible to backup Ubuntu's entirety? I recently installed the full version of Ubuntu Desktop Version 9.04 Jaunty on my netbook/laptop. Not even a week passed and i was already tweaking away at Ubuntu. During one of my common failed 'tweaks', it completely messed my laptop up. The only thing that i could do was to reinstall Ubuntu. And that meant having to reinstall ALL the software, updates, and EVERYTHING over again. It is extremely tedious and exhausting to do this - twice. 

Excuse me if i say this incorrectly (i'm still very unfamiliar with linux), is there a GUI program that can back up my ubuntu's settings? Let's say i screw up my ubuntu, and it won't even get to booting. I would then want to reinstall Ubuntu using my Live CD. Then, through the newly installed Ubuntu, i could 'restore' the old settings through this program... and all the programs, files, settings i downloaded/installed would still be on there. 

I have taken a slight interest in the fact that i can "make a clone of my partition"? **I prefer copying the partition over just 'backing up settings'**.  So that i can make a HARD COPY of EVERYTHING that is my laptop. If something went wrong, i could just replace the partition

* I'd like to be able to backup to my external hard drive. My partition on my laptop is ~160 GB. My ext hard drive is 500 GB.

I don't want to keep messing up my laptop. Could someone give me some tips or how-to's that would lead me in the right direction? 

Thanks!

---

### Post by scouser73 on 2009-09-06
Hi, there is a program that I use called [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html"), it's a GUI that is extremely easy to use.

I back my **/home** up on a weekly basis incase of any mess ups on my part.  [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html") allows the user to restore **any files that you wish** incase of any foul ups that may occur, you can backup to a local drive, CD/DVD or Remote Host (SSH).

I'm positive that it will suit your needs for backing up.

---

### Post by winotree on 2009-09-06
I recently used *remastersys* [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html) to clone my minimal, tweaked installation of Xubuntu.  Honestly, it's more xfce than Ubuntu!  :D  Once I got everything just the way I wanted it I made an iso  which I then burned to disk and now have *an exact image in time* of my device and its system.  It also offers an option to burn incremental changes back to that iso *or* you could make copies for friends -- minus your personal information.  It'll do that, too.  Why not take a look, or try it before this long weekend's over.  ;)

EDIT - Hey! That PyBackup **does** have a great GUI!  Good choice!

---

### Post by knowndarkness on 2009-09-06
[SIZE=1]> **scouser73 said:**
> Hi, there is a program that I use called [[COLOR=Red]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html"), it's a GUI that is extremely easy to use.

I back my **/home** up on a weekly basis incase of any mess ups on my part.  [[COLOR=Red]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html")**any files that you wish** incase of any foul ups that may occur, you can backup to a local drive, CD/DVD or Remote Host (SSH).

I'm positive that it will suit your needs for backing up.
[/SIZE]
If my laptop suddenly wouldn't boot. Could i reinstall using the Live CD, and then just install that program and restore using the program? Would i have all my programs, settings, etc back?[SIZE=1]
[/SIZE]

---

### Post by knowndarkness on 2009-09-06
> **winotree said:**
> I recently used *remastersys* [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html) to clone my minimal, tweaked installation of Xubuntu.  Honestly, it's more xfce than Ubuntu!  :D  Once I got everything just the way I wanted it I made an iso  which I then burned to disk and now have *an exact image in time* of my device and its system.  It also offers an option to burn incremental changes back to that iso *or* you could make copies for friends -- minus your personal information.  It'll do that, too.  Why not take a look, or try it before this long weekend's over.  ;)


I heard about this one, but i didn't know how to use it. Maybe i'll look into it again. I'm not entirely certain of what it does or how it works :(

---

### Post by scouser73 on 2009-09-06
> **knowndarkness said:**
> [SIZE=1]
[/SIZE]
If my laptop suddenly wouldn't boot. Could i reinstall using the Live CD, and then just install that program and restore using the program? Would i have all my programs, settings, etc back?[SIZE=1]
[/SIZE]

Yes, that wouldn't be a problem as the files that you backed up could be transferred if you had to do a reinstallation again.

---

### Post by scouser73 on 2009-09-06
> **knowndarkness said:**
> I heard about this one, but i didn't know how to use it. Maybe i'll look into it again. I'm not entirely certain of what it does or how it works :(

The link that I posted shows you how to use it and successfully backup your files, If you need any further help please ask.

---

### Post by winotree on 2009-09-06
Reference your post # 5

I wasn't either until I tried it!  It's not the same as, but you could think of it as a reverse iso, but that may only confuse you and I don't want to do that!  Once I made my image I deliberately took something vital out of my distribution -- of course it didn't work.  Pop!  In goes the image and in about ten minutes, maybe a bit more, it was restored.  :)  I also use *Grsync* to back-up my user file daily.  I don't have much but it feels good to know I can recover it, if necessary.

---

### Post by knowndarkness on 2009-09-06
> **scouser73 said:**
> The link that I posted shows you how to use it and successfully backup your files, If you need any further help please ask.

I installed remastersys. Which option would i select if i want to make a copy of my entire system, and then be able to put it on my external hard drive... where i could boot it from there as Live?

If this doesn't work, i'll give pybackpack a try.

Thanks for the advice you guys :)

---

### Post by rmcellig on 2009-09-07
Can I clone my Ubuntu drive using Pybackpack? If so, are there instructions somewhere that I can look at? I am trying to find the easiest way for me to clone my drive.

---

### Post by louieb on 2009-09-07
Tried and true [Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522")

All or nothing backup and restore. old style n-cursors interface. It just works - would not think about making a major change to my system (like the upcoming upgrade to v9.10 ) without using it 1st. 

And thanks **scouser73 **for the pybackpack link - looks like something I should try out.

---

### Post by winotree on 2009-09-07
> **knowndarkness said:**
> I installed remastersys. Which option would i select if i want to make a copy of my entire system, and then be able to put it on my external hard drive... where i could boot it from there as Live?

If this doesn't work, i'll give pybackpack a try.

Thanks for the advice you guys :)
Open *remastersys, *open the backup option **not** the grub option, open and use the backup or first option.  I stored my backup image on a CD-DVD as this is the only computer I have and disk space is at a premium.  :? 

EDIT - I can't speak about other means of storing the backup -- this should work, if not something else will...   Hoping you find a process that works for you regardless of which one it is!  ;)

---

### Post by t_virus on 2009-09-07
there is a nice backup app in jaunt's repos:
sbackup  -> apt-get install sbackup

this app has a nice gui easy to use and can backup all dirs you want and u can even schdulle the task.

try it, maybe souts for u.

---

### Post by rahulthewall3000 on 2009-09-07
Might I suggest fsarchiver - just back up the entire partition and then "extract" it to your new partition.

I used it to backup my Gentoo and XP installation - so it would work with an Ubuntu partition as well.

Read about it at: [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by winotree on 2009-09-07
Say, **rahulthewall3000**, that looks interesting.  I've found something I like, and am willing to recommend to others, but not necessarily something I'll live with and not have to worry about.  I'll have to look into it a bit more.  Thanks for the link, too!  ;)

---

### Post by ankspo71 on 2009-09-07
I am using a live CD called Clonezilla to back up my Ubuntu. It can can create a backup of an entire drive and place it on another drive as an image file. If it will detect your external drive, then this might be something you could use. I use my second (internal) hard drive as file storage and it doesn't interfere with the stored files already on there so I really like it. At a first glance, it appears to look tricky to use but it's not that bad after the first time. It has a few back up options, but I have only tried backing up the entire drive as an image. 

If Ubuntu fails to boot, I just boot from the Clonzilla CD and use it to restore Ubuntu. The restore process takes me about 10 minutes with a not so quick computer. The image size it created for me is 1.1gb in size, which is the entire Ubuntu 9.04 installation with all the current updates. Hope this helps.

---

### Post by knowndarkness on 2009-09-07
Now i remember why i gave up on remastersys. I used it, or at least tried, using it on my laptop. When i used the backup option, i waited like two hours. After it finished it said that i didn't have enough storage space, and i don't know what to do with that.

Could someone explain how PartImage works please?
I'm trying to install it on my laptop. So far i've got as far as downloading the "partimage-0.6.7.tar.bz2" file. Then in Terminal, i typed in "cd Desktop". Then "tar xfjp partimage-0.6.7.tar.bz2" So far so good.

Now i am confused about what i am suppose to do with this code 
"./configure --prefix=/usr && make && make install"

---

### Post by louieb on 2009-09-08
> **knowndarkness said:**
> Could someone explain how PartImage works please?
Not to reinvent the wheel  did you check the link in post #11? 

Partimage will not backup a partition that is mounted, the only partition that needs to be mounted is the one you are writing the backup to.  -  Best to run it from a live CD. Two good live CDs are  [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") and  [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

---

### Post by ken78724 on 2009-10-02
Reference to "entirety" in Posts 1, 2, 3:
1st I've install Ubuntu Studio w/9.04 Jaunty; I do not see hubackup listed System > Administration > [hubackup] but want to create both an OS backup and an all files backup. Am not yet set to do external backups. 

My Qs are, where do you download the py.... for files backup? & 2) if I use the mas,,, alternative can I use the option w/o an external or networked storage?

am often not able to get back promptly so pls don't be cryptic if  intricracies are involved. Apologies up front; involved since late 50s, I've gotten crusty as the dickens; now am easily challenged. 

wow, I just read posts 10-18 which I did not read 1st pass thru. some of my ? is answered there.
thanx ken

---

### Post by SoylentSteak on 2009-10-02
Does Pybackpack back up configurations?

If I have to do a reinstall, this is always the major pain. I've had to do it before, and there are easily a dozen things I need to change around before I get everything working properly. Will it also keep me from having to remove things and install others, provided I have it configured that way in the backup?

Example: Will it automatically install TuxGuitar, then install Timidity, and configure it (Timidity) to begin on startup, and load all my other TuxGuitar settings?

---

### Post by ken78724 on 2009-10-10
This thread [two in one] provides most valuable insights 4 backing up Ubuntu, including our OSs and fine tuning private installations. I believe it would merit being made a sticky all can use as needed. If done,I feel a step by step presentation, letting one view Qs and As for achieving solutions in an orderly, sequential manner. I missed powerful points by not reading beyond post # 11, then not connecting points made earlier with remedies mentioned later. tho am a retired military research scientist, I remain challenged when Qs are answered "later".

So, can't a summary sticky be posted in lieu of the longer string ?

---

### Post by rmcellig on 2009-10-10
ken78724,

I fully agree with your post. A step by step for beginners with no terminal or programming background would I think be essential to anyone entering the world of Ubuntu. Even step by step videos would be a great asset.

---

### Post by alexandermdevereux on 2009-10-10
you can use clonezilla. It backs up everything and will reinstall grub for you. Clonezilla is a live cd with a gui much like the text base installer for ubuntu. It can also copy a drive.

Clonezilla works with:
Images
Partitions
Drives
MBR
Hidden Data
Any partition type

---

### Post by rmcellig on 2009-10-10
I did a disk to disk clone backup using Clonezilla. Now when I try to open the Cloned drive, it says that I lack the permissions to do this. Is this because the cloned drive was saved as root? What do I have to do to see the drive on the desktop?

---

### Post by SoylentSteak on 2009-10-10
> **SoylentSteak said:**
> Does Pybackpack back up configurations?

If I have to do a reinstall, this is always the major pain. I've had to do it before, and there are easily a dozen things I need to change around before I get everything working properly. Will it also keep me from having to remove things and install others, provided I have it configured that way in the backup?

Example: Will it automatically install TuxGuitar, then install Timidity, and configure it (Timidity) to begin on startup, and load all my other TuxGuitar settings?

An answer to this would be much appreciated, as it's not long before I upgrade to Karmic. :cool:

---

### Post by caue.rego on 2009-11-04
> **SoylentSteak said:**
> An answer to this would be much appreciated, as it's not long before I upgrade to Karmic. :cool:

I haven't tried pybackpack, but if it just backs up your home directory to a DVD, then no, it won't be a complete Ubuntu backup at all.

For a complete backup, both focusing an upgrade and for the topic starter, I highly advise to use either **partimage** or **clonezilla**. It's a bit troublesome, but the only completely safe options I could find so far. There's a topic I started after coming here:

[http://ubuntuforums.org/showthread.php?p=8241150#post8241150](http://ubuntuforums.org/showthread.php?p=8241150#post8241150)

---

### Post by rmcellig on 2009-11-04
I now use Clonezilla from the Parted Magic Live CD, but for the average user, I don't think there is anything for Ubuntu that actually works seamlessly. I have Time Machine working on my Mac fine. Set it and forget it. If Ubuntu really wants to make inroads in the mainstream arena, it has to be for the most part idiot proof.

Now if I can just have a fster PC to run 9.10 (which I really like so far). :)

---

