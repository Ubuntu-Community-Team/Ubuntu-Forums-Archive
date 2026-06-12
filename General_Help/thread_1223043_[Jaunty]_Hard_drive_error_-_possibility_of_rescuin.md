---
title: "[Jaunty] Hard drive error - possibility of rescuing files?"
date: 2009-07-25
forum: General Help
---

### Post by ajpfox on 2009-07-25
Hey all, I really hope someone out there can help me.

I installed Jaunty Jackalope on my Dell Insipron 2200 a while ago when windows xp sp2 crashed on me and some essential system files got corrupted.  Luckily I was able to boot into windows again with an xp cd, recover my data and then format the hard disk for the ubuntu install.  things were going great until just the other day my system wasa struggline (its an old machine) so I shut it down while I ate lunch.  Much to my surprise, an hour later when I reutrned and powered the machine back on, I was unable to boot into Jaunty.  

The normal start sequence begins, but at the Ubuntu splash screen, suddenly I am taken to a screen with lines of code.  I will try and update with what the error is momentarily - theres alot so I may not be able to get it all (and if there is a way I can make it print the error out to a USB for example, please let me know and I'll furnish that).  I'd really hate to have to type it all in...

The point is, I know have a system I cannot boot into for whatever reason.  My campus IT told me the hard disk itself is ok, so I'm hoping just the file system got corrupted somewhere.


So, I ask you Ubuntu guru's of the world, how can I attempt to recvoer any of my data from this system?  Keep in mind I can't boot into it at all.  I found programs like the "ubuntu rescue remix" but I'm unsure how to go about using it, or if thats even what I want to use.  Also, whats the best way to create an "ubuntu rescue remix" bootable USB?  

If there is a program out there that could simply read the disk and allow me to pull some files from the old hard drive to an external that would be miraculous - does such a thing exist?

Please help!  I'm currently using Vista from a friends laptop to try and get this sorted out, if that at all matters.  

Thanks!

---

### Post by merlinus on 2009-07-25
testdisk and photorec.

---

### Post by ajpfox on 2009-07-25
That looks good.  Is it possible you can guide me through or at least give me some hints on how to use the program?  Well, maybe not so much as use it but seing as I can't install it on my Linux system, how do I make a boot USB or CD with this program on it?  Thanks for your help!

---

### Post by merlinus on 2009-07-25
You can download them as .iso or .exe files, burn to a cd, and boot from it.

User guides and screeenshots are available at the website:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by ajpfox on 2009-07-28
Again, thanks for your help, sorry for all the questions.  I just want to make sure I'm doing this right.

On my windows PC, I need to download the Photorec / Testdisk files that are compatible with my Ubuntu Jaunty system right?  Those files are in the form of a tar.bz.  I'm unfamiliar with thi format, do I just burn it to a disk as an image file?  Should I need to extract anything from the archive first?  Thanks again!

---

### Post by hessiess on 2009-07-28
Boot the ubuntu live cd, and run fsck on the bad drive. As you have had problems with the drive once when your XP system got damaged, you should hav taken that as a sighn that the drive was going bad, replace the drive ASAP.

Also when you have the live cd running, can you post the output of

```

df

```

---

### Post by az on 2009-07-28
> **ajpfox said:**
> 
If there is a program out there that could simply read the disk and allow me to pull some files from the old hard drive to an external that would be miraculous - does such a thing exist?


Well, if the drive is intact, then the live cd should allow you to boot and try to mount the file system.  If the problem only affects a few files, then you will be able to dran and drop the intact files you need to another hard drive.

If you run into problems because the disk is not intact, you need to image the disk.  Use gddrescue to do that.  Once you have an image, you can either mount it as if it were a real disk (and read the files without any problem), or extract files from it if the image is too badly damaged to mount it.

Ubuntu-rescue-remix is both a bunch of packages and a live cd.  If you have an Ubuntu live cd with internet access, you can just install the ubuntu-rescue-remix-tools metapackage instead of creating another live cd or USB.

See here about installing the metapackage and finding further information on data recovery:
[http://ubuntu-rescue-remix.org/node/149](http://ubuntu-rescue-remix.org/node/149)

---

### Post by ajpfox on 2009-07-28
Hey again.  I created an ubuntu-recsue-remix liveCD.  Unfortunately, even trying to boot from this yields the same error. I get to the rescuse remix splash screen and any option I take from there leads me to the same problem.  So, I'm guessing my next step is to image the drive?

Ok so...how do I do that?  I know the rescue remix has photorec in the bundle, so what I need to know now is how do I use it from the "boot" prompt in the rescue-remix splash screen.  I have only a basic understanding of commands to use from linux terminals, so anykind of step by sstep walkthrough would be great.

Additionally, if there a way I can only image part of the drive?  Or perhaps just a specific folder or file?  Additionally, where does the image get saved?  If I hookup a usb or external harddrive to my machine, will I be able to copy the hd image (or hopefully image of just the necessary folders) to those external devices?  Does that require some fancy commands as well or is it something simple like drag and drop?  

Thanks again!

---

### Post by sefs on 2009-07-28
Hi, I believe the compnents you will need are 

1) A live CD (ubuntu live cd should do)

2) gddrescue (you install from the repos after booting live cd)

3) an external drive with enough space to hold your image

gddrescue will try to grab the good sections of your disk first and then work over any bad sectors which can takes hours/days/weeks/years. It will mostlikey  give you like a drive map that can show progress so when you take a look at it and most of it seems to be processed you can ctrl-C to stop it (so you dont wait ages for bad sectors to be processed) and work with the image file to see what you can retrieve.

