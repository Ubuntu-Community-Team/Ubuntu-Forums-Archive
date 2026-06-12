---
title: "Several Ubuntu questions - I'm ready to learn!"
date: 2006-06-01
forum: General Help
---

### Post by badrad on 2006-06-01
I've finally decided to install linux, give it some serious attention and learn my way around. I know Ubuntu is supposed to be a great distro, and have no doubt that it's what I want to try. I have a couple of questions though.

Quick background: I've been using computers all my life and know my way intimately around Windows systems. I know how they work, know how to fix them, and am comfortable doing anything with them. I'm the guy everyone comes to for help. What I know about Linux comes from the things I read that show up on sites like Slashdot/Digg, and from the few Live CDs I have tinkered with.

Anyway, onto my questions. I know with the new release the forums will probably get a lot of new posts, hopefully someone can answer me:

1. Ubuntu or Kubuntu? I know that Ubuntu uses Gnome and Kubuntu uses KDE, but don't know which one to pick. I have heard lots of people say they like KDE better, but the Ubuntu people obviously chose Gnome as the default environment. What considerations should go into this choice? What recommendations to people have? One thought I have is that I listen to a lot of music and I heard that amarok is the best music program on linux, but isn't it made for KDE? Or are their packages to get it to work in Gnome?

My other questions may also influence this decision.

2. x86 or 64-bit? I have a dual core 64bit AMD processor. Which should I use? Are there significant application compatibility problems in the 64-bit build? Can 32-bit programs work in it? Are there speed increases that make it worthwhile or is not worth the headache? Do either take advantage of both cores?

3. Xgl! Xgl is sexy. Super sexy. I must have it. I see the stickied thread at the top that surely will help me set it up, but have these questions. Is it decently stable? Will it effect my choices of x86 vs 64-bit? Does it work with both gnome and KDE? Anything else I should know?

4. NTFS access. As far as I have been lead to believe Ubuntu can read, but not write, to NTFS drives. Is there a way to get it to write? I have 5 NTFS drives and many NTFS drives on the network. Can Ubuntu be configured to write to NTFS? Is it stable?

5. For that matter, filesystem? I'll give Ubuntu its own hardrive - I'm assuming it has a favorite filesystem. What is it? If its not Fat32 then windows probably wont be able to read from it correct? I am not looking forward to my OSes not being able to access each other.

6. Well, not really a question, and probably the hardest to answer. Basically, I know nothing about Linux. In Windows I know the filestructure very well. I know where I can find any file, why it is there and what it will do. I know the filetypes really well. I know how everything boots and how drivers and devices are managed. In Linux, I'll be clueless. Why is the filestructure the way it is? Are all executables still .exe? How are drivers installed? How, and under what circumstances, do I compile my own program? I am good with computers and know I will be able to figure it all out, but the MAIN thing that previously has kept me away from learning Linux is that I wasn't looking forward to learning the new way, but I know it is a necessity. I am not necessarily asking you these questions, but are there any good resources online for learning linux/(k)ubutnu/gnome/kde?

Thank you for any help at all and taking the time to look at my questions. I look forward to learning and using Linux and Ubuntu. It's truly amazing what the community has accomplished, and I look forward to being a part of it.

---

### Post by eqisow on 2006-06-01
Welcome aboard! I will answer your questions as best i can.

1) I recomend starting with Gnome. It is simpler overall and will be the best choice while you are learning, imo. KDE tends to ahve more options and is more customizable and is therefore also more complicated. Learn Ubuntu first, then learn KDE if you want.

2) x86, definitely. There are several things that don't work in 64 bit that will bother you to no end. You can set up a chroot to solve this, but that's not something you want to tackle as a beginner.

3) While I ahve had decent luck with XGL, it is extremely alpha atm. So be warned! It works best on Gnome, but can be made to run on KDE as well. My opinion? Stay away until it becomes more stable or until you are more comfortable with your system. Besides, there's a good chance it will be default on the next release in just four months.

4) NTFS write support is beta, and can muck up your filesystems. I don't recomend it. Your other option is to reformat some of those NTFS partitions as Fat32.

5) Ubuntu's default is ext3. There are otehr options such as ReiserFS and XFS. For home use, there's not that big a difference between them. Stick witht he default.

6) This would take a very long response, which I'm afraid I don't ahve time for just now. I recomend trying to Google for some Windows/Linux beginner's guides or for some Ubuntu beginner's guides. There are plenty! You could start [here]("http://www.unix-tutorials.com/go.php?id=518") for some basic stuff. The [Ubuntu Wiki]("http://wiki.ubuntu.com/") is also an awesome resource.

---

### Post by grendelkhan on 2006-06-01
Whew.. okay, these are all really subective questions, but I'll take a shot:

1) This gets down to a preference between GNOME and KDE apps, asthetically, I like how GNOME stuff looks better than KDE, but that's me.  Also, for right now, Compiz (the window manager Novell created to go with Xgl) works better with GNOME, but it can work well with KDE.  Food for thought.

