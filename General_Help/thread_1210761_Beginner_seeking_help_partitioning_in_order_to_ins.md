---
title: "Beginner seeking help partitioning in order to install Ubuntu while maintaining XP"
date: 2009-07-11
forum: General Help
---

### Post by andrewcd on 2009-07-11
Hi Folks,

I am an absolute neophyte with regard to linux, and I am here seeking some very basic help.  I am not a computer professional, so it is hard to define my questions in such a way as to easily search for the answers via the internet.  In other words, I am a huge n00b.  

The backstory is that I am accustomed to XP, and like it OK.  But I dislike vista, and I don't want to get forced into it by default.  I just got a new Lenovo X200.  It has XP pre-installed, but it comes with a Vista backup disk -- not a XP one.  I figure that Linux is something that I should learn, and now that microsoft is going off the deep end, I should take the time to learn how to use something else.  I also appreciate how many of you spend so much time developing OSs for no money, and I want to try out your product.  

Eventually, I want to figure out how to run a virtual machine with XP, from inside ubuntu.  If all goes well, I'll leave my XP partition and never use it.  But I want to leave it there just in case.

SO, Here is my situation:

[LIST]
[*]I just defrag'd my computer.
[*]I have system restore CD on one disk, and ubuntu on another
[*]**What do I need to know before I boot with system restore and start partition away?  Could I screw up my system?  How do I avoid bad stuff happening while partitioning?**
[*]I want to leave XP in one partition
[*]**How much space should I leave for the XP partition??**
[*][B]How many other partitions should I make?  
[/B]
[*]**How big should they be?**
[*]**Once the partitioning is done, how do I know that my computer is booting from the new partition when I install linux, and not overwriting my XP partition?**
[/LIST]
I realize that people could probably write a lot about this.  I bet that people already have.  Could people reccomend any good tutorials for people like me?

Thanks in advance for any help!  I hope that I'm at least somewhat on the right track.

---

### Post by joseacavallo on 2009-07-11
ok, there are some things you have to know, 1st...Ubuntu is not XP, you cant use the programs that you have on Windows, another one, Ubuntu have a nice Gui when you are installing it, so, it have to be easy even for you to leave the Xp partition like it is roght now.

---

### Post by andrewcd on 2009-07-11
> **joseacavallo said:**
> ok, there are some things you have to know, 1st...Ubuntu is not XP, you cant use the programs that you have on Windows, another one, Ubuntu have a nice Gui when you are installing it, so, it have to be easy even for you to leave the Xp partition like it is roght now.

thanks.  I am aware that things will be totally separate.  I have two computers for the next two weeks, and my new machine is brand new.  the goal is to become accustomed to ubuntu. 

are you telling me that I can install ubuntu without overwriting XP, and without partitioning the disk?

---

### Post by merlinus on 2009-07-11
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by c0mput3r_n3rD on 2009-07-11
> **andrewcd said:**
> thanks.  I am aware that things will be totally separate.  I have two computers for the next two weeks, and my new machine is brand new.  the goal is to become accustomed to ubuntu. 

are you telling me that I can install ubuntu without overwriting XP, and without partitioning the disk?

Partitions are x amount of memory reserved for a particular use.  Therefore, Windows XP is on one partitions, and Ubuntu will have to be on another; if you want to dual boot.  

You also said something about virtualizing XP in Ubuntu? That will work out fine, and if it's what you're planning on doing any way; I say just give Ubuntu the whole disk and then virtualize XP.

---

### Post by joseacavallo on 2009-07-11
of course you can screw up your system, if you dont follow the instructions.
Regularly XP is ok with 60 Gb of HDD, but thats your choice...
you will have to make 3 partitions, one for xp of course, another one for Swap area, and another one for te file system.
you will konw that you di it right, when the pc boots up, an show you the GRUB, the last option have to be the XP system, click on there, and if xp boots up, you are ready :D

---

### Post by andrewcd on 2009-07-11
> **c0mput3r_n3rD said:**
> Partitions are x amount of memory reserved for a particular use.  Therefore, Windows XP is on one partitions, and Ubuntu will have to be on another; if you want to dual boot.  

You also said something about virtualizing XP in Ubuntu? That will work out fine, and if it's what you're planning on doing any way; I say just give Ubuntu the whole disk and then virtualize XP.

thanks.  virtualization is down the line (I'll need it for a few programs that don't yet have linux versions).  I want to give myself a lifeline in case anything goes sour somehow.

in the short term, dual boot is just fine, as basic things I need can be done in linux (openoffice, mozilla suite, etc).  later when I'll need ArcGIS, the virtualization will come in handy.

