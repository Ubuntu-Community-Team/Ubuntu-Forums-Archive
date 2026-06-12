---
title: "Where are the system files and folders located?"
date: 2012-03-24
forum: General Help
---

### Post by oslub on 2012-03-24
Hello everyone.

I installed lubuntu together with windows xp on my desktop (the first option in install menu) and now I would like to resize partitions on my hard drive.

I am not sure where lubuntu files and folders are located and I'm afraid I can delete them with the procedure.

So I would like to know where exactly are they located and if I can see them on windows explorer.

On my computer, only the three partitions I created are showing up, but on disk management there are three other partitions, which are said to be unknown by windows. 

How should I proceed to move only free space from one partition to another, in case this "hidden" partitions are necessary for lubuntu?

Thank you in advance ;)

---

### Post by JC Cheloven on 2012-03-24
- Every LUbuntu system file should be in the Lubuntu partition. Clean and nice.
- Windows not seeing/understanding linux partitions is normal behaviour.
- If you want to resize partitions, keep these simple rules:
- - Resize windows from within windows
- - Resize linux from a live linux cd (use gparted for that).

If you wish, please post back here what your intent is in particular, and the output of this comand at a terminal:
```
sudo fdisk -l
```

---

### Post by Bucky Ball on 2012-03-24
> **jc cheloven said:**
> - every lubuntu system file should be in the lubuntu partition. Clean and nice.
- windows not seeing/understanding linux partitions is normal behaviour.
- if you want to resize partitions, keep these simple rules:
- - resize windows from within windows
- - resize linux from a live linux cd (use gparted for that).

If you wish, please post back here what your intent is in particular, and the output of this comand at a terminal:
```
sudo fdisk -l
```

+1

---

### Post by oslub on 2012-03-25
> **JC Cheloven said:**
> - Every LUbuntu system file should be in the Lubuntu partition. Clean and nice.
- Windows not seeing/understanding linux partitions is normal behaviour.
- If you want to resize partitions, keep these simple rules:
- - Resize windows from within windows
- - Resize linux from a live linux cd (use gparted for that).

If you wish, please post back here what your intent is in particular, and the output of this comand at a terminal:
```
sudo fdisk -l
```

First of all, thank you very much for your reply.

So, this means that using windows explorer I can move some files I need to my D: and E: partitions without having to worry about overwriting LUbuntu files, since they are located in the "unknown" partition with 4,36GB in size, which I cannot open in windows.

Actually this is very nice, because using Easeus partition master, I can see all of the partitions and there I am able to easely resize the main partitions, leaving the Lubuntu partitions intact and I can make use of my regular partitions as I used to, without any concerns I guess.

I can assume that a windows failure or virus won't compromise lubuntu (except if it is a boot failure), which is another nice thing, although I keep making backups with driveimage xml, now I know I won't lose access to my windows documents.

Anyway, whenever I need more space in Lubuntu partition, I should increase using Gparted right?

Taking advantage of the discussion, I would like to know three more things, as a linux beginner. 

First, is it required to install an antivirus on a linux distribution or is it completely safe? Secondly, I shall search for this on forum but in a quick reply, can you tell me how to backup Lubuntu settings or even partitions for restoration after some sort of problem? Finally, how can I prevent someone to acess my windows files and documents, using a live usb distribution for some bad purpose?

Thank you in advance

---

### Post by matt_symes on 2012-03-25
Hi

I would _highly_ recommend backing up the drive first. 

Take an image using Clonezilla or ddrescue or a Windows tool.

Kind regards

---

### Post by zombifier25 on 2012-03-25
> **oslub said:**
>  First, is it required to install an antivirus on a linux distribution or is it completely safe? Secondly, I shall search for this on forum but in a quick reply, can you tell me how to backup Lubuntu settings or even partitions for restoration after some sort of problem? Finally, how can I prevent someone to acess my windows files and documents, using a live usb distribution for some bad purpose?

Thank you in advance

 1. Generally you don't need an antivirus on a Linux system, unless you usually share files with other Windows users.