2) I'm in the same boat as you and here's what convinced me to stay 32 bit - the web.  Proprietary plugins like Real and Flash don't exist in a 64 bit version, and installing a 32 bit environment for them to run under was too big of a PITA for me to do.  I went 32 bits and I don't feel bad about doing it.

3) Xgl is just the pallete Compiz paints on and Compiz is BEYOND sexy.  Windows users drool when I start changing desktops or throwing windows around.  And, there's a nifty script called nonXgl (search for it here in the forums) that will let you run 3D games under Xgl through a nifty hack.  Word to the wise, Xgl is happier with Nvidia cards than ATI cards, though it should be said that Nvidia's driver history for linux is better than ATI's, but there are plenty of threads in this forum that can walk you through setting them up.

4) NTFS access is dicey.  Linux can write to NTFS drives, but it's not a 100% accurate endeavor.  Sometimes things go wrong and you can bork your drives.  There are utilities that can help you recover, but generally folks avoid it.

5) EXT3 is good enough for most people.  I run XFS on filesystems I share out with Samba because it supports Windows ACL's on the files.  For everyday uses EXT3 is plenty good.

6) Wow, this is a tough one.  From personal experience, I bought an "Understanding Linux" book and went cold turkey - formatted my drives and forced myself to learn how to do things the Unix/Linux way.  I was then lucky enough to luck into a Unix position at my job and had some great admins take me under their wing.  I think you will find these forums to be VERY forgiving and understanding for newbies, the Ubuntu community is much more welcoming and warm than some of the others I've seen.

Most of us put our IM and email info on here too, so don't hesitate to reach out.

---

### Post by ketsugi on 2006-06-01
Regarding NTFS partitions on the network, don't worry about those. You'll be mounting those either via NFS or SMBFS anyway; network shares are pretty much filesystem-agnostic.

---

### Post by badrad on 2006-06-01
Wow, three quick and thoughtful answers. I can't thank you enough.

1, 2, 3. Well, I'll definitely go with 32bit gnome to start. Sounds like the best place. I can always branch out and play with KDE later, or 64bit if I want to torture myself. Thanks a lot for the advice. As far as compiz, once I am decently comfortable in Ubuntu I'll give it a shot.

4, 5. Thanks for the warning about NTFS writing. Is NTFS reading supported well? I assume it would be safe as well. I'll stick with the default EXT3 for Ubuntu. What do most people do, have a separate Fat32 partition for passing information between Windows and Ubuntu? Not looking forward to that, but it's unavoidable and is no ones fault. Also good to know about NTFS over the network. Come to think about it, that's obvious, I'm not actually accessing the filesystem :)

6. Thanks for the advice.

I have work and school breathing down my neck this weekend, but I'll probably start diving in any day now! I'm excited.

---

### Post by grendelkhan on 2006-06-01
mounting local ntfs drives, you can insert an option in /etc/fstab (where all the drives are listed and described and their mount points determined) to make them read only, to keep you safe from yourself.  When I was dual booting, that's what I did and I had no issues.

---

### Post by eqisow on 2006-06-01
4/5 NTFS reading is pretty much perfect. Never had or heard of a single problem. And yes, when I still had a Windows partition I used a Fat32 partition for swapping files. It probably doesn't need to be very big. If there are files you want both partitions to have access to then put them on the Linux partition. There are shell extensions for Windows ext3 support.

Again, welcome to the community and good luck in your new adventure! And remember, never hesitate to ask a question. That's what we're here for!

---

### Post by badrad on 2006-06-01
Wow - I didn't know Windows could read ext3. I searched Google and found several different extensions - do you have one you would recommend (XP SP2)?

I have no option but dual booting - I use several professional applications for work that I must have, and I'm a huge gamer.

Here is a sort of related question, is there a safe way to re-size my existing drives? If I have a drive that is formatted with one large NTFS partition, is their a nondestructive way to create a new ext3 partition in the empty space?

---

### Post by eqisow on 2006-06-01
Aa far as reading ext3, I recomend one that is a shell extension and actually integrates into windows explorer instead of a standalone program. Other than that, I don't really have a preference.

About resizing NTFS partitions, the first thing your going to want to do is defrag it. This will move data to the beginning of the partition. After that, there are a few options. One is using Partition Magic for Windows. It cost money though, and I'm not sure I'm allowed to advocate BitTorrent here. *cough* However, that is actually not the best solution, imo. I recomend using a Linux live CD such as Knoppix to run QtParted (or GParted). The new Dapper live CD may also contain GParted, but I don't know for sure.

---

### Post by badrad on 2006-06-01
Cool, I'll defrag tonight. Been meaning to do that.

One more question :)

I know that if you have two partitions, one with windows, one with linux, you can use a boot manager to get a gui to upon boot to pick your OS. My question is if there is a way to do that with each OS actually being on a different drive? My main drive is an uberfast drive but is only 70 gigs - not enough room for two OSes really.

I'll definitely check out GParted, thanks for the advice.

---

### Post by eqisow on 2006-06-01
GRUB (the boot loader) should automatically detect all your OSes on all your drives and configue itself automatically at the end of your Dapper install.

