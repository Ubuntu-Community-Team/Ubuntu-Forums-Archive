---
title: "why is it so hard to install 9.04?"
date: 2009-10-21
forum: General Help
---

### Post by beanco on 2009-10-21
So, I have a new lenovo laptop at work.... it came with WIN XP.

So I quickly got the IT guys to give me permission to add anythign I want.... Tehn I went to get ubuntu and I had a ton of problems.

It used to be so much easier....I would just get the CD burned and boot from that, follow instruction and be don eiwth it... now it took me like 15 attempts.

I think I have it installed from the CD and not WUBI.... when it boots up there is a choice of OSes at any rate... now the next thign to do is kill windows... I do not need or want it on my laptop.

so, 1. how do I actually know if I have installed via WUBI or if it is actually on a seperate partition... (yes, I am such a noob that I do not really know what all this means)

2. how to kill XP?

3. Languages... I choose English but there are bits and pieces in Hungarian , like the calender and I do not remember what... how did that happen? How do I fix it?

Thanks

Rob

---

### Post by KeLa on 2009-10-21
1. If you installed wubi in windows then maybe you installed ubuntu via wubi. If you booted from ubuntu cd and installed from there then you didn't use wubi.

2. Never had that effect on linux only on ms windows ;)

---

### Post by PatrickBoyle on 2009-10-21
I recommend starting over again. Boot from the CD and choose install at the menu. Once you get to the partitioning portion, choose the option to use the entire hard drive. This will overwrite your Windows partition and install the GRUB boot loader. Good luck.

---

### Post by DeMus on 2009-10-21
> **PatrickBoyle said:**
> I recommend starting over again. Boot from the CD and choose install at the menu. Once you get to the partitioning portion, choose the option to use the entire hard drive. This will overwrite your Windows partition and install the GRUB boot loader. Good luck.

Will IT be so happy with that? They probably know Windows XP and not Linux.
Do you have to log in to the company network? Or is it more a stand-alone computer?
Will all the software you have to use run on Linux? Ever thought of that?

---

### Post by NightwishFan on 2009-10-21
Generally if the live cd loads, the installed system will work, so you could perhaps go ahead and just use the default partition option to dualboot, or just wipe the disk. Then a single boot Ubuntu system will be installed. Enjoy.

As demus says, make sure you truly have permission.

---

### Post by P4man on 2009-10-21
I dont quite understand how it could be so hard if you managed to do it without knowing how lol.

Anyway, go easy, and keep windows around for a bit longer until you're certain you no longer need it.

