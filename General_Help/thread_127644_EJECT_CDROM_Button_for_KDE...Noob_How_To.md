---
title: "EJECT CDROM Button for KDE...Noob How To"
date: 2006-02-09
forum: General Help
---

### Post by PapaWiskas on 2006-02-09
First off, please don&#8217;t flame me&#8230;.this post is for all the Noobs like myself who find themselves tirelessly searching for ways to make sure we never go back to Bills' World O' Windoze.  With that said, for all of you guys and gals who are experienced please feel free to correct me on any points I made in this post, because I am by no means as good in Linux as the experts that tirelessly help us Noobies day in and day out.

So **THANK YOU** to all of you who contribute to one of the best if not THE BEST linux forums I have ever seen.

I know this has been addressed before in numerous posts, but myself being new to Linux and Ubuntu in general, I have spent a great amount of time reading and sifting through a ton of threads learning how to do things.  So I thought I would write this for some fellow Noobs like myself.  I generally use XFCE, just because I like it.  However I do use Gnome quite a bit, and recently started using KDE over the last few days, trying to give it a chance, because I never really have liked the look and feel of it.  I am finding KDE not so bad.  I use a laptop, and being a windows user for so long I am used to things like being able to eject my cdrom by pushing a button.

I know there is a fix for that, but I tried that command and for some reason it did not work for me.
So I created an icon that does it for me, it comes from another post out there with an explanation by quonsar- his post can be found here [http://www.ubuntuforums.org/showthread.php?t=115499&page=2&highlight=eject+cdrom](http://www.ubuntuforums.org/showthread.php?t=115499&page=2&highlight=eject+cdrom), so I thought I would write up how I did it for all the Noobs like me.

Right click on your K Menu Icon (similar to Start Windoze button)  and choose Menu Editor.  Menu Editor will come up with all your categories and programs listing.  Click on File and choose New Item, give it a name, I called mine Eject CDRom.

Once that is created you see some areas to fill in on your right hand side, you will only need to edit a few of them.  First thing I did is drag the new item I just created and dropped it down to the very bottom of the list, that way when you click on the K Menu icon (similar to Start Windoze button) it will be right there at the bottom.

As for the fields to the right, Name will already be filled in.  The icon graphic you can change to whatever you want.

In the command field I typed in the following

/usr/bin/eject

I left the two check boxes below it unchecked.  (side note&#8230;.I intially or it was by default checked off on Enable launch feedback&#8230;this caused a bouncing icon for awhile after clicking my Eject CDRom icon, not sure what this means or does, but it annoyed me, so I unchecked the box and it doesn&#8217;t do that anymore)

Not sure if I needed the next part or not but in the Work path I just put my home directory path&#8230;in this case..

/home/papawiskas <---you will need to change this value to whatever your home path name is-->

Then what I thought was pretty cool is the Current shortcut key, if you click on that icon it will let you set a hot key for executing this command.  My key is set to the ` key, or the one with the tilde as some people call it.

Once you have done all this and close Menu Editor it will ask you to save the changes.  So save it.

So now if you click on your K Menu icon (Start Button for Windoze converts) you will see a icon called Eject CDRom

I took this a step further and added it to my panel of quick launch apps&#8230;.to do this you simply can do this two ways that I know of&#8230;.

Right click on your panel, choose panel menu, then Add to Panel, then Application, your Menu listings should come up, and if you dragged it to the bottom like I did it will be in your list, just click on it and it will add to your panel.

Or you can click on your K Menu icon, find your Eject CDRom icon, right click on it and choose Add item to Main Panel Menu, and there you go.

Again my thanks to quonsar for posting that graphic, it made the world of difference to me.  Also ejecting the CDRom was a major hurdle for my wife, whom I will be movning over to Linux soon.  She does not have any interest in learning commands.  She just wants to be able to use her computer&#8230;..so thanks to all of you and quonsar&#8230;.I just found a way to make it easier on her&#8230;.and when its easier for her, its easier on me.

Best Regards to you all.

PapaWiskas

---

### Post by MJoshi on 2006-02-09
That was a great post *PapaWiskas*.  It's good to read such posts from other newb's who have managed to get someothing to work and give detailed instructions on what to do.

Does the same shorcut key also close the C.D drawer?

---

### Post by GeneralZod on 2006-02-09
I always like having the Storage Media applet enabled; when a CD is placed in the drive, it appears on the panel and you can eject it by right-clicking on the icon and choosing "eject".

[http://etotheipiplusone.com/kde-cd-eject.png](http://etotheipiplusone.com/kde-cd-eject.png)

Your wife might like this solution as it also deals with e.g. USB Pen drives.

Edit:

666th post! :twisted:

---

### Post by PapaWiskas on 2006-02-09
[QUOTE=MJoshi]That was a great post *PapaWiskas*.  It's good to read such posts from other newb's who have managed to get someothing to work and give detailed instructions on what to do.

Does the same shorcut key also close the C.D drawer?[/QUOTE]


For me it doesn't.  I have done this on my laptop, so you have to manually close the disc tray.  Not sure about a tower pc yet, I am in the process of buidling our new one over the next couple of weeks.  If it dont close the drawer, she can just push it closed I assume.  Haven't gotten that far yet, so I can't elaborate at this time.

---

### Post by PapaWiskas on 2006-02-09
> **GeneralZod]I always like having the Storage Media applet enabled said:**
> http://etotheipiplusone.com/kde-cd-eject.png[/url]

Your wife might like this solution as it also deals with e.g. USB Pen drives.

Edit:

666th post! :twisted:

Hey GeneralZodd thanks for the tip.  I just added that to my Panel as well, that is freakin sweet.\\:D/ \\:D/ 

The goal of my post was to just get the darn cdrom to eject so I could get discs into the tray, since my button didnt work, LOL.

---

### Post by Jucato on 2006-02-09
I know it's a bit frustrating not having your eject button to work when you want it to. But I think it's good that it was implemented this way, and that it needs a sort of paradigm shift away from how Windows works. The reason for this is simple: you shouldn't eject your CD-ROM unless you are absolutely sure that the system is not reading from it. And what better way to make sure than to let the system itself eject the CD for you? Of course if your GUI hangs up, then a CLI alternative can be used.

Another possible option, besides the one mentioned by GeneralZod, is to enable mounted CD-ROMs to be displayed on your desktop, so that everytime a CD-ROM is put in, an icon will appear on your desktop, w/c you can right-click and choose to eject.

---

### Post by PapaWiskas on 2006-02-09
I can not argue the fact that having the icon show up on the desktop "AFTER" you put a cd in it.  That portion has always worked for me without a hitch.

My problem was simply being able to open my CDROM in the first place in KDE.

There was no way for me to do this in KDE until I did the above mentioned.  Unless of course if I wanted to go through the command or terminal and used the eject command.  It's just easier with an icon, so I guess, yeah, Windoze spoiled us in that sense.  I have no problem with the way Linux is set up with regards to opening the CDROM tray, its no big deal that I cant use the button, heck I created an icon to do it for me, no biggie.

---

### Post by Hiroshima on 2006-07-08
Thanks for the eject button!  Hurray for the eject button!  Seriously though,I am really happy with your solution.  I could open my CD tray with the physical CD button, but then it wouldn't close again.  Now I can use your icon to open and the button to close.  Thanks for the solution, you have saved me a lot of hassle (and my wife too... how is it that our wives are getting dragged into this?)

Cheers,
Hiroshima

---

### Post by PapaWiskas on 2006-07-09
Glad it helped you out!:)

---