Note: Linux should always be the last OS you install. If you install Linux then Windows, Windows will bork the boot loader. It's fixable, but it's a pain.

---

### Post by blakamin on 2006-06-01
[QUOTE=badrad] My question is if there is a way to do that with each OS actually being on a different drive? My main drive is an uberfast drive but is only 70 gigs - not enough room for two OSes really.
[/QUOTE]

70gig for 2 OS's???

I had 3-4 on a 30gig laptop drive!!! (XP, Auditor, Breezy and dreamlinux)

now I just have Dapper and Auditor

It shouldn't be a problem to boot from another drive if GRUB is installed in your MBR of the main drive (I think)

---

### Post by mattkenn4545 on 2006-06-01
Just a quick drop in.

The Xgl/Compiz sexyness is off the wall. Just remember to enable the quinn repositories and install. compiz-gnome xgl and the package to change the settings for compiz (much better gconf) 

Also disable the dock plugin as it is currently broken other then that have been running it for ~ 4Months and it is now VERY STABLE and hasn't outright crashed for me yet (using it everyday to boot) 

Also remember the best way learn is to break - fix - break - fix - and re-rinse as needed

---

### Post by badrad on 2006-06-01
[QUOTE=mattkenn4545]Also remember the best way learn is to break - fix - break - fix - and re-rinse as needed[/QUOTE]

You know, your right. That's how I've learned as much as I know about computers. I guess the reason I've been so apprehensive about learning a whole new system is that I am not a kid with nothing but freetime anymore.

I've downloaded the GParted Live CD - as soon as I am done with today's school work I'll reboot to defrag and get started on my first Ubuntu set up. That's for the advice everyone - I'll probably be back with more questions :)

---

### Post by thasheep on 2006-06-01
Sorry, by the time I get to the second page, I've forgotten which question had which number but I'll try to say what hasn't been said yet.
ntfs read/write support DOES work reliably under linux but to do so (with the write bit anyway), you need to use a little tool called "captive" that acts as a wrapper for the real windows driver. There are problems with distributing with with the distro because it uses windows stuff but if you already have windows (and a license) then as far as I know, there's nothing wrong.You could follow the (old) guide [here to install it](http://www.ubuntuforums.org/showthread.php?t=10175) but it's slightly outdated so to save you the effort, I've changed it a little bit below.
[list=1]
[*] First download the rpm package from [http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)
[*] Install kernel-headers for your kernel revision
[list][*]sudo apt-get install linux-headers-$(uname -r)[/list]
[*] use alien to convert rpm to deb package then install it
[list][*]sudo alien captive-static-1.1.7-0.i386.rpm
[*] sudo dpkg -i captive-static_1.1.5_1.i386.deb[/list]
[list][*]Set up captive using the gui to find ntfs.sys and other needed files.
[*] sudo captive-install-acquire
[/list]
[*] create user and group named captive
[list][*]sudo groupadd captive
[*]sudo useradd -g captive captive[/list]
[*] use '*mount -t captive-ntfs /dev/hd?? /mnt/winpart*' to mount. Change options to enable write etc....[/list]
I have the following line in /etc/fstab. I've set it so that it needs to be mounted (with sudo/root) manually and can only be written to with sudo/root. Change the device and mountpoint as desired and have a look into the umask, uid and guid options if you want to have user write-access.
```
/dev/sda1   /mnt/win   captive-ntfs    defaults,noauto 0 0
```

