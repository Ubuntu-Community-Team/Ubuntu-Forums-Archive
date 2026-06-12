---
title: "ready to throw my ipod out the ****ing window"
date: 2010-02-05
forum: General Help
---

### Post by cscott5288 on 2010-02-05
uggghh, I have been trying to sync my ipod with ubuntu for weeks now and I have had no luck. I installed banshee and after a few days of troubleshooting I FINALY got Banshee to recognize my ipod when I plugged it in. Unfortunately, when I open ipod in banshee I get: Unable to read your ipod with two hyperlinks: 'what is the reason for this?' and 'rebuild iPod database'. When I try to rebuild the database, I am able to view music on my ipod within banshee. I can even drag and drop files from my library to the ipod and it appears to work. Until I umplug my ipod and check if the new songs are on there -- they are not and everytime I plug the ipod back in I get the same "unable to read ipod" message in banshee and I have to rebuild if I want to see the music in my ipod again ...

Please help me. Windows 7/vista is a ****in joke; ubuntu is great but you have to be a god damn computer hacker to sync your ipod.

---

### Post by jrusso2 on 2010-02-05
Best you can hope for is drag and drop apple wants you to use iTunes to synch.

---

### Post by saturnblackhole on 2010-02-05
what model ipod do you have? currently only the classic ipods have support in media players meaning the ipod touch and nano are not supported you can try to see if you have better luck using song bird. 

if you have the model that isnt supported you can try to a)see if itunes work in wine b)sync your ipod in ms thats running in virtualbox or on another partition (dual boot) or c)get a new mp3 player lol

---

### Post by switch10 on 2010-02-05
Haha throw it to me!!

but seriously I have been messing with this for nearly a year now.  I have an IPhone.  Like all of the modern SSD ipods, its a pain to sync with Ubuntu.  I can sync my older ipod no problem with banshee or rhythmbox.

I'll save you some time.  Install virtual box from the website, not the OSE version.  Install Windows XP (I hate Windows 7 as well, It's way to "dumbed down"), install ITunes or other and set up a shared folder with your Music folder in Ubuntu.

This is truly your best option.  There is no USB support in Wine so you can forget about syncing with Itunes in Wine.

I wrote a step by step for upgrading jailbroken iphone firmware using ubuntu and virtualbox.  here: [http://u-bunted.blogspot.com/](http://u-bunted.blogspot.com/)  You can follow the first half of it at least to get all the links you will need to install and configure Virtual Box

good luck

Dave

---

### Post by cscott5288 on 2010-02-05
but i have ipod classic video ... i don't understand why it won't work

do you need an official xp license to install an xp emulator?

---

### Post by Ginsu543 on 2010-02-06
> **switch10 said:**
> Haha throw it to me!!

but seriously I have been messing with this for nearly a year now.  I have an IPhone.  Like all of the modern SSD ipods, its a pain to sync with Ubuntu.  I can sync my older ipod no problem with banshee or rhythmbox.

I'll save you some time.  Install virtual box from the website, not the OSE version.  Install Windows XP (I hate Windows 7 as well, It's way to "dumbed down"), install ITunes or other and set up a shared folder with your Music folder in Ubuntu.

This is truly your best option.  There is no USB support in Wine so you can forget about syncing with Itunes in Wine.

