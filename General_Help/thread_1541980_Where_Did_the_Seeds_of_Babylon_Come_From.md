---
title: "Where Did the Seeds of Babylon Come From?"
date: 2010-07-29
forum: General Help
---

### Post by oldefoxx on 2010-07-29
My wife' Asus desktop, which was set up with Ubuntu 10.04 LTS, has just puked its guts up, software-wise that is.  I was walking her through the steps of getting photos placed in an image to burn to a CD, and she wanted to look at them just to be sure they were right.  She had scores of things to view photos with, but most were empty duplicates that did not connect up with an actal application.  A significant one that had just gone away was Irfanview, written for Windows, but usable under wine 1.2 which as also installed.  But go to wine in the menu, it only had one listing below it, which was Programs,  Under programs there was just one listing as well, which was Babylon.

Babylon?  I know the original story, butr this is something I knew nothing about.. Where it came from and what it was were unknown to me.  Unknown to the package manager and apt-get as well, as efforts to remove it were futile.  So I decided to rid myself of wine first, only efforts to do that still left it in the Menu as it was.  apt-get got rid of it once, and then no further matches.  Again, Babylon was not found to be gotten rid of.

Finally, to try and force some recognition, I started shortening the possible package name letter by letter, with an asterick at the end.  I got a huge removal effort from apt-get when I got down to Baby*.  I had to try it, because nothing else presented itself as an alternative.  That is when I found I could no longer bring the system up.

You know that supposed Recovery option that shows up as an alternative boot mode in grub?  Most times it does nothing to help, but this time it got me back to the login screen, and the user names showed up.  But apparently the passwords were gone, because nothing I entered got me back into the system.  I would have tried 'root' too, but you know how secretive the Ubuntu people are about that one.

At this point I would have to say that Ubuntu does not have a valid recovery and restore option, unless you somehow got it into a backup image that is still on hand, and not so dated that it will undo recent efforts at getting work done.

I could just re-install Ubuntu 10.04 LTS, but it has its own way of making up its mind which present install of /home to use, and if the one it goes for has any contrary config settings, I just go from one bad situation to another.  I could just install from scratch by formatitng the parition as well, but then there goes all files and settings from the previous install, and that does not prevent the installer from still seeking out a /home on this or other partition.  And again, if the config setting are way off, I will still be hosed up.

I am currently up an running under a fallback install of 9.04, but I will likely have to revert to the use of a LiveCD so that I can protect the /home folder that goes with this install by putting it and all its contents under a new folder I will call /hold

You know, you come right down to it, and Ubuntu's way in these matters is hardly any imporvement over the way Windows has done it from the beginning, which goes back over a decade.  You hear lots of praise for Linux when it comes to running without interruption for long periods, but nobody talks abut what happens after something goes wrong.  Except me, that is.  I figure every OS demands a decent backup and recovery plan to be in place and workable.

Before posting this thread, I decided to use a second tab to search out the terms Ubuntu Wine Babylon.  It turns out that this is some damn silly game that some people want to run under wine.  Fine, that explains what it is, but not how it got on my wife's PC.  Nobody else uses her machine except me, and I am not into gaming.  For her, Spyder Solitare or Mah-Jongg are the limit.  But she does visit a variety of embroidery sites, and who knows what lurks behind those doors.

---

### Post by ubunterooster on 2010-07-29
Babylon, being a wine program, is not found by synaptic or apt-get pruge ```

**Uninstalling Wine Applications**

 Open up a terminal window and type the command below. 

[COLOR=MediumTurquoise]uninstaller[/COLOR]

What this will do is open up a program similar to the Windows **add/remove programs** 
 control panel, allowing you to uninstall applications from a Wine  installation.  Running
 uninstall programs directly via Wine should also  work normally.  Alternatively, you could 
also simply delete the folder  of the application.  However, as when done in Windows, this 
method will  be **unclean** and will not remove the program's configuration from the Wine
 registry like using an uninstaller will. If the command **uninstaller** results in an error 
message try the following command instead. 
[COLOR=Cyan]
wine uninstaller[/COLOR]
```by removing all those files, it seems you instead roved system files. The simplest 
option is to reinstall, but for backups and restoring, see  [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by hansdown on 2010-07-29
Hi oldefoxx.

Babylon is a windows dictionary.

It is also a trojan, that masquerades as this program.

[http://www.file.net/process/babylon.exe.html](http://www.file.net/process/babylon.exe.html)

The full search results are here.

[http://www.google.com/search?client=ubuntu&channel=fs&q=windows+Babylon&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=windows+Babylon&ie=utf-8&oe=utf-8)

ubunterooster has some good advice.

---

### Post by oldefoxx on 2010-08-07
Folks, I am ever appreciative of replies, good advice, and some insight as to what is going on.  I got several this time.  My delay in replying is that it often takes me days to come back and check threads for possible answers.  I'm all there is for keeping a good range of PCs going, and once you tackle a PC a PC repair job, you are stuck until you have results of some sort.

That spate of lightning the other day not only killed my sister-in-law's and her husband's PCs, but it apparently damaged the circuits in the KVM switch I use here to tie two desktops to the same monitor, keyboard, and mouse.  I did not catch this right away, as I was then focused on my wife's PC and making use of my laptop. When I caught it, the real decision was which replacement to buy.

I will tell you honestly, I could not quite make up my mind, so I ended up ordering 3 different ones, and finding good prices on each.  One was a PS/2 model exactly like the one lost, because it is really an excellent performer and a bargain.  The next one, also from IOGear, supports USB rather than PS/2, and can have several uses includng dealing with both a USB keyboard and mouse.  The third, from another OEM, does 4-to-1, not just 2-to-1, so adds to my setup choices.  The IOGear models come with the necessary cables and connectors all formed in, which I like, and work very well.  Oh, and the IOGear switches work on any PC, regardless of the operating systems involved. Hard to beat.  Thought it worth the mention.

---