As for the questions about the file structure under linux, it's goes by the posix (unix) standards. This probably doesn't mean much to you unless you've used linux or macos X or feel like a bit of googling. There's no such thing as .exe files but permissions for every file (including executables) are decided per user/group. The three basic permissions are read, write and execute. Now for the filestructure...... Firstly, drives go someplace within the filestructure, like any other directory (folder in windows talk), they don't get drive letter. Secondly, a forward (like on the internet) rather than backward slash is used between directories.
/ is the beginning or 'root' (don't confuse with 'root' user)
/bin (binary) contains executables that are basic system stuff that anyone can use, such as ls (equivalent to dos 'dir')
/boot contains basic boot stuff including the kernel and some bootloader files 
/dev (devices) contains files that 'talk' to all devices (keyboard, mice, screen, disks, .....)
/etc contains mostly system setting files (plays the role of the registry and more but is much easier to deal with)
/home contains user directories (like 'documents and setttings')
/lib (library) basic system libraries (stuff programmes need to run)
/media where removable drives should be mounted
/mnt where other permanent drives should be mounted
/opt often unused but where programmes that don't really fit in the distro should go
/proc contains lots of information about the system
/root the home directory of root (the 'superuser'), who has the power to change (and ruin) everything
/sbin basic system executables that should only be run as root
/sys kernel (system) stuff - some low level stuff can be changed here if you really know what you're doing
/tmp temporary directory that anyone can write to
/usr another directory that contains all the stuff that isn't really system stuff
/usr/bin normal executables
/usr/include files used for compiling stuff
/usr/lib normal libraries
/usr/sbin normal root-only executables
/usr/share data and config for programmes
/usr/local where you should install stuff you compile yourself (not part of distro)
/usr/src where source can be compiles
/var contains logs, cache, running info

edit: one more thing - linux is case sensitive

---

### Post by B0rsuk on 2006-06-01
As for Gnome vs KDE, i prefer KDE. It's not as complex as some people would like you to believe. In my opinion it's easier/more consistent than windows interface. Certainly easier to configure than Gnome.

Some tips...

if you use commandline, **man command** will print you manual about that command.

Good wikipedia articles (don't try to memorize entire articles now; good thing about wikipedia is that it gives lots of examples, unlike linux man pages)

[http://en.wikipedia.org/wiki/File_system_permissions](http://en.wikipedia.org/wiki/File_system_permissions)

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
(fairly exhaustive directory descriptions, more than you'll need to know in a while.)

[http://en.wikipedia.org/wiki/Superuser](http://en.wikipedia.org/wiki/Superuser)
(root account is hidden in Ubuntu, but most things that apply to root apply to sudo, too. Avoid using root/sudo unless necessary)

Everything in linux is a file, even directories. There little restrictions on file names; for example you can have files named 'badger', 'ba.dger', '.badger', or 'ba.d.g.er'
There's no such thing as file extension.

/home/yourusername is where you should keep most of your data. Windows keeps one directory for system, linux keeps one directory for users.
Aside from obvious reasons like 'don't mess with what you don't understand' or 'keep your filesystem tidy', it has additional benefit that you can reinstall your system and keep data+most configuration. Not that you're going to reinstall very often (unless you actually break something)

-----------------
I don't encourage you to start learning commandline immediately, but once you get used to it it's both faster and often more convenient. Not to mention advantages you can get with scripting.

---

### Post by tht00 on 2006-06-01
[QUOTE=badrad]6. Well, not really a question, and probably the hardest to answer. Basically, I know nothing about Linux. In Windows I know the filestructure very well. I know where I can find any file, why it is there and what it will do. I know the filetypes really well. I know how everything boots and how drivers and devices are managed. In Linux, I'll be clueless. Why is the filestructure the way it is? Are all executables still .exe? How are drivers installed? How, and under what circumstances, do I compile my own program? I am good with computers and know I will be able to figure it all out, but the MAIN thing that previously has kept me away from learning Linux is that I wasn't looking forward to learning the new way, but I know it is a necessity. I am not necessarily asking you these questions, but are there any good resources online for learning linux/(k)ubutnu/gnome/kde?[/QUOTE]

With question 6 being least answered, I'll give it a whirl. I am a decently recent Linux convert -- not quite a year, FYI.

The filesystem is mounted to / .  Similar to C:, except in a *nix environment, *everything* exists under /.  This took a little while for me to grasp.  Rather than having different letters to identify drives, the drives are mounted to a folder somewhere.  Usually at /media.  One of my other partitions is at /media/hdb2.

Other things about the filesystem...
/bin appears to have some system binaries.

/dev stores stuff about devices attached to the computer -- typically hard drives and such.  Devices need to be mounted before used.

/etc is where most system configuration files are stored.  You shouldn't have to dig around here too much.

/home is like the Documents and Settings folder in a Windows setup.

/media, as mentioned before, is where stuff is often mounted (at least in Ubuntu).  /mnt is another place to mount stuff.

/usr stores a lot of programs that are installed.  You don't need to venture in here much either, as apps are accessible from the command line and GUI apps are often added to the menu automatically.


Executables often don't have a .exe (I've only seen that on a number of occasions).  Sometimes they'll have .run or .sh after them, but that isn't a requirement either.  They can be binaries (compiled programs), or they can be scripts, however, to be able to be executed, they have to have permissions to be able to be 'executed'.  This is where the ext3/similar filesystem comes in.  There are extra properties that can be applied to files -- who owns it, who can read/write/execute, etc.  Kinda how files can have a 'hidden' or 'read-only' attribute in Windows.

In any case, programs (if installed globally to the system) can be started by going to the terminal and typing the command (and any parameters). 
```
firefox &
```
That will open firefox as a process and give you back control of the terminal.  If you don't include the "&", the terminal will wait till that process is complete and then return control of the terminal back.

Programs that are in a folder that you want to get to, you can run in the terminal by accessing that folder and using ./program_name to run it.

Remember, that with Linux/related, the terminal can be one of your most useful tools (unlikes some other OSes).  BASH is the shell of choice most of the time.  It will be a great asset.

Best of luck learning Linux. :)

---

### Post by greggh on 2006-06-01
About the KDE vs. Gnome question... as someone already mentioned I think KDE is more intuitive for someone coming from Windows. I think Gnome would be easier for someone switching from OSX.

---

### Post by nanotube on 2006-06-01
regarding filesystem structure:
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
regarding learning the commandline:
first link in my sig, under "commandline resources" section.
have at it :)

---

### Post by Svanteson on 2006-06-01
To get rid of the 4Gb limitation of FAT32 I recommend using ext3 for the partition that is used for both windows and Ubuntu.
Install this driver in order to read/write to the partition in Windows:
[http://www.fs-driver.org](http://www.fs-driver.org)

I use it myself and it works pretty well. However you don't get the journaling feature when using it from Windows.

BR/Nicklas

---

### Post by badrad on 2006-06-01
Wow, fantastic responses and links, really helping me become familiar with the system. So, to see if I understand the file structure, if I was installing an app I downloaded I would put it in /usr/bin/appname/ and it would store its data in /usr/share. If I was storing stuff like documents and music, I would use my user directory in /home. Does that sound accurate?

I can grasp user permissions easily enough, but I have a question on filetypes / executable files.

[QUOTE=tht00]Executables often don't have a .exe (I've only seen that on a number of occasions).  Sometimes they'll have .run or .sh after them, but that isn't a requirement either.  They can be binaries (compiled programs), or they can be scripts, however, to be able to be executed, they have to have permissions to be able to be 'executed'.  This is where the ext3/similar filesystem comes in.  There are extra properties that can be applied to files -- who owns it, who can read/write/execute, etc.  Kinda how files can have a 'hidden' or 'read-only' attribute in Windows.[/QUOTE]

I'm having trouble understanding this. I can see that for anything to be executable the user must be granted execute permission for that file. But obviously not all files are executable, only binaries and scripts right? If there is no filetype, than how is one to know what files can be execute and what cant? If I look at a folder with 40 files in, how do I know which ones are executable?

[QUOTE=B0rsuk]Everything in linux is a file, even directories. There little restrictions on file names; for example you can have files named 'badger', 'ba.dger', '.badger', or 'ba.d.g.er'
There's no such thing as file extension.[/QUOTE]

I guess I need a little help understanding the lack of a file extension. I understand that the file is still what it is with or without the extension - music.mp3 is still an mp3 file whether is has the extension mp3, txt, or no extension at all. But the file extension is what directs the computer how to use it. With Windows the filetypes are registered - my computer knows to open all MP3 files with winamp, and I can easily change that to another program.

I use OS X at work and I know it works differently. It appears that the associated application can be saved in the files metadata. I can save a TIF file out of photoshop, not put the file extension, and it will open up in photoshop again. Or you can go to file info and force an application for a filetype.

What the hell is my point here. I guess I'll ask the simple question - how does the lack of a file extension work? How does Ubuntu know what program to open the file with? Could I change that association.

Oooh, you guys are getting me excited. I might just screw repartitioning and pop in a new harddrive and play with Ubuntu tonight. Gotta finish my schoolwork first. Thanks again for all the wonderful help and advice.

---

### Post by eqisow on 2006-06-01
I think it was a little innacurate for these fellows to say that Linux doesn't use file extensions. While it is true that file extensions are not necessary for the system to recognize filetypes, they are still often used. You will probably want to keep .mp3 on all of your mp3's, .odt on your OpenOffice documents, .deb on your debian packages, and so on and so forth. The difference is that these file extenions are for your benifit, not the systems. However, it is also true that if you were to add .txt to a picture file, Gnome and KDE would both try to open it as a text file. So while extensions are optional, they also take precedent.

I'm not sure I explained that clearly.. let me know if you're still confused.

P.S. - I'm not sure exactly how recognizing filetypes is done. Perhaps it can analyze the file? Or perhaps there is metadata that tells it? Maybe it's just magic! All I know is that it works. :)

Edit: After a bit of thinking and experimenting, I'm pretty sure it's metadata. Somebody correct me if i'm wrong.

---

### Post by badrad on 2006-06-01
[QUOTE=eqisow]I'm not sure I explained that clearly.. let me know if you're still confused.

P.S. - I'm not sure exactly how recognizing filetypes is done. Perhaps it can analyze the file? Or perhaps there is metadata that tells it? Maybe it's just magic! All I know is that it works. :)[/QUOTE]
I understand it now much better, thanks.

