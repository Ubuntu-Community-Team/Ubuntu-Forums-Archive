---
title: "Cannot use some of my programs in ubuntu"
date: 2010-03-22
forum: General Help
---

### Post by shaun67 on 2010-03-22
I have just recently converted to ubuntu and love the OS it's fast and nice but i am having problems as i need to put some software on my pc  that i need..The software is TIS and AUTODATA  ..now i have tried wine with no luck  and have now installed virtual box  with win xp .

my win xp cd worked right away but when i try to add my software off of the cd i keep getting this  " windows cannot read from this disc. The disk might be corrupted or it could be using a format that is not compatible with windows.

But these discs worked fine in my xp before i wiped it with ubuntu..

 So guys if i cannot get my discs to work then i am considering uninstalling ubuntu and reloading xp over it [IMG]http://static.techguy.org/smilies/frown.gif[/IMG] i really like ubuntu it's faster and nicer but i really need this software to work and it won't even in virtual box i can easily download stuff in virtual box but it won't open up my programs from discs..strange thing my xp disc installed without problems ..gonna try once more and if no luck then i have no choice i don't wanna really dual boot unless anyone knows how to get this working.
 
Ubuntu needs to catch up if it wants to be more user friendly for people like me who need certain programs.I was just getting used to it as well[IMG]http://static.techguy.org/smilies/mad.gif[/IMG]

---

### Post by oldos2er on 2010-03-22
If you need to run Windows programs, it's best to do so under Windows.

There may be Linux equivalents to the programs you mentioned, if you could describe their function.

---

### Post by purpleturtle on 2010-03-22
You should be fine with your Windows VM.

Can you successfully read other discs?

---

### Post by Megafag on 2010-03-22
> **shaun67 said:**
> Ubuntu needs to catch up if it wants to be more user friendly for people like me who need certain programs.I was just getting used to it as well[IMG]http://static.techguy.org/smilies/mad.gif[/IMG]

You should ask for a refund sir!! what kind of customer service is this!!

---

### Post by shaun67 on 2010-03-22
The only disc that worked was win xp install disc the funny thing is that when i shut down virtual box the disc load ok in ubuntu but i cannot install the programs ..i see them on the discs but ubuntu does not let me do what i need..

These discs are for automotive use they have data for all cars including wiring diagrams and repairs..

Any ideas appreciated as i would love to stay with ubuntu but i do really need these programs.

Thanks

---

### Post by shaun67 on 2010-03-22
When i close virtual box and reload the cd in ubuntu i can see the files on the cd   ..Trouble is the file says auto run exe  ,this is the installer file that would install the software if it was win xp or vista but i don't have a clue how to get this file to install ..xp i would just double click it and away it would install.

Thanks

---

### Post by bowens44 on 2010-03-22
> **shaun67 said:**
> 
Ubuntu needs to catch up if it wants to be more user friendly for people like me who need certain programs.I was just getting used to it as well[IMG]http://static.techguy.org/smilies/mad.gif[/IMG]

Ubuntu needs to catch up because it won't run some software that was made for another operating system?

If you need windows apps stick with windows.

---

### Post by blueridgedog on 2010-03-22
Do you only have one CDROM drive?

When you start your windows virtual machine, how do you tell virtualbox to mount the CD for the guest operating system?

Have you tried devices - Mount CD/DVD ROM - then select your device?

---

### Post by Mark Phelps on 2010-03-22
Speaking from personal experience, if you really need to use native MS Windows apps, the best solution is to dual-boot. 

It's really no more work than using VB or any other Virtual solution, and if you already have XP up and running, adding Ubuntu in dual-boot mode is really LESS work than wrangling with Virtual solutions.

---

### Post by purpleturtle on 2010-03-23
I think the problem may be that you need to tell VirtualBox that you want to mount your host cdrom on the VM.

To do this, in the Windows VM window select the "Devices" menu then select "CD/DVD Devices" then select "Host Drive....".

You should then see the CD from within the Windows VM.

---

### Post by pcjunkie on 2010-03-23
Nothing works under WINE?

$ start of mini rant
(
Windows should run Linux programs too! If only I could use text mate and have music folders open like they do in OSX..
)// EOR

---

### Post by shaun67 on 2010-03-24
> **blueridgedog said:**
> Do you only have one CDROM drive?

When you start your windows virtual machine, how do you tell virtualbox to mount the CD for the guest operating system?

Have you tried devices - Mount CD/DVD ROM - then select your device?

I have a dvd/cd writer a dvd rom  and a floppy  but the floppy is disabled ..I have managed to get my dvds/cds to load but not i am having trouble ejecting them even after i unmount them..I have tried the command lines but no good ..I have to hold reset button to get my discs back ..This is becoming more and more frustrating..I know it's a free OS but surly these little bugs should be sorted by now.Any other ideas how to get the dam thing to eject without resorting power off !

---

### Post by blueridgedog on 2010-03-24
I eject mine by launching nautilus (places then computer) and pressing the "eject" button that appears beside each loaded disk.

---

### Post by seenthelite on 2010-03-24
There is a virtualization forum here where you may find help with your problem.  Downloading software from the internet into XP in virtual box works.



 [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by cab_bae on 2010-03-24
Hey have you tried Cross Over it's another alternative to wine but not free I think.

---

### Post by Serpher on 2010-03-24
IMO, it's best to duel boot. When you boot your computer and GRUB comes up, if you partition your hardrive so half of it is Windows and the other half is GRUB Windows will be an option on that list. Also programs are made for specific operating systems. Linux is actually pretty much the only OS that can run other OS's programs using a program called WINE you can install from the Software Center. Right click the .exe then run it in WINE. It doesn't work for everything, or only works a little bit, but it's better than nothing. VMWare if  you can get it working is your best option though. Worst comes to worst, right click the CD in Ubuntu, turn it into a .iso, and drag it into your VM. You can then mount it using DAEMON Tools Lite.

---

### Post by seenthelite on 2010-03-24
I just tried to install software into XP in Virtual Box running on 9.10 64 bit, from a CD  and it worked no problem. It seems that your problem is with your settings or the software you are trying to install.

---

### Post by egalvan on 2010-03-24
> **shaun67 said:**
> I have just recently converted to ubuntu and love the OS it's fast and nice

 but i am having problems as i need to put some software on my pc  that i need..The software is **TIS and AUTODATA**  ...
 
**Ubuntu needs to catch up if it wants to be more user friendly for people like me who need certain programs.**
I was just getting used to it as well

Ubuntu needs to catch up to *what*?

TIS and AUTODATA, which you chose to purchase, clearly state that they require Windows in order to run.

If you need TIS and AUTODATA to run under Linux, then write to the companies that wrote TIS and AUTODATA and ask/demand that they release versions that will run under Linux.
 *They* are the folks who made the decision to support Microsoft, and not support Linux.
*They* are the folks who chose to make their software closed-source/proprietary.
If enough users send in letters stating that they will not buy their products until/unless they run well under Linux, then maybe they *will* release Linux versions.

Or send in a hefty $$ donation to WINE and ask that Wine run TIS and AUTODATA well.


And as you said, Linux runs well, it runs fast, and you like it.

---

### Post by biserbe on 2010-11-25
Run autodata cda3 with  KISO + WINE.  I did not need virtualbox.These are programs for installing autodata
intended for windows in ubuntu

---