---

### Post by joseacavallo on 2009-07-11
you can install ubuntu without erasing you xp system, but, you can use virtual box too, its a vrtual machine that lets you emulate any windows OS, but it is not the same, also there are 2 good programs, Wine and Crossover, they just let you play Windows programs, but in a native way.

---

### Post by Daniel1994 on 2009-07-11
If you're not sure if you will like ubuntu or not, I recommend that you install a small ubuntu inside your windows system. This will allow you to try out a full featured version of ubuntu without making major changes to your system. The way to do it:
1. Start the computer as usual
2. Insert the ubuntu CD
3. Open install_wubi(or something like that) on the CD
4. Choose "install inside windows"
5. Fill in a password and all the other stuff
6. Let the CD do its thing

Then, when you reboot you will be given the option to start either from XP or ubuntu.
You can try out ubuntu, and if you don't like it, you can simply boot onto XP, open the "ubuntu" folder in XP and press uninstall. 

hope this helps

---

### Post by andrewcd on 2009-07-11
> **merlinus said:**
> [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

wow!  is it really that simple?

if yes, and Ubuntu automatically creates the partition for itself, then can I simple erase ubuntu later using systemrecoveryCD?

---

### Post by andrewcd on 2009-07-12
more of a basic question now:

I stick the Ubuntu install disk in, and I get the following screen:
[IMG]http://apcmag.com/images/apcapc/howto/Dualboot_-_XP___Ubuntu__XP_first__images/media_1208756272146.jpg[/IMG]

Only nothing is happening when i hit enter!  Enter works for selecting languages, etc, but when I select "Install Ubuntu" and hit enter, nothing responds.  I am using an external DVD drive.  What gives?

---

### Post by TeamJ on 2009-07-12
go into XP, install Partition Magic or something else, resize it (make sure that isn't remove and replace with a smaller one)
boot into install CD, make a partition in the free space, install there
next you need to add XP to the Grub bootloader, visit howtogeek.com for advice

To install select to option above, it will load the "Live CD" bit, then use the install feature in there

---

### Post by whole.grains on 2009-07-12
I suggest you check the disc for errors. It's right under "Install Ubuntu" on the LiveCD. If the CD has errors, burn again using the lowest speed setting. I was looking at the specs of your laptop and it looks like it's more than capable of running Ubuntu. Weird that a laptop(especially one that expensive) comes with no CD/DVD drive.

So another possible problem(not sure) is that you're trying to install from an external CD/DVD drive. You might also want to try installing from a USB stick if your machine will boot from that(see: [http://en.wikipedia.org/wiki/UNetbootin](http://en.wikipedia.org/wiki/UNetbootin)). Or the alternate CD(which is text based).

I'm also pretty green when it comes to Ubuntu/Linux, but I will say when I first tried it out I used that APCMag article and it worked perfectly. You may want to print those instructions out.

-Good luck

---

### Post by theozzlives on 2009-07-12
WUBI (Windows UBuntu Installer) doesn't re-partition your disk. It creates a "virtual disk" on your Windows partition. If you decide to remove it just go to "Add/Remove Programs".

It'll bring up the Windows Boot Menu (not GRUB) where you can choose a fully functional version of Ubuntu, or XP. The CD contains an AUTORUN.INF so if your in Windows, WUBI should start. If not, look on the CD for WUBI.EXE.

---

### Post by andrewcd on 2009-07-12
folks, I got it to work.  I was going about it the wrong way thinking that I needed to partition it manually and then install ubuntu.  turns out ubuntu does it for you.

I am posting this from ubuntu!  Thanks!

---

### Post by jskandhari on 2009-07-12
You want to retain XP right..

go in XP make a extended volume i.e the size you plan for Ubuntu ( file system + Swap).
Then make two partiton in extended volume 
1) for File system 
2) for SWAP recommended size 2x of RAM.

let the partitions be of any format.
next insert the CD/DVD
select "try ubuntu before install" 
Then select install app

When you reach the partition area select the manually select the partition select the "file system partition" you created in format select ext3 and in flags select "/"

Then select the "swap" partition and simply give it the SWAP format
After doing this hit apply..

In this manner you will retain you XP and Ubuntu will be installed and yes don't worry about booting to XP a multi boot will be created..


P.S:: In bookmarks add the XP document and settings folder locations.. will help you save the pics songs and other stuff in one location it self.
## Don't Select import My documents folder ( songs and stuff from Xp ) during install it will ismply copy paste occuping disk space for some thing which is already accessible.

---