I think various methods for recognizing file types is used. File extensions work, you can analyze the mime type of the file, or I know some OSes can use metadata (i know OS X does). It acts like magic though!

---

### Post by jmacak on 2006-06-01
Hi 

I believe that in unix most files (executable files and the like) have header information that tells the os what to do with the file.  A shell script will have something like "#!/usr/bin/ksh" as the very first line, telling unix to execute this file as a korn shell script.  Binary executables have this too but it's harder to see.

If you have an unknown file that you would like to see what the os thinks that it is, just type "file filename", e.g. "file bumps" returns "bumps: Bourne-Again shell script text executable".

Hope this helps a little.

cheers

joe in seattle

---

### Post by tht00 on 2006-06-01
[QUOTE=greggh]About the KDE vs. Gnome question... as someone already mentioned I think KDE is more intuitive for someone coming from Windows. I think Gnome would be easier for someone switching from OSX.[/QUOTE]

I'm still not sure how one would come to this conclusion.  I find Gnome quite Windows-like, though, I haven't used KDE much to compare to.

Gnome - things that are Windows-like:
Taskbar on the bottom. Menu that launches apps, opens different folders, can get to system configuration, and even has recent documents.  Ability to place shortcuts on panels (like quick launch).  System tray.  Clock.  Desktop that can hold files.