As for if you did a wubi install or not; if the screen that allows you to choose the OS has " GNU GRUB" as title, like this:
[http://thegabfather.files.wordpress.com/2008/09/grub4kt.jpg](http://thegabfather.files.wordpress.com/2008/09/grub4kt.jpg)

 then you did a regular install on a dedicated partition (recommended way). 

If not, and its called "windows bootmanager" and looks like this:
[http://i197.photobucket.com/albums/aa76/indyank/techbliss/install-ubuntu-windows.jpg](http://i197.photobucket.com/albums/aa76/indyank/techbliss/install-ubuntu-windows.jpg)

then you did a wubi install.

---

### Post by beanco on 2009-10-21
folks do not worry about IT... i really do not care what they think but I did actually say I want permission to install anythign I want and I do not want MS ... they laughed and said they know that since I hate MS.... and then they gave me the permissions to intall whatever.

I can run remote desktop to log on to the system if I need to... I am not sure how the WiFi thing will work but I cannot imagine that the system handles MS machines only and I know that ther a few mac users who use it, so.....

The head IT guy is the one who was happy when I started running Ubuntu here at home. He helped me when I had problems that I oculd not solve using this forum.

Regarding the install.... I kept getting a menu, 3 points... reboot now, reboot manually later and sg I cannot remember... it was not like the menues I have seen in the past... The machine would not reboot when I chose that option. When I tried the reboot later run in win or sg like that it would ask me to uninstall, then ask  me to make settings... password, username, language, etc... after making these is when it kept stopping and giving me some error message - no I do not know what it said. I forgot to write it down)....

at some point it worked for some reason, the disc popped out and I had ubuntu. I rebooted and had to choose between XP and ubuntu...

Rob

---

### Post by Another Monkey on 2009-10-21
1. Make sure the ISO has been burnt correctly.  Do not burn the ISO to a CD, use it to create a Live CD.
2. Insert CD (if done on different PC)
3. Power off
4. Power on
5. Enter BIOS
6. Make sure that the CD will be used for booting first
6b. [PC will probably power cycle at this point]
7. You should now get a Line menu (black screen, orange/white text) and then very quickly a "menu" asking you to pick a language.
7b. Choose your language
7c. Set the correct keyboard if it is not en-US (F3 or F4, I forget; it's at the bottom)
8. Install Ubuntu (if you are sure the hardware is compatible)
9. You can use the whole disk if you want, there will be a partition manager section that will allow you to erase the "Windows" partition.
10. Once it's done, eject CD, reboot.
11. Login and set up any final language settings.
12. That should be it.

I am pretty new to (I can't even get multi-screen to work!) but the install is usually pretty straight forward.  Thing is to breathe and go slowly.  Oh yeah, and see if anyone else has installed on that laptop.

If in any doubt, try running Ubuntu without making change (default option) and see if it works OK.  Fancy graphics, some WiFi and other "heavy" items won't work like this, but you will get a very good idea if it even possible.

---

### Post by beanco on 2009-10-21
Another Monkey,


Oh, well I get points 2 - to the end... it is point 1 that I am lost on...

how do I make sure the ISO has been burnt correctly?,, or is that what all the other steps will show / prove?

I am sure I burned it since I used Nero and hit iras (hungarian for burn).. so how to creat a live CD?

but why can't I just do all this from the command line, just force it to install or sg? from what I have already installed?

Robi

---

### Post by Iowan on 2009-10-21
I suspect he meant "burn it to a CD - don't COPY it to a CD. Difference being  a bootable CD versus a non-bootable CD with an .iso file on it.
After reported problems with Hardy and Intrepid, I was surprised and pleased with how painless Jaunty installed to my laptop (dual-booted with Vista).

---

### Post by P4man on 2009-10-21
> **beanco said:**
> Another Monkey,

Oh, well I get points 2 - to the end... it is point 1 that I am lost on...

how do I make sure the ISO has been burnt correctly?,, 

Boot from the cd. In the main cd menu there is an option to verify the cd.
If you dont know how to boot from cd have a look here:

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD) 
> 
I am sure I burned it since I used Nero and hit iras (hungarian for burn).. so how to creat a live CD?

Burning the ISO will make a live cd. But the download can be corrupted, the cd medium faulty, your burner flaky.. see above how to verify it was burned successfully.
> 
but why can't I just do all this from the command line, just force it to install or sg? from what I have already installed?

If you really want a command line install, you can download the so called "alternate" iso and burn that.
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by beanco on 2009-10-22
off to work in a minute and I will see whwat I can get done...

Command line install sounds fun to me.

Robi

---

### Post by beanco on 2009-10-22
just checked the link on checking if the CD is burnt correctly,... I do not have an start.exe but I have a wubi.exe file.....

robi

---

### Post by P4man on 2009-10-22
> **beanco said:**
> just checked the link on checking if the CD is burnt correctly,... I do not have an start.exe but I have a wubi.exe file.....

robi

thats ok. The filename has probably just changed since the screenshot was made, but it still  shows you burned the iso correctly (rather than burning a cd with the iso file on it). To really verify if the cd is correct you'd still have to boot from the cd and run the [integrity check.]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

but what is it you actually want to achieve? I believe you got it installed already, so are you having any issues?

---

### Post by MichaelDance on 2009-10-22
I found installing Ubuntu 9.04 berfore i switched to 9.10 easy to install, fast, and really easy to use.

---

### Post by Another Monkey on 2009-10-22
Yes, I mean just don't copy the file on to a CD.  Then all you have is a CD with an .iso on it.

Use the .iso in the CD Software of your choice to make a Live (bootable) CD.

This is usually "Burn image to CD" or something rather than "Copy file to CD".

The guide on the Ubuntu site is pretty good.
[https://help.ubuntu.com/community/LiveCD?action=show&redirect=LiveCd](https://help.ubuntu.com/community/LiveCD?action=show&redirect=LiveCd)
and
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by mechro on 2009-10-22
Check the integrity of your downloaded ISO file and the integrity of your burned CD using md5sum.

How to md5sum...

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Of course you'll need the md5sum to start with...

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)


Edit: Poo! the thread is 2 pages long, not 1. Apologies if I've trod on anybody's toes.

---

### Post by beanco on 2009-10-22
OK,

I have had enough... i have been having too many problems.

What about simply getting the iso, burning a CD on my ubuntu machine at home and then installing that on this machine?

How can I do that?


Robi

---

### Post by mechro on 2009-10-22
> **beanco said:**
> OK,

I have had enough... i have been having too many problems.

What about simply getting the iso, burning a CD on my ubuntu machine at home and then installing that on this machine?

How can I do that?


Robi

Transfer the ISO via flashdrive.

or

Download the ISO from your home machine and burn it.

---

### Post by beanco on 2009-10-22
> **PatrickBoyle said:**
> I recommend starting over again. Boot from the CD and choose install at the menu. Once you get to the partitioning portion, choose the option to use the entire hard drive. This will overwrite your Windows partition and install the GRUB boot loader. Good luck.

so, I just tried this and could not do it... i did not get such menu options.... 


Robi

---

### Post by P4man on 2009-10-22
> **beanco said:**
> OK,

I have had enough... i have been having too many problems.


For the record, the only problem you have outlined so far, is that you have problems. I got no clue what the problem is. Im guessing you havent managed [to set the PC to boot from the CD]("https://help.ubuntu.com/community/BootFromCD#BIOS%20is%20not%20set%20to%20boot%20from%20CD%20or%20DVD%20drive"), but thats only a guess.

No offense mate, but if you find this so hard, I think you should reconsider your plan of wiping windows and jumping in to ubuntu on a corporate laptop. If it turns out your wireless or wired network doesnt work, or you have to set up a VPN or something to access stuff at work, then you'll be in real trouble.

---

### Post by PatrickBoyle on 2009-10-22
> **beanco said:**
> so, I just tried this and could not do it... i did not get such menu options.... 


Robi

I think P4man is correct about your PC not being set to boot from a CD. You need to go into your BIOS and set your boot order to place your CDROM at the top of the list. Every manufacturer has a different key for getting into the BIOS.

Turn on your laptop and try some of the common keys: DEL, ESC, F2, F10, F12. If they don't work, Google your laptop's manufacturer and model to find out.

---

### Post by mechro on 2009-10-22
If only smoking was this hard. I'd never have started!

---

### Post by beanco on 2009-10-22
Ok, I have been rather unclear and I realize that I cannot get much help that way...

SO, there is no need to worry about the corporate aspects of this whole thing.  The IT guys are fine wiht me having ubuntu. They are fine with me killing MS, they just do not have the time to do it for me.


I have installed ubuntu on two other computers successfuly, no major problems.


I will think this through, and try to figure out what I was actually having problems with and write them down....

Thanks for the help so far!

Robi

---

### Post by phillw on 2009-10-22
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)

Will leave you with a nice, dual boot system.

When you're happy everything is working well you can nuke the windows partition and grow you ubuntu partition.

I just shrank my windows partition to a minimum and grew my ubuntu partition. My music files are still on the windows partition, along with all my ISO images, both linux & windows.

Ubuntu has no problems seeing, reading and writing to this area.

You'll know when you're ready to do this, as the thought of doing it will not confuse the living daylights out of you !!!

Just a thought.

Regards,

Phill.
P.S. - One thing I did learn, the hard way, .... When you install ubuntu onto a wi-fi capable laptop - don't have the ethernet lead plugged in - I had 4 attempts before I discovered this, completely by chance !!!

---