2. For backup, Ubuntu 11.10 has a GUI backup tool installed by default. Or, you can use rsync to copy your files to somewhere else:
```
rsync -av --delete /source/folder /source/folder/2 /source/folder/blabla /destination/folder
```
Destination folder should be located on a different partition. The -av flag is to copy only new/modified files, and the --delete flag is to delete files on destination that are no longer on the source.
Generally, to save all of your personal files and program settings, configurations, you only need to backup your home folder.
3. Not possible. If you want to prevent anyone from viewing your files, use an encryption tool like [TrueCrypt](http://www.truecrypt.org/)

---

### Post by garvinrick4 on 2012-03-25
I have a little time going to type out a partition scheme that works well.
I myself use app "gparted" in Live CD to partition with then go to install system
and just place my / and /home and swap into pre-made partitions.


Make your own partitions:
Windows comes with machine has usually sda1
If windows 7 usually a /boot is in sda1 already
The windows 7 operating system is then in sda2
They are both making 2 primary partitions (YOU GET 4 TOTAL)
Now resize Windows to make room for linux lets say 100 gig for linux
Now make extended partition of whole 100 gig. (that is now 3 Primary partitions)
Inside of extended you can now make all the logical partitions you want.
There Linux assaigned numbers will be sda5 and up. (sda is drive sda5 is partition #.
In windows they assaign letters C: D: F: and so on linux is sda#'s mean same thing.
now make 10 gig partition for your operating system or /  then make a 74 gig partition for /home and a 10 gig for data to be read in both windows and linux (ntfs format) 
and a  6 gig partition for swap.
Put in install cd and when it says how to installl choose "something else" and we will do it
manually. Make your / of 10 gig in ext4 and format, make the /home 74 gig ext4 format
 and now the 10 gig as ntfs format and last the 6 gig as swap.
Now finish your install.  
 The 10 gig NTFS you made will be issued a Number in Windows such as F or G or such you will see it in windows 
This way you have a means of putting data in that partition to be in both your operating systems. 
Now you never bother your /home and all your personals when doing a fresh install.
They are on two seperate partitions is nice.
If you want to put another operating system of linux make a 10 gig partition for / and for
/home use same one BUT DO NOT FORMAT. Just do not check that button ever will wipe out your home. 
Now you will have 2 operating systems using same /home and that is real nice. Whatever you put in one is in the other as far as /home

Now to back-up just your /home and your / you just need bookmarks in firefox really. Setting up a fresh install takes all or a 1/2 hour to a hour in your / partition.
There are ways of making your own .iso file using "remastery" if ever want to go there and a GUI app called "kickstart" (system-config-kickstart) that you can make your own script to install if you want to go there.
Lots of ways to customize your system but first get your partition scheme correct and then look further down the road. Sky is the limit really.
Can use rsync command and download the whole 300 gig of a Ubuntu mirror and be able to install from within own system using URL with ip address and can install and upgrade in a flash.
Never have to go onto internet you have all local. Fun to do and set up if you got time and 300 gig spare. Lots of things to do with Ubuntu Linux if you investigate and read.

---

### Post by oslub on 2012-03-25
> **zombifier25 said:**
> 1. Generally you don't need an antivirus on a Linux system, unless you usually share files with other Windows users.
2. For backup, Ubuntu 11.10 has a GUI backup tool installed by default. Or, you can use rsync to copy your files to somewhere else:
```
rsync -av --delete /source/folder /source/folder/2 /source/folder/blabla /destination/folder
```Destination folder should be located on a different partition. The -av flag is to copy only new/modified files, and the --delete flag is to delete files on destination that are no longer on the source.
Generally, to save all of your personal files and program settings, configurations, you only need to backup your home folder.
3. Not possible. If you want to prevent anyone from viewing your files, use an encryption tool like [TrueCrypt]("http://www.truecrypt.org/")

Thank you very much for your helpful information zombifier.

---

### Post by oslub on 2012-03-25
> **garvinrick4 said:**
> I have a little time going to type out a partition scheme that works well.
I myself use app "gparted" in Live CD to partition with then go to install system
and just place my / and /home and swap into pre-made partitions.


Thank you for your instructions, they will be very useful, soon I will install ubuntu on my notebook and unlike what I did with Lubuntu, I shall do it on pre-made partitions this time.

By the way I really am enjoying Lubuntu distro, I can't believe I found the perfect OS for my very old desktop, running really smoothly and fast, functional, clean, customizable, no trouble with old motherboard drivers, love it!

---

### Post by JC Cheloven on 2012-03-25
> **oslub said:**
> By the way I really am enjoying Lubuntu distro, I can't believe I found the perfect OS for my very old desktop, running really smoothly and fast, functional, clean, customizable, no trouble with old motherboard drivers, love it!
Glad to see you're finding yor way. I also use Lubuntu in my modern & mighty desktop pc. I like it simple :)

Just in case, for future occasions: if you want to post the output of a command to be run at a terminal (I suggested one in my former post), you have to obvioulsly open a terminal window, type in the command, hit enter, let the output come up, then select the desired text with the mouse, hit Ctrl-Shift-C to copy (at a terminal the Ctrl-C sequence has a different purpose), then go to your post at the forum and hit Ctrl-V as usual.
EDIT: and to rise to perfection, put the text between "code tags", which is done with the button # that you see at the top of the editing window in the forum.

Cheers
JC

---