Things that are different:
Customizable by default.  Standard with 2 panels on top and bottom, not 1.  Locations of many things are different.  Multiple desktops.


Really, the only thing that I find is more 'Mac-like' than 'Windows-like' is the upper panel... but it doesn't act anything like Mac's panel.  The rest of the differences are more similar to KDE than Mac.

In reality, both have their share of Windows similarities and differences.  It seems to come down to preference.  I see them nearly equally departed from the Window's environment. :)

[QUOTE=badrad]Wow, fantastic responses and links, really helping me become familiar with the system. So, to see if I understand the file structure, if I was installing an app I downloaded I would put it in /usr/bin/appname/ and it would store its data in /usr/share. If I was storing stuff like documents and music, I would use my user directory in /home. Does that sound accurate?[/quote]

Really, the installation of the apps will do everything behind the scenes.  Ubuntu has a fantastic package manager -- everything is precompiled for Ubuntu.  You can search for packages, download them, and install them with a couple clicks.  If something isn't in the repositories, then you may have to compile it from source (a couple commands from the command line, maybe some searching for dependencies to install first, and that's _normally_ all there is to it).  In either case, the application is installed to the locations it needs by default.  Unless one is developing a new app or something, one doesn't need to venture in the /usr folder often.

EDIT:
And yes, everything that is 'yours' should go in your /home directory.  Your home folder is the only location you have permission to write to by default.  This is done as a safeguard for your system against yourself, others, and the potential for malicious software.  This is a large factor in why _most_ *nix machines are more inherently secure.  To gain access to other parts of the system, 'sudo' is used on the command line and 'gksudo' is typically used for GUI apps.  You are prompted for the root password, and then given access.

[QUOTE=badrad]I'm having trouble understanding this. I can see that for anything to be executable the user must be granted execute permission for that file. But obviously not all files are executable, only binaries and scripts right? If there is no filetype, than how is one to know what files can be execute and what cant? If I look at a folder with 40 files in, how do I know which ones are executable?[/quote]

I think I'll clarify a little.  As expressed before, extensions really aren't all that necessary (though should still be used).  For executables, I did a quick test.  I made a new text file named 'asd' with text "blah chaisekncuie" (random garble) to see what would happen if I tried to execute it:
tom@thtroyer:~/Desktop$ ./asd
./asd: line 1: blah: command not found

Apparently, if the file isn't a binary file (compiled machine code), it runs it as a script, which should default to BASH automatically.

An example of a working script would be helloworld, "echo Hello World":
tom@thtroyer:~/Desktop$ ./HelloWorld
Hello World

Hopefully that makes more sense. :)

---

### Post by badrad on 2006-06-02
Well, I dove in and have Ubuntu running. I have a few more questions, and I could create new threads but since you have all helped me so much I'll just put there here for now.

There were some positive and some negative experiences :) As far as negative, I started with the GParted Live CD to do some partitioning - and it wouldnt boot, informing me it could not find a screen, despite the fact that it displayed said error message to me on my screen. But, hey, there you go.

So instead of partitioning I just popped in an extra hard drive and gave Ubuntu full reign on it. Ubuntu booted off the live cd and installed beautifully. Some tasks are ridiculously simple - adding and removing programs through the interface, for example. I think I had amarok in like two clicks.

Anyway, off the top of my head (back in Windows now :( ) here were some of my issues:

1. Most important - I have no sound. I have a Creative X-Fi soundcard, with no linux drivers on their site. Some search of the web has revealed that I am probably screwed - is that still the case? It's a huge bummer, although I am aware it is Creative's fault not Ubuntus.

What does that leave me? Do you think if I switched on my onboard (nforce4 board) sound Ubuntu would pick that up? I'd still have to swap my audio connection which would be unpleasant but at least I would have sound.

2. NTFS read access. When I browse my computer I can see my NTFS drives, but I when I double click them I get an error that they can't be mounted. I thought Ubuntu could read from NTFS ok?

3. Grub weirdness. When I first installed Ubuntu, my computer rebooted right into Windows - no grub. I changed the boot disc to the disc with Ubuntu and just got an error that the OS could not be started. Then I figured out Ubuntu assumed my primary master drive was the drive to put grub on, even though I boot off of a SCSI drive - but I guess it has no way of knowing that. Anyway, now grub is on a random older storage drive of mine - I set it to boot and it works fine, but what happens when I remove that drive? Trying to boot the Ubuntu drive directly doesn't work. It's something I don't have to deal with anytime soon, just curious...

4. I set up compiz already, which was kind of an adventure :) I've customized it a little to my liking, but one thing I couldn't figure out is how to turn "wobbly" off the menus. I like the wobbly effects most everywhere, but I despise them on menus (file, edit, etc.). I tried every option in the dialogue and couldnt get it off. Is it all or nothing right now?

easier questions:

5. I went to gnome-look to look at other themes and there are a bunch of theme types - GTK 1, GTK 2, metacity, GDM...what do I want to use?

