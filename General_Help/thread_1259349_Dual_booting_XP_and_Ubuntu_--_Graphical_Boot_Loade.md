---
title: "Dual booting XP and Ubuntu -- Graphical Boot Loader options?"
date: 2009-09-06
forum: General Help
---

### Post by artemenko on 2009-09-06
Listen to me, I can say "boot loader" and have some idea what it means! Oh well, I still have a LONG way to go.

Yesterday, I used gparted to shrink my Ubuntu partition down to make room for a smaller XP partition.

Research on these forums and this other tutorial in particular helped a lot:
[http://bit.ly/DnmHd](http://bit.ly/DnmHd)

Why go "back" to XP?  I missed CS: Source and need to use Dreamweaver to update my blog.  I've tried Wine and virtualization, but I wanted to learn how to dual boot.  Besides, this thread isn't really an invitation to a performance discussion.

I really just tried a dual boot setup to see if I could.

Now I am wondering, is there a graphical boot loader so I can actually select my OS from a menu?

Right now, Ubuntu loads by default.  Otherwise, I have to quickly hit "escape" when grub is loading up to get a menu with 4-5 Ubuntu options and then XP sitting at the bottom.

Did a Google search and found some pretty ugly options and an alternate splash image in grub?

Are there more elegant solutions available, so say, another user could easily switch the two without me explaining the "you have to quickly hit escape" method?  :redface:

---

### Post by mike555 on 2009-09-06
I use " GAG" it lets me boot up to nine OS's , it's free and easy to set up ........   [http://gag.sourceforge.net/](http://gag.sourceforge.net/)   ... just remember to install grub to the partition your installing Ubuntu to (not the MBR)then install GAG and it will automatically pick up your Windows and Linux partitions (even .ext4)and let you ad them to the boot menu and set a time for the main one....... it's especially good if you install a bunch of different os's .

---

### Post by thunk77 on 2009-09-06
You can edit your grub bootloader options by editing a file called menu.lst which is located at /boot/grub

It's a text file so fire up a terminal and issue

```
sudo gedit /boot/grub/menu.lst
```

Options are well explained and you shouldn't have any problems, however:

If you don't want to have to hit escape every time uncomment the last line

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu 
```

If you need more hand holding just give a shout :P

---

### Post by artemenko on 2009-09-06
> f you need more hand holding just give a shout

Well, you offered! =)

Downloaded ver. 4.1 of GAG and in the zip is a "Docs" area with an HTML tutorial.  It begins by saying:

> If you have an operating system which needs a boot loader (like Linux or BSD, which needs GRUB), you must install it in the SuperBlock of the root partition.

What does that mean?  Do I need to install Grub first (again? I thought I already had it?)

Next, the GAG guide says...

> Just open the **Linux** folder and run (as root) the script **copy-files.sh**. It will copy the linux installer and other needed files in /boot/gag. Now you can use **gag-install** to install gag in your hard disk, passing as parameter the device where you want to install it.


Seems easy enough

> Example: if **/dev/sda** is your boot hard disk, then you must use:
       sudo gag-install /dev/sda


OK dev/sda is me... and Ubuntu is /sda1 and XP is /sda2

Before I get started, anything I can break by doing this?  Not sure about installing the whole grub thing again...

---

### Post by Graham1 on 2009-09-06
Another graphical boot loader you could try is XOSL ([http://www2.arnes.si/~fkomar/xosl.org](http://www2.arnes.si/~fkomar/xosl.org)). Just install XOSL to the MBR but you will need to re-install GRUB to it's own (i.e Ubuntu's) partition. I use this setup on my main computer (Ubuntu and XP) and 2 tablets (Fedora, openSUSE, Ubuntu and Linux Mint, XP).

:)

---

### Post by artemenko on 2009-09-06
0

---

### Post by artemenko on 2009-09-06
OK Gag is up and running.  I now have cool icons (in retro 90's quality) for Windows and Linux.

I also have a few problems.

First, I'll tell you what I did:

Installed Grub in my Ubuntu partition:

> sudo grub-install /dev/sda1

Then dropped the folder from the GAG zip archive into my "home" folder (my computer's name is office)

> cd /home/office/gag4.10/linux

> sudo gag-install /dev/sda

Hit restart and Boom!  I have been GAGified.

Linux starts up fine...  but XP just hangs at the intro screen.  I get the progress bars moving horizontally then blue with the XP icon... forever.

Did I break something with XP?  :confused:

---

### Post by kronos262 on 2009-09-07
> **artemenko said:**
> OK Gag is up and running. I now have cool icons (in retro 90's quality) for Windows and Linux.
 
I also have a few problems.
 
First, I'll tell you what I did:
 
Installed Grub in my Ubuntu partition:
 
 
 
Then dropped the folder from the GAG zip archive into my "home" folder (my computer's name is office)
 
 
 
 
 
Hit restart and Boom! I have been GAGified.
 
Linux starts up fine... but XP just hangs at the intro screen. I get the progress bars moving horizontally then blue with the XP icon... forever.
 
Did I break something with XP? :confused:
 
I did the install and everything, and I get no graphical interface at all just the grub.
 
it said gag was sucessfull but don't forget to reinstall grub, which i did, but something tells me that probably overrode gag. Any ideas?

---

### Post by artemenko on 2009-09-07
> I did the install and everything, and I get no graphical interface at all just the grub.

Hmm -- not sure about that. Here is the thread that helped me install GAG:

[http://ubuntuforums.org/showthread.php?t=932081](http://ubuntuforums.org/showthread.php?t=932081)

It *seemed* to work perfectly.  In that I assigned names and icons to each of my OS's (Ubuntu and XP).

Ubuntu booted from grub just fine, but XP seems totally borked.

It hangs on the welcome screen, won't go into safe mode.  I can't repair it from CD in the repair console (tried "fixmbr" and fixboot" commands).

And oh yeah, typing "fixmbr" into the Windows XP repair console killed GAG.

So now I have erased all of my progress.  Just have Ubuntu, and a dead version of XP without GAG.   So I guess learn from me and be careful.

Maybe a nifty graphical boot manager isn't worth the trouble...  because before I started down this path I had both Ubuntu and XP working just fine without GAG.

---

### Post by Graham1 on 2009-09-07
Sorry, forgot to mention in my earlier post that you need a FAT32 partition to install XOSL to. I set aside 100MB which is ample (it only really needs a couple of MB). Once XOSL is installed to MBR (Master Boot Record) you can then select your OS's to boot (probably similar to GAG, although I've never used this program).

:)

---

### Post by artemenko on 2009-09-07
Yeah I'm through with GAG.  I've got both OS's working separately now.

Seems like a ton of work to avoid hitting "Escape" when Grub is loading and selecting XP.

I wonder if the solution is just enhancing the Grub loader like this?

[http://grub.gibibit.com/About](http://grub.gibibit.com/About)

Surprised no one mentioned this before...

---

### Post by kronos262 on 2009-09-07
> **artemenko said:**
> Yeah I'm through with GAG. I've got both OS's working separately now.
 
Seems like a ton of work to avoid hitting "Escape" when Grub is loading and selecting XP.
 
I wonder if the solution is just enhancing the Grub loader like this?
 
[http://grub.gibibit.com/About](http://grub.gibibit.com/About)
 
Surprised no one mentioned this before...
 
 
have you tried that yet?

---

### Post by egalvan on 2009-09-07
> **artemenko said:**
> Yeah I'm through with GAG.  I've got both OS's working separately now.

[B]Seems like a ton of work to avoid hitting "Escape" when Grub is loading and selecting XP.
[/B]
I wonder if the solution is just enhancing the Grub loader like this?

[http://grub.gibibit.com/About](http://grub.gibibit.com/About)

Surprised no one mentioned this before...

First, that link is refering to GRUB 2, not the GRUB legacy which you are using now.

Next, avoiding the "escape" is extremely simple.

Making XP the default is also extremely simlpe.

Use StartUpManager, found under 

System -> Administration

note... if not there, then use Synaptic to install it.

Everything StarUpManager can do, can also be done by editing /boot/grub/menu.lst...
but StartUpManager is much easier to use, and much less prone to errors.

but if you want to be bold and edit the menu.lst to remove the need for "escape", then let us know.

---

### Post by artemenko on 2009-09-08
>  
Everything StarUpManager can do, can also be done by editing /boot/grub/menu.lst...

 
Thanks egalvan, I like the way you think.
 
I was able to obtain Startup Manager.  Ideally, I'd like to do the following:
 
[LIST=1]
[*]Make it so the computer goes to the Grub OS selection first, not diving straight into Ubuntu
[*]Hide some of the OS choices like "memtest" and just have (2) selections for Ubuntu and XP
[*]Have a nice background image or font to display the choices.  This is completely for form rather than function.  However I'm stubborn and I originally set out to have a graphical boot menu and I'm still working on that challenge :)
[/LIST] 
Can Startup Manager do all of this?  Maybe do more?  There appear to be "themes" for Grub, but Startup Manager does not come with any pre-loaded.

---

### Post by egalvan on 2009-09-08
> **artemenko said:**
> Thanks egalvan, I like the way you think.
 
I was able to obtain Startup Manager.
I'd like to do the following:
 
[LIST=1]
[*]Make it so the computer goes to the Grub OS selection first, not diving straight into Ubuntu
[*]Hide some of the OS choices like "memtest" and just have (2) selections for Ubuntu and XP
[*]Have a nice background image or font to display the choices.  This is completely for form rather than function.  However I'm stubborn and I originally set out to have a graphical boot menu and I'm still working on that challenge :)
[/LIST] 
Can Startup Manager do all of this?  Maybe do more?  There appear to be "themes" for Grub, but Startup Manager does not come with any pre-loaded.

#1 is covered in the first tab "Boot options"

#2 is covered in the fourth tab "Advanced"

#3 is covered in the second tab "Appearance"

Also, herman has a good website (hermanzone) that has excellent GRUB info. It's where I started learning GRUB & menu.lst.

There is a web site devoted to GRUB splash stuff, but I don't recal it at the moment. "Google is Your Friend" here.

For even fancier GRUB stuff, I have played around with the GRUB menu.lst from several LiveCD, such as SuperGRUB and PartedMagic.LiveCD

---

### Post by artemenko on 2009-09-08
> "Google is Your Friend" here.It sure is...  particularly Google Images.  Since Grub backgrounds are limited to 14 colors, I highly recommend searching for "pixel art" images, which can be beautiful without having too many colors.

Thanks to this tutorial:
[http://maketecheasier.com/create-and-install-your-own-grub-splash-image/2009/01/27](http://maketecheasier.com/create-and-install-your-own-grub-splash-image/2009/01/27)

And this image:
(credit to [Yuriy Gusev]("http://pixeljoint.com/p/6741.htm") of Pixel Joint)

[http://pixeljoint.com/files/icons/full/isocastle.png](http://pixeljoint.com/files/icons/full/isocastle.png)

And egalvan's help with StartUp-Manager I now have a cool new graphical boot loader:

[[IMG]http://artemenko.org/grub_loader_background_sm.jpg[/IMG]]("http://artemenko.org/grub_loader_background.jpg")

[URL="http://artemenko.org/grub_loader_background.jpg"]Link to large image
[/URL]

---

### Post by egalvan on 2009-09-09
> **artemenko said:**
> I now have a cool new graphical boot loader:


Excellent! You can be proud of the work you have done!

Now all you have to do is type up EXACTLY what you did, in detail, with screen-shots,
and post it on the "tips and Tricks" section!

have at it!   :lolflag:

ErnestG

---

