---
title: "Installing Applications to Various Drives"
date: 2009-12-14
forum: General Help
---

### Post by Tyrionn on 2009-12-14
Cheers All!

I have a very noobish question:

When I use the Add/Remove Applications or the Synaptic Package Manager they appear to install the programs to the default "C" drive.  I have two other drives and would like to install programs to drives other than "C."

How do I go about doing this?  :D

---

### Post by earthpigg on 2009-12-14
there is no "C drive" in ubuntu...

do you mean that you want to install them to different *[partitions]("http://en.wikipedia.org/wiki/Disk_partitioning")*?

short answer: there is no reason to do this that a supernerd would approve of, so no supernerd has coded an easy way to do this that i am aware of.

if you could provide more detail as to the exact dilemma making you wish to consider doing this, though, we could probably help you out.

---

### Post by raymondh on 2009-12-14
> **earthpigg said:**
> 

if you could provide more detail as to the dillemma making you wish to consider doing this, though, we could probably help you out.

+ 1

---

### Post by Tyrionn on 2009-12-14
> **earthpigg said:**
> 
if you could provide more detail as to the exact dilemma making you wish to consider doing this, though, we could probably help you out.

Okay......let me see if I can rephrase this a bit better:

I have my **/home** (that I think of as "C" cause I'm....well.....very green).

I also have two drives, which are mounted: 1 - **/media/drive one**; and, 2 - **/media/drive two**

I would like to install a program on **/media/drive one** and not on **/home/name**

Is this possible?  Or is my thinking too windows-centric and I need to see this differently......?

---

### Post by earthpigg on 2009-12-14
hrmm....

let me see if i can break it down a bit more accurately for ya:

this is very rough, as there are no exact equivelants.

/ is the 'root filesystem'. anything capable of interacting with the CPU in your computer is a file or folder within it. speakers, keyboard, hard drive partitions, everything. everything listed below can be it's own partition, but usually people only do this for home.

/bin is c:\windows\ (you dont play with this, you let the package manager do it)

/boot is ummm c:\autoexec.bat, system.ini, and stuff like that. the bootloader lives here.

/usr/bin and /usr/share/bin are c:\windows\program files (you dont play with this, you let the package manager do it)

/home is "my documents and settings" - this is where the settings for various programs go, but the programs themselves do not go here. open your /home/username/ folder in the file manager and select view -> show hidden files and folders. see the stuff that starts with a period? .bashrc, .mozilla, .openoffice, etc. all that stuff usually is is text files that store the settings for a given program.

/dev is where the 'files' and 'folders' that represent things like thumb drives and keyboards and hard drives and partitions go. anything plugged in is assigned a file or folder here.

/var/cache/apt/archives is where backup copies of any software you install via synaptic or add/remove software is kept. this is the equivalent of that stack of install CD's or stack of video game boxes containing a manual and CD that most windows users have sitting around their computer desk somewhere.

/media/whatever represents 'mounted' cd drives and thumb drives and partitions and stuff like that. 'mounted' just means 'ready for you to use'. stuff here is generally ***not needed*** for the system to function. if you want a partition that contains software installed by you, you would probably want to go ahead and have that partition's mountpoint be /usr/.... but this is highly unusual and, in fact, i've never actually heard of it being done. as far as i know, i just came up with the idea (but im sure im not the first person to think of it).

migrating /usr/ to its own partition would be highly irregular, and if it doesn't go right you will break your system.

are you worried about one of your partitions or hard drives filling up?

here are two commands you can safely run that may be helpful for you to take a look at your own system:

```
mount
```

```
df -Th -x tmpfs
```

---

### Post by 3rdalbum on 2009-12-14
As far as I am aware, this can't be done from the repositories.

Some programs, when you download them precompiled from the developer's website, are not actually installed, they are just run where they are. So you would be able to drag them to another place and run them there.

---

### Post by Tyrionn on 2009-12-14
Thank you very much, Earthpig!

Now, how do I go about installing a program onto a specific drive?  My main drive is a Raptor 300gb - I want to use that for the OS and games.  I would like to put programs on one of the other drives.

For some reason I feel like I'm asking a question you just answered :)........ Gotta try, though.....

---

### Post by bodhi.zazen on 2009-12-14
In general programs install to your root partition , or /

If you wish to install applications to other partitions you can do this by compiling them from source code, using the prefix option to ./configure :twisted;

You almost certainly do not want to do this, is there some reason you can not go with the defaults ?

My guess is your best option is to re-install using one of those other partitions as root (/) and your current partition as /home

---

### Post by earthpigg on 2009-12-14
> **Tyrionn said:**
> Now, how do I go about installing a program onto a specific drive?  My main drive is a Raptor 300gb - I want to use that for the OS and games.  I would like to put programs on one of the other drives.

> migrating /usr/ to its own partition would be highly irregular, and if it doesn't go right you will break your system.

the results would be that the basic operating system and basic tools will reside on your / hard drive, while everything you install will go onto the hard drive you designate to mount at /usr.

again, highly unusual and radical. since i've never done it, i wouldn't want to offer you advice on how specifically to do it... i'd need to do extensive testing on my own first to make sure i wasn't giving you broken directions.

it kind of sounds like you are trying to over-organize or re-organize the existing highly organized standard linux filesystem.

ya know the old saying that "if it aint broke, dont fix it!" ?? i think it applies here.

efforts have been made to radically alter the fundamental underlying filesystem of Linux.... it isn't very popular. they are so busy trying to implement what you are asking for, other features and the like don't get much attention. [http://en.wikipedia.org/wiki/GoboLinux](http://en.wikipedia.org/wiki/GoboLinux)


if you describe to us exactly how much data you have and whatnot (ie: "300gb of movies kept on this hard drive, 20gb of music"), we could help you come up with a better partitioning scheme than you currently have... if needed.

---

### Post by earthpigg on 2009-12-14
one more thing to consider:

if you start having different programs residing on two different hard drives, that means your system is ***twice*** as likely to break due to hard drive failure if any of them are essential to the system functioning.

---

### Post by Tyrionn on 2009-12-14
Thank you all for answers to my questions!  

I'm going to leave things as they are - programs and such as default, and music & photos on the other drives.

I need to learn more before I go rooting around too far in linux (though my nature is to fiddle till I bust it and then figure out why it broke).  Right now I feel like I'm imposing a windows paradigm where one does not exist.

Thanks Earthpigg for helping me visualize the structure.  The more I think about it, the simpler it is......my head just keeps slipping into old mappings.

Cheers!

---

### Post by earthpigg on 2009-12-15
> **Tyrionn said:**
> I'm going to leave things as they are - programs and such as default, and music & photos on the other drives.


if you want your music and photo hard drives to appear at /home/your-username/music and /home/your-username/photos... that might be a good place to start for this:

> (though my nature is to fiddle till I bust it and then figure out why it broke)

expect a few things to bust on your first attempt, but if you want to give it a shot google for the outstanding 'how to fstab' writeup that exists on these forums somewhere.

to get a sneak peek at one of the things you will be editing:
```
cat /etc/fstab
```

if you have another computer (even a windows computer, or an ipod, or a mac, or damn near anything that has an IP address) that you want to set up to be able to 'remote control' your ubuntu computer, do some reading up on 'ssh'.

---