I wrote a step by step for upgrading jailbroken iphone firmware using ubuntu and virtualbox.  here: [http://u-bunted.blogspot.com/](http://u-bunted.blogspot.com/)  You can follow the first half of it at least to get all the links you will need to install and configure Virtual Box

good luck

Dave
This +1. This is exactly the method I chose when I recently purchased an iPhone, and I have had zero problems syncing my iPhone through iTunes. As Dave said, you need to get the PUEL version so that you will have full USB compatibility. So don't throw your iPod out the window, just throw Windows at it through Virtualbox! :D

---

### Post by n0dix on 2010-02-06
I sync a classic and nano iPod with no major problem with Rhythmbox.

---

### Post by cscott5288 on 2010-02-06
> **Ginsu543 said:**
> This +1. This is exactly the method I chose when I recently purchased an iPhone, and I have had zero problems syncing my iPhone through iTunes. As Dave said, you need to get the PUEL version so that you will have full USB compatibility. So don't throw your iPod out the window, just throw Windows at it through Virtualbox! :D
Yeah ... I looked at virtual box. No way I am going to have the patience to go through the 999 step installation process. I am chucking my ipod and getting a zune because i just don't have patience for this **** anymore. God, what a man needs to do to get a working computer around here. I would have been perfectly content with XP or even 98 but no, the world had better plans for me. They put a gun to my head and forced me to use windows vista and then, after it crashed and wiped all my data three times I installed windows 7. When that crashed and wiped my data, i installed ubuntu and have been trouble shooting for three months to get all my **** working just like it was on xp. boo hoo, there's my sop story. Oh yeah, I hate ipod too because all it is, is a normal mp3 player with constraints, like having to use itunes. Of course I had plans to install just windows vista on a seperate partition but I am unable to do that because HP want's to charge me $25 to ship recovery disks ... when I already payed for the software. It's not my fault they put the recovery ON THE  HARD DRIVE. What is the point of that? Why put a recovery partition on a hard drive when -- 90% of the time -- it is the hard drive that fails? It is a sick twisted world.

---

### Post by mushwars on 2010-02-06
Had the same exact problems.

You need the program called banshee it is the only one that can sync your device.

When you get the stupid Ipod error that says you need to run the itunes restore utility, all that does is format your device you can do that with mkfs.vfat /dev/<DEVICE NAME> (probably sdb or sdc)

---

### Post by NFblaze on 2010-02-06
Check out [Rockbox.org]("http://rockbox.org") and see if you can throw rockbox onto your Ipod. Give it a spin you might like it better. Also, it works by making your ipod dual-bootable so you can boot into either normal ipod mode or rockbox mode.  That should also help you add music and sync/drag and drop better with your computer much better than the rotten Apple.

---

### Post by tacantara on 2010-02-06
Setting up VirtualBox and installing a Window OS on it isn't quite as difficult as you think.  I run XP in a virtual machine, and it was really easy to set up.  I can sync my iPod touch without fail, and I can even talk to the XP desktop in my home to share files and a printer while running "XP in a box."

I used to have a Zune, and it is a decent music player, but it isn't any easier to sync music files to it than the iPod.  In fact, I had more problems with the Zune in Ubuntu than I had with the iPod.  Like some of the other people who have posted here, I was able to get an iPod Classic to sync in Banshee...music files and videos.  Believe me, if you wind up with a Zune, you'll definitely have better luck syncing it with the Zune software on a Windows machine...virtual or otherwise.

There are many posts on the subject of portable music players in the Ubuntu Forum.  Do some checking.  There are MP3 players that actually work quite well with Ubuntu (I can't recall any of them off the top of my head, but I've seen several posts on the subject).

---

### Post by switch10 on 2010-02-06
> **cscott5288 said:**
> Yeah ... I looked at virtual box. No way I am going to have the patience to go through the 999 step installation process. I am chucking my ipod and getting a zune because i just don't have patience for this **** anymore. God, what a man needs to do to get a working computer around here. I would have been perfectly content with XP or even 98 but no, the world had better plans for me. They put a gun to my head and forced me to use windows vista and then, after it crashed and wiped all my data three times I installed windows 7. When that crashed and wiped my data, i installed ubuntu and have been trouble shooting for three months to get all my **** working just like it was on xp. boo hoo, there's my sop story. Oh yeah, I hate ipod too because all it is, is a normal mp3 player with constraints, like having to use itunes. Of course I had plans to install just windows vista on a seperate partition but I am unable to do that because HP want's to charge me $25 to ship recovery disks ... when I already payed for the software. It's not my fault they put the recovery ON THE  HARD DRIVE. What is the point of that? Why put a recovery partition on a hard drive when -- 90% of the time -- it is the hard drive that fails? It is a sick twisted world.

I am personally not an Apple fan either.  There is no way I would ever pay for an IPhone.  Mine was given to me because a friend thought it was broken.  

There are many other players that will sync with Ubuntu.  Search here in the forums.  

There is no reason, however that your Ipod classic will not sync.  Do you have GTKpod installed?  search for that in package manager.  Also look for libgpod4.  I have both of these programs installed, and my ipod classic syncs fine with rhythmbox.  no setup required, plug it in and transfer songs.

---

### Post by platosearwax on 2010-02-06
I have VirtualBox and XP installed and it was easy.  My wife's Creative Zen Vision:M syncs just fine now through that.

I have a Cowon A3 PMP and as far as I know, all Cowon and iAudio players connect to PC's as a USB storage device.  Drag and drop for everything.  Plus, they are the best sounding audio devices around.  And they play ogg and flac.

---

### Post by cscott5288 on 2010-02-06
> **switch10 said:**
> I am personally not an Apple fan either.  There is no way I would ever pay for an IPhone.  Mine was given to me because a friend thought it was broken.  

There are many other players that will sync with Ubuntu.  Search here in the forums.  

There is no reason, however that your Ipod classic will not sync.  Do you have GTKpod installed?  search for that in package manager.  Also look for libgpod4.  I have both of these programs installed, and my ipod classic syncs fine with rhythmbox.  no setup required, plug it in and transfer songs.
This is the problem that I have ... I try to download this stuff but I get stuck at the install. I am trying to install GTKpod right not, but what does this mean:

`cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

That is all in the install readme. What does 'cd' mean?

EDIT: ok, wait I kind of get it. You only need to 'compile' if you are using the source files to install and I can install easily by just searching for the program in software center and clicking the install button?

---

### Post by switch10 on 2010-02-06
> **cscott5288 said:**
> This is the problem that I have ... I try to download this stuff but I get stuck at the install. I am trying to install GTKpod right not, but what does this mean:

`cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

That is all in the install readme. What does 'cd' mean?

EDIT: ok, wait I kind of get it. You only need to 'compile' if you are using the source files to install and I can install easily by just searching for the program in software center and clicking the install button?

yeah you got it.  just find those programs in synaptic package manager.  It should work then.

---

### Post by LightB on 2010-02-06
If it's a 5th generation nano, it won't work yet, I don't think. Unless ubuntu already carries the necessary svn version of libgpod. I don't think it does. Didn't get such nano to work.

---

### Post by switch10 on 2010-02-06
> **LightB said:**
> If it's a 5th generation nano, it won't work yet, I don't think. Unless ubuntu already carries the necessary svn version of libgpod. I don't think it does. Didn't get such nano to work.

He said it was an Ipod Classic

---

### Post by cscott5288 on 2010-02-06
> **switch10 said:**
> He said it was an Ipod Classic
No, I'm sorry that was a misnomer. It's a 5th generation ipod video, model a1136. I got gtkpod to recognize it but one problem: I can't transfer wma files into my library. 25% of my songs are WMA format unfortunately. What to do ...

EDIT: plus gtkpod crashes my system every time it tries to import my music library.

---

### Post by switch10 on 2010-02-07
if its a newer, solid state hard drive IPod you are SOL.  Sorry dude.  Gonna have to take my advice in my first post about installing Virtualbox.  Its not as hard as it looks.  Pretty straight forward.  I bet you will have it up and running in less than an hour.

If the 5th gen video is not a solid state hard drive, you should be OK.

check [this ]("http://www.linuxquestions.org/questions/linux-software-2/convert-wma-to-ogg-226230/") out to convert wma files in linux

---

### Post by switch10 on 2010-02-07
> **cscott5288 said:**
> No, I'm sorry that was a misnomer. It's a 5th generation ipod video, model a1136. I got gtkpod to recognize it but one problem: I can't transfer wma files into my library. 25% of my songs are WMA format unfortunately. What to do ...

EDIT: plus gtkpod crashes my system every time it tries to import my music library.

You dont need to use gtkpod to actually transfer the files.  Banshee or rhythmbox should now see your ipod as well.

---

### Post by captaincrook on 2010-02-07
5th Gen Video is working fine for me in Karmic. The precaution I had taken was to initially use nothing higher than iTunes 7 otherwise the database gets fudged (at least, thats what happens to me all the time).

I installed podsleuth and banshee. I also installed all the g-streamer plugins so it could convert properly (good, bad ugly, whatever was there) when syncing other formats to my ipod.

Lastly, I had mounting issues. What I did was add myself to the Disk usergroup and access the iPod via Dolphin (I use Kubuntu, the Gnome equiv would be Nautilus). After Dolphin accessed my ipod, it was mounted in Banshee and I was able to easily sync my library. Amarok doesn't fancy my iPod much it seems so I am using banshee purely to sync.

---