6. Is their any "widget" like program for Gnome? I found Super karamba but thats for KDE.

7. Where's my nvidia control panel? Do I even have an nvidia control panel?

I am still getting used to my way around Ubuntu, but its nice so far I just gotta quit it for today and go to bed. It's easy to see that the only real limitations to linux are hardware and application support - both which are really the problems of the respective companies.

Anyway, thanks again for all your help!

EDIT:
I'm also assuming their is a quick key command to access the terminal like you can do windows+r to get run in windows. I couldnt figure it out though, is there such a keycommand?

---

### Post by B0rsuk on 2006-06-02
First, this seems like a good guide, althrough I can't verify it without installing gnome. Some solutions in there rely on Gnome GUI tools.
[http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide)
> 
1. Most important - I have no sound. I have a Creative X-Fi soundcard, with no linux drivers on their site. Some search of the web has revealed that I am probably screwed - is that still the case? It's a huge bummer, although I am aware it is Creative's fault not Ubuntus.

I did a quick search and it seems this card simply doesn't work with linux, but if you enable your onboard soundcard, it should work. Try doing it with gui...

When trying to configure sound (or something else), manufacturer's site is usually the last place I look. Lots of hardware doesn't officially have linux drivers etc.
My ac97 was configured properly out of the box, but this is where I would start if I had problems:
1: [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)
"Howtos" subforum is all about guides to installing/configuring something.

 use search function of this forum. There are many duplicate threads.
Unfortunatelly I can't help you more with sound, I didn't need to reasearch the topic.