So from the command line in your live environment make sure your "bad" disk is not mounted and your usb drive is

lets say your bad disk is /dev/hda and your ubuntu is on /dev/hda1  and your usb partiton is mounted to /media/disk in the live environment you can go

```

ddrescue /dev/hda1 /media/disk/mybadubuntu.img

```

When all that is done make a backup of that img if you have space so you can play with the orignal image you made (in other words back up the back up just to be safe) in case something goes wrong with it while you play.

then you can use install testdisk 
and use photorec to retrive all the files it can find by following this tutorial...

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Update:

Now that I think of it photorec only tries to recover deleted files, which is not exactly what you want, I think there is an option though to retrieve more than just deleted files, it may very well be mentioned in that tutorial, so be sure to look out for that, otherwise you will need another tool to search the image for files.

Update 2:
pay attention to section titled "Carve the partition or unallocated space only" in the tutorial listed.  That should get you going.

---

### Post by ajpfox on 2009-07-28
@ sefs: Thanks for the great walkthrough!  However, I cannot boot into anything.  Using my Ubuntu LiveCD or my ubuntu-rescue-remix LiveCD I still can't boot into my system.  Unless I don't understand what an ubuntu liveCD is...I thought it was the same / similar as the cd I downloaded and burned to originally install ubuntu.  If its different could you like me to the proper liveCD download site?  

Again this all sounds great, but I can't get past the boot splash screen at the moment.  Either I'm doing something wrong, or I'm going to need a tool I can boot into WITHOUT starting the operating system proper (or something that can scan and fix issues from boot)...


Update:  After more careful examination I realized that after selecting "start the default live system" after selecting to boot from the ubuntu-rescue-remix cd, my system is merely reseting back to the opening Dell screen.  It boots /casper/vmlinuxl and /casper/initrd.gz and then resets, so I'm not getting anywhere...is there a possibility somethings wrong with my rescue remix live cd?

---

### Post by sefs on 2009-07-28
...or maybe you have a hardware failure somewhere, try to run the memtest on your system and see if it completes successfully.  Is this laptop fully charged? Are you doing this while plugged in?  Do you have any type of alternative boot media like a windows install disk? or a usb that boots to dos, to test if this is more a hardware problem.

---

### Post by ajpfox on 2009-07-28
I thought of that.  I took it to my campus IT department who did "something" and reported that the hardware was fine, but they are unfamiliar with linux so they didn't know how to recover any of my files - which is why I've turned to the forums here.  The error is some kind of ext3 file system error, it can't reference some blocks.  

I realize now I didn't even try to explain what this error was.  Basically GRUG loads up fine, and the Ubuntu splash then loads.  After a few seconds, the screen changes to white text on black and the error keeps repeating - can't access /dev/sda1/, ext3 fs error can't read inode at blocks ###- ### and then finally the grand finally is the whole "kernel panic - attempted to kill init" error.  Not sure this helps you all.  If there is a way to generate a file and maybe save it as text to a usb I'd do it and show you, but no one has been able to tell me how to do that without being able to boot into the system.

Hope this helps teast out a better answer...let me know what else I can do!

---

### Post by sefs on 2009-07-28
I am wondering if you are trying to boot from CD but your bios is not set with the CD as the 1st or 2nd boot device or once it is set to boot before your HD.

Because I am stumped, as to why booting from a CD unless the CD is damaged you would get the same error as you would get when you boot into your HD.

Can you verify that in your bios the boot order is such that the CD comes before the HD.

---

### Post by hamstersquasher on 2009-07-28
After you finish with the data recovery, I would recommend that you run manufacturer diagnostics on the HDD before tossing it out.  Manufacturers' websites usually have a means for you to create a bootable CD or floppy to run diagnostics on your drive.

---

### Post by Coder543 on 2009-07-28
If Ubuntu corrupted in less than 3 days, it sounds like a faulty hard disk.

---

### Post by ajpfox on 2009-07-28
I had ubuntu installed for awhile.  Not a long time, but more then 3 days.  Though I do not doubt the HD may be on its last legs (its an older machine after all), I still think if I could just get in there I could salvage what I need.  Then it can go quietly into that good night.

I can verify that the boot order in the bios is CD and then HDD.  Originally I was hitting f12 in the dell startup after switching on the power, but that became tedious, so I switched the order myself.  The problem is, after selecting the "boot from LiveCD" command, both on the Ubuntu LiveCD and the Ubuntu-rescue-remix LiveCD, the system resets back to the Dell startup screen - as if it had been powered off and then back on.  The system then boots into whatever is number one in the bios.  Effectively, now that I selected the CD as the primary boot location I've created and endless loop. The system will boot into the ubuntu-rescue-remix splash screen, I hit "boot into default liveCD" it resets and boots into the ubuntu-rescue-remix splash screen ad infinitum...

The question now is why won't it actually boot from the CD?  

I'm wondering if perhaps there is a problem with the CD or the optical drive.  I'd like to try and use a bootable USB, but I'm unsure of how to create one for Linux using my Vista notebook.  If anyone has a step-by-step guide of how to do so, that would be my next step I suppose.  Unless anyone can recommend another rescueCD that may be of more help?  Possibly one that can run straight from the disk without having to boot anything and I can just select which folders I want and copy them to an external HD?  Does such a thing even exist??

---

### Post by sefs on 2009-07-29
What you may also try to do, is totally disconnecting the HD from the computer and try booting with the CD as the only attached media.  

If it still does not boot then something is wrong with your computer hardware or  your CD.

---