2. 'hardware' subforum:
 [http://ubuntuforums.org/forumdisplay.php?f=135](http://ubuntuforums.org/forumdisplay.php?f=135)
3. "video and sound' subforum
[http://ubuntuforums.org/forumdisplay.php?f=138](http://ubuntuforums.org/forumdisplay.php?f=138)
4. 'absolute beginner' forum...
[http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)

In general, Linux treats drivers a bit differently than windows. Linux has one big kernel which contains most (all?) drivers. Some drivers are compiled into kernel and you can't change it without recompiling, but many can be inserted as modules. Then you may need to execute some script (like in case of nvidia-glx) or edit a configuration file or two manually. Never try this without documentation/howto of some sort. Ubuntu often makes it as simple as installing a package via synaptic/adept/apt-get .

NTFS... I don't have an NTFS partition to toy with, but I used to have and it worked. Most probably you just need sudo/root to mount other partions.
I'd check mounted devices with ```
df -h
```
At which point it is worthwhile to mention Linux naming convention...
Hard drives will probably be named like this: hda, hdb, hdc (often reserved for cdrom) etc. Partitions are distinguished with numbers, for example hda1, hda2, hda3.
I usually apply some guesswork, but I you know your hardware inside out you can guess which partition do you need to mount. Hda seems to be the one on first cable/primary disk, hdb - secondary etc.  If in doubt, check /etc/fstab: ```
less /etc/fstab
``` (exit with q). You should see a list of mountable devices; you're obviously interested in ones with NTFS in description. Then you can mount it with 
mount /dev/deviceshortcut /where , for example
```

sudo mount /dev/hda1 /media

```
When done, do 
```
sudo umount /dev/hda1
``` (replace hda1 with something else) 
I do it this way because I used Debian before. There may be easier/gui ways to do it. At this point you should have the drive mounted.... but by default you aren't allowed to view mounted drives. I would try ```
sudo nautilus
``` to run nautilus with root privileges, and then navigate to /media. 
I post partially to provoke someone to mention more user-friendly way... a way that involves spending less time as 'root'.

About quick console command: not sure about Gnome, but in KDE you do it with ALT-F2. In any case, I always have a terminal or two open.

Are you sure you have proper video drivers installed ? If you want hardware acceleration, you are going to need nvidia-glx or nvidia-glx-legacy for older cards such as my GeForce2 MX. The easiest way to check if you have opengl enabled is to try some sort of opengl screensaver. If you need to install the glx (probably), be sure to read the package description. It says *To enable the driver, run "sudo nvidia-glx-config enable".* After doing this, it should work. NOTE: messing with sensitive stuff like graphic drivers or kernel can ocassionaly stop your x.org (graphical mode) from working. That's why installing glx with command mentioned above backups your /etc/X11/xorg.conf file.  If it breaks, all you have to do is to copy older configuration file back in place. But this would require you to know some basic shell commands, otherwise you're toast. 
Don't count too much on drivers/packages making backups for you, you never know which are going to do backups and which not. Better safe than sorry.

---

### Post by DaveRowell on 2006-06-02
I'll give it a whirl - that's where I was last fall!

1 - Gnome is the default - you know defaults are nice, right?  Anyway its no big deal to change to KDE or something else for that matter.  If you don't like Gnome change later.

2 - can't comment I'm running an AMD Athlon XP 3200+

4&5 - I'm dual booting XP Home and Dapper.

In XP I use explore2fs to read or copy files on my ext3 formatted partitions.  In Ubuntu I have my NTFS drive mounted as read only so that I have no chance of screwing-up those files.  There are extensions to both systems to allow write access but why play with fire?

I have a Windoze NTFS partition, an ext3 partition for / (root), an ext3 partition for /home, a FAT32 partition for shared files, and of course the swap partition.  The last three are extended partitions.  I have no plan to change that setup in the forseable future.  If it wasn't for FEMA, and maybe Ancestral Quest, I'd dump Windows entirely.

I understand that GRUB, Ubuntu's default boot loader, will handle booting from multiple drives.  I suspect that you'll want to follow the text mode install path.

6 - I'm surprised no-one mentioned it but the documentation included in Dapper is pretty darn good.  I'd suggest spending some quality time in the 'help' section, click the life preserver in the upper panel.  

I'd also suggest TUX magazine as a useful resource for Linux Noob's.  [www.tuxmagazine.com](www.tuxmagazine.com)  D/L and browse the back issues too.

As someone else has said come here when you get stuck - everyone's bent over backward to help me over the rough spots - for which I thank all of them
:p

---

### Post by badrad on 2006-06-04
Thanks for your help B0rsuk, I was able to get NTFS read working.

As for my other questions and new questions, I guess I'll start opening new threads :)

Actually, here's a question for you guys if you check this thread...I mentioned one of the things I want to do is learn my way around the unix filesystem. Well, take this example. I screwed up my settings in Amarok real bad to where I couldnt even get back at the settings. So, I uninstall the program using add/remove. Reinstall. Settings still screwed up. So I uninstall the program using Synaptic Package Manager and saying destroy configuration files. Reinstall. Settings still screwed up.

So it's saving settings, but where would they be. In Windows I know all the various places to hunt for settings, but in Ubuntu I am clueless.

Now I have since solved my Amarok problem but its just an example of how I don't know where to look for stuff. Where would I look for the Amarok settings for example? Just trying to learn my way around :)

---

### Post by blimpyboy on 2006-06-04
[QUOTE=badrad]Thanks for your help B0rsuk, I was able to get NTFS read working.

As for my other questions and new questions, I guess I'll start opening new threads :)

Actually, here's a question for you guys if you check this thread...I mentioned one of the things I want to do is learn my way around the unix filesystem. Well, take this example. I screwed up my settings in Amarok real bad to where I couldnt even get back at the settings. So, I uninstall the program using add/remove. Reinstall. Settings still screwed up. So I uninstall the program using Synaptic Package Manager and saying destroy configuration files. Reinstall. Settings still screwed up.

So it's saving settings, but where would they be. In Windows I know all the various places to hunt for settings, but in Ubuntu I am clueless.

Now I have since solved my Amarok problem but its just an example of how I don't know where to look for stuff. Where would I look for the Amarok settings for example? Just trying to learn my way around :)[/QUOTE]

Per-user settings are saved in the user's home directory in directories beginning with a "." .  Directories (and files) that begin with a dot are 'hidden' in that by default 'ls' (and probably gui browsers) won't show them.  You can list them however with "ls -a" (first cd to your homedir) .  I'm not sure if amarok has its config dir or it is somewhere inside ".kde" (kde and kde apps settings dir).

---

### Post by badrad on 2006-06-04
[QUOTE=blimpyboy]Per-user settings are saved in the user's home directory in directories beginning with a "." .  Directories (and files) that begin with a dot are 'hidden' in that by default 'ls' (and probably gui browsers) won't show them.  You can list them however with "ls -a" (first cd to your homedir) .  I'm not sure if amarok has its config dir or it is somewhere inside ".kde" (kde and kde apps settings dir).[/QUOTE]
Ah ha! I see now! Thank you so much.

I am beginning to feel comfortable in linux, which is great. Its about time I made myself do this. "ls -a" ... I must remember that now. Thanks again blimpyboy!

---

### Post by ffi on 2006-06-04
[QUOTE=badrad]Wow, three quick and thoughtful answers. I can't thank you enough.

1, 2, 3. Well, I'll definitely go with 32bit gnome to start. Sounds like the best place. I can always branch out and play with KDE later, or 64bit if I want to torture myself. Thanks a lot for the advice. As far as compiz, once I am decently comfortable in Ubuntu I'll give it a shot.
[/QUOTE]
I find that KDE is way easier to get into than GNOME, GNOME hides all the options, so you spend hours looking for the way to make GNOME work the way you want it to work, rather than how the devs wanted you to work with GNOME. KDE makes this very easy, i´e been using linux for a few months but still am quite lost in GNOME, whereas in KDE I felt home almost right away.

---

### Post by ffi on 2006-06-04
[QUOTE=badrad]
2. NTFS read access. When I browse my computer I can see my NTFS drives, but I when I double click them I get an error that they can't be mounted. I thought Ubuntu could read from NTFS ok?
[/QUOTE]
You might want to install Captive-ntfs and Fuse, which use the windows driver for reading/writing ntfs, it is a bit slow but at least you will have full r/w access to ntfs. Then you may need to modify your fstab file so regular users can read/write ntfs too, see:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

The latest linux kernels(>>2.6.16) supposedly have full ntfs support too.

---

