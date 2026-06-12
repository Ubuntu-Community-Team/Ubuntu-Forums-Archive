---
title: "Trouble using wine"
date: 2006-01-24
forum: General Help
---

### Post by Piggah on 2006-01-24
Hi, I just installed wine 0.9.6 and I'm having some trouble. 

I ran winecfg as directed, but I'm lost after this point. 

The main and pretty much only thing I wish to run is Photo Shop 7, which is installed on my windows partition. 

I tried to add it through winecfg, but I'm lost with that as it doesnt appear. Do I need to bring my Photoshop folder over to Linux rather than accessing it through  Linux? 

Also, is there a wine application I should be able to access through the menu, or just winecfg? 

I tried to find a detailed guide on using wine, but none turned up. So if anyone just wants to point me in the direction of a place that could answer my questions I'd appreciate that as well.

Thanks in advance. :)

---

### Post by RAOF on 2006-01-24
Try installing it in wine.  To run something in wine you should be able to just double-click on the executable (in this case it'd be setup.exe or the like).  Running it from a console (with wine <nameofthing>.exe) will give you any error messages it generates, though.  They can be useful if it doesn't actually work :)

---

### Post by Piggah on 2006-01-24
Ok, so in that case, I will have to bring it over? Because nothing useful appears when I browse. :p 


thanks

---

### Post by RAOF on 2006-01-24
[QUOTE=Piggah]Ok, so in that case, I will have to bring it over? Because nothing useful appears when I browse. :p 


thanks[/QUOTE]
Um, when you browse **where**? ;)

Just stick in the Photoshop install CD, open it, & click on "setup.exe" or whatever it uses.

Alternatively, you could **try** copying the Photoshop directory to ~/.wine/drive_c/Program Files/.  That's where wine puts the things you install.  However, this won't work if the photoshop installer does anything but copy files into that directory - if it installs anything into the windows directory, sets up some registry stuff, whatever, just copying the folder won't work.

---

### Post by Piggah on 2006-01-24
Yes, well, it's not from a CD. 

When I try to run the .exe it says that it "cant display" it. And when I try to open it with wine, it doesn't appear on the menu.

---

### Post by RAOF on 2006-01-24
[QUOTE=Piggah]Yes, well, it's not from a CD. 

When I try to run the .exe it says that it "cant display" it. And when I try to open it with wine, it doesn't appear on the menu.[/QUOTE]
Ok, then let's try option 2 - the console.  Open up a terminal, cd to where you've got either 1) Photoshop installed or 2) An installer for photoshop.  Then run ```
wine theprogram.exe
```obviously replacing "theprogram.exe" with the actual name of the program.  See what happens.

When you say "doesn't appear on the menu", do you mean in the Applications menu?  'Cause it won't - you'll need to do a bit of fiddling to do that.

---

### Post by Piggah on 2006-01-24
Ok, that worked and it installed Photoshop.

But, how do I run Photoshop now? 

Thanks for the help :)

---

### Post by RAOF on 2006-01-24
[QUOTE=Piggah]Ok, that worked and it installed Photoshop.

But, how do I run Photoshop now? 

Thanks for the help :)[/QUOTE]
I'm not sure of the easiest way.  Try loading up the menu editor - there may be a "wine" menu hidden, and I think that would have a link to photoshop.

Alternatively, put
```
#!/bin/sh
wine "~/.wine/drive_c/Program Files/Photoshop/thephotoshopexecutable.exe"

```in a file, save it somewhere easy to find (like the desktop), and change its permissions so that it's executable.  Then you can double-click on that to start Photoshop.

---

### Post by Piggah on 2006-01-24
The second method isn't working for me, I'm probably not typing it right, but it's getting hectic. So how would I go about loading the wine menu? =\

thanks

edit: I got the second to work, but now when Photoshop is loading it stops and says that it cant continue because of a harware or system error. Now I'm lost. =\

---

### Post by RAOF on 2006-01-24
Well, there should be a "menu editor" icon in one of the menus.  I think it's Applications->Accessories->Alacarte menu editor?  Although that might be only in Dapper :)

Alternatively, it might be called "smeg".  It's possible you'll have to install it first - run "sudo apt-get install smeg" at a terminal.  That should get you a menu editor.

---

### Post by Piggah on 2006-01-24
It appears that I have smeg... how do I access it? 

thanks

---

### Post by RAOF on 2006-01-24
[QUOTE=Piggah]It appears that I have smeg... how do I access it? 

thanks[/QUOTE]
Just type "smeg" from the terminal.

---

### Post by Piggah on 2006-01-24
the .wine folder doesnt appear when i browse...

is there an alternative command?

---

### Post by RAOF on 2006-01-24
[QUOTE=Piggah]the .wine folder doesnt appear when i browse...

is there an alternative command?[/QUOTE]
It's a hidden folder (that's what the leading '.' is for).  In nautilus (the file browser) you can press Ctrl-H to show hidden files, and .wine will show up (under your home directory).  At the console, ls -a shows all files, including hidden files.

---

### Post by Piggah on 2006-01-24
Ah, I found an option to show the hidden folders.

I'm in the .wine folder, but what file do I need to select to run wine? =\

sorry if this is getting hectic, i really appreciate it :p

---

### Post by RAOF on 2006-01-25
[QUOTE=Piggah]yes it shows it in nautilus normally, but when I try to show it when i browse for the folder in smeg it doesn't show hidden folders[/QUOTE]
Oh.  Ahh.  There's no way to manually enter the .wine directory in?  Does Ctrl-H work there?

---

### Post by Piggah on 2006-01-25
No no, I'm in the .wine directory. I can view all the hidden files. 

I just don't know what file to select. =\

---

### Post by RAOF on 2006-01-25
[QUOTE=Piggah]No no, I'm in the .wine directory. I can view all the hidden files. 

I just don't know what file to select. =\[/QUOTE]
Aaah.  You want to go to the directory .wine/drive_c/Program Files/Photoshop and select whatever .exe looks most appropriate.  It'll probably be something like "photoshop.exe" :)

Edit: We're talking a bit at cross-purposes it seems.  You don't actually **run** wine per se - you use wine to run other things.  So you'd run "wine theprogram.exe", rather than "wine" on its own.

---

### Post by Piggah on 2006-01-25
When i try that, it says their's no such directly =\

---

### Post by RAOF on 2006-01-25
[QUOTE=Piggah]When i try that, it says their's no such directly =\[/QUOTE]
There isn't a drive_c type directory?  What **is** there under the .wine directory?

---

### Post by Piggah on 2006-01-25
dosdevices
drive_c
system.reg
user.reg
userdef.reg

---

### Post by RAOF on 2006-01-25
Hm.  Here's a better question:  Where did you install photoshop to ;)

---

### Post by Piggah on 2006-01-25
drive_c

should i have installed it somewhere else?

---

### Post by akiro.yamamoto on 2006-01-25
There are too many bits of info flying around.
Let's try to get this as coherent as possible.
Did you install Photoshop?
If you did the default install location is in your home directory in the .wine folder.
Click Places >> Home Folder. Press <CTRL>+<H>, to display hidden folders.
Scrool down to the .wine folder and move through the directories to your Photoshop folder. It should be under drive_c/ then Program Files..
If that folder is not there it's probable that you did not install the software correctly of that you installed it to a non default location.
If it is there look for Photoshop.exe or similar file, Double clicking it should start the program. Note however that some of the newer versions are not compatible with wine and must be run natively in a M$ enviroment.

---

### Post by Piggah on 2006-01-25
[QUOTE=akiro.yamamoto]There are too many bits of info flying around.
Let's try to get this as coherent as possible.
Did you install Photoshop?
If you did the default install location is in your home directory in the .wine folder.
Click Places >> Home Folder. Press <CTRL>+<H>, to display hidden folders.
Scrool down to the .wine folder and move through the directories to your Photoshop folder. It should be under drive_c/ then Program Files..
If that folder is not there it's probable that you did not install the software correctly of that you installed it to a non default location.
If it is there look for Photoshop.exe or similar file, Double clicking it should start the program. Note however that some of the newer versions are not compatible with wine and must be run natively in a M$ enviroment.[/QUOTE]

Yes I installed Photoshop and I installed it in that location, which was the default. 

There is an .exe, but when i try to run it by double clicking it says that it can't display the location. 

I know that you cant run the CS versions of Photoshop, but I have heard quite a few times that you could install Photoshop 7. 

thanks

---

### Post by akiro.yamamoto on 2006-01-25
Did you install Photoshop with the Install CD or did you copy the Photoshop Folder from your Windows Partition?
If you copied the files over you may get a host of weird errors, the program may be looking for a file that was installed in the windows enviroment that you did not copy. Or it may expect certain settings that wine will not know about as it had no control over the install process.

---

### Post by RAOF on 2006-01-25
Let's try it from the console.  cd to the directory that contains the .exe file, and run wine <nameoftheexefile>.exe
(It's possible that wine isn't handling double-clicking on an exe file correctly.)

---

### Post by Piggah on 2006-01-25
[QUOTE=akiro.yamamoto]Did you install Photoshop with the Install CD or did you copy the Photoshop Folder from your Windows Partition?
If you copied the files over you may get a host of weird errors, the program may be looking for a file that was installed in the windows enviroment that you did not copy. Or it may expect certain settings that wine will not know about as it had no control over the install process.[/QUOTE]

Well, I don't even have a CD, for eh, other reasons. But yeah, I copied the folder over from the windows partition. 

and I'll try that RAOF.

---

### Post by akiro.yamamoto on 2006-01-25
When you navigate to the drive_ c/ folder can you see the Photoshop folder under the Program Files Directory?

---

### Post by Piggah on 2006-01-25
I see Adobe first, but then Photoshop. So yes. 

And for some odd reason im not able to cd to the directory... ill keep trying though

---

### Post by akiro.yamamoto on 2006-01-25
My advice would be to use the same install SOURCE ;) that you used to install it in M$ and use that to install it in wine. If the source if a compressed file just extract it to a temp directory and run the set-up from there. Using the command line at this point will probably be mute as if you cannot find the file visually, you probably won't find it at the Terminal either.
When one of these programs installs, it installs files to the windows directory and makes changes to the windows registry. So all the info that it needs may not be available to it if you just copy the Photoshop directory over.
USE YOUR ORIGINAL INSTALL SOURCE!!!

---

### Post by RAOF on 2006-01-25
[QUOTE=Piggah]I see Adobe first, but then Photoshop. So yes. 

And for some odd reason im not able to cd to the directory... ill keep trying though[/QUOTE]
Possibly because of the space in the "Program Files" directory?  Try going 
```
cd "Program Files"
```from the drive_c directory.

---

### Post by akiro.yamamoto on 2006-01-25
If you cant CD to the directory but you can SEE IT in Nautilus right click on the directory and check the permissions under Properties. You should have at least Read, Write and Execute permission for the owner.
To set the correct permission from the console.....
sudo chmod 755 the_directory/

---

### Post by Piggah on 2006-01-25
The permissions are fine, so that cant be it. I'm really not sure. I might just be incapable of running it..

---

### Post by akiro.yamamoto on 2006-01-25
OFF-TOPIC:
ROAF do you know of any special requirements to allow me to use 2.0 GB of System memory?
My MB supports up to 4GB Ram. What is the max that the default i686 kernel will support. If I have to reduce my Swap partition to stay below that max that's not a problem.

---

### Post by RAOF on 2006-01-25
So running from a console
```
cd ~
cd .wine
cd drive_c
cd "Program Files"
cd Adobe
cd Photoshop
ls -lh

```**doesn't** work? (ie: show photoshop.exe, or something)

---

### Post by Piggah on 2006-01-25
Ok, that works. It starts photoshop. 

Now I'm still getting an error though. "Unable to continue because of a hardware or system error" 

any ideas?

---

### Post by akiro.yamamoto on 2006-01-25
[QUOTE=Piggah]The permissions are fine, so that cant be it. I'm really not sure. I might just be incapable of running it..[/QUOTE]
You may have incorrect permissions for the files in the directory......
From the command line you can try....
sudo chown username:username -R the_directory/
This should give you Owner permission for all files contained in that directory.

---

### Post by Piggah on 2006-01-25
Yeah, I have the permissions working fine. See my post above for the current issue. :p

---

### Post by akiro.yamamoto on 2006-01-25
That sounds like it's looking for something that it can't find on your system. A specific .dll file or registry setting or registry key perhaps?

---

### Post by Piggah on 2006-01-25
[QUOTE=akiro.yamamoto]That sounds like it's looking for something that it can't find on your system. A specific .dll file or registry setting or registry key perhaps?[/QUOTE]

I'm not sure, but everything looks fine. It has all the same files that it contains on windows.

---

### Post by RAOF on 2006-01-25
[QUOTE=Piggah]Ok, that works. It starts photoshop. 

Now I'm still getting an error though. "Unable to continue because of a hardware or system error" 

any ideas?[/QUOTE]
**That** will be because you just copied across the Photoshop directory ;)  It's probably looking for a dll or service or something that the installer will have installed to the Windows directory.  Like akiro.yamamoto said, find an installer & run it.  That's got a better chance of working.

Or, I suppose you could try just copying your entire windows directory in to drive_c... I've never tried that, but it **might** work.

@akiro.yamamoto - I belive that the i686 kernel supports up to the maximum that x86 supports - ie: 4GB (without crazy 36bit addressing hacks).  You're unlikely to have a 2GB swap partition ;)

Also, in the past you've had to add "ram=<whatever>" to your kernel (boot) options to get more than 1GB of ram.  I don't think that's still the case, but you could try that if it's not working.  You could look at man bootparam, but it seems a bit old ;)

Edit: Ignore that last bit - the figure in question was "more than 64**MB** of ram".  Since it obviously sees more than 64MB, that option's probably useless ;).  The Ubuntu kernels are built with support for >1GB of ram.

---

### Post by Piggah on 2006-01-25
I did run the installer though...

---

### Post by RAOF on 2006-01-25
[QUOTE=Piggah]I did run the installer though...[/QUOTE]
You ran the installer in wine?  Well...

Maybe this version of photoshop just won't run in the version of wine that you've got.  Have you checked out the wine application database?

---

### Post by akiro.yamamoto on 2006-01-25
Thanks ROAF, I thought so but it's good to know.;)
Piggah: I would seriously recommend that you INSTALL Photoshop NOT COPY the Photoshop directory over. Copying over the entire windows directory over may not work either as wine will have no direct control over the files there. Unless you KNOW what files or registry setting Photoshop is looking for you may be in for a VERY FRUSTRATING time....


EDIT:
Late Post.

---

### Post by Piggah on 2006-01-25
Well, it doesn't appear on the list, but I had assumed that it would handle it since I'd seen it so much. I did find a link to WineTools on the page that claims to be able to install Photoshop 7, so I'll give that a shot I suppose. 

thanks for the help

---

### Post by RAOF on 2006-01-25
[QUOTE=Piggah]Well, it doesn't appear on the list, but I had assumed that it would handle it since I'd seen it so much. I did find a link to WineTools on the page that claims to be able to install Photoshop 7, so I'll give that a shot I suppose. 

thanks for the help[/QUOTE]
No problem.  Hope you can get it working ;)

---

### Post by akiro.yamamoto on 2006-01-25
[QUOTE=Piggah]Well, I don't even have a CD, for eh, other reasons. But yeah, I copied the folder over from the windows partition. 

and I'll try that RAOF.[/QUOTE]


Copying the Folder is NOT the same as having wine INSTALL the program.
I do not want to recommend any thing even smelling illegal but unless you get an INSTALL SOURCE, you may never get this program to run properly.,  ;)

---

### Post by akiro.yamamoto on 2006-01-25
[QUOTE=Piggah]Well, it doesn't appear on the list, but I had assumed that it would handle it since I'd seen it so much. I did find a link to WineTools on the page that claims to be able to install Photoshop 7, so I'll give that a shot I suppose. 

thanks for the help[/QUOTE]

WineTools will ask you for the INSTALL CD or the the SETUP.EXE file/directory.

---

### Post by Piggah on 2006-01-25
It appears that way right now. I'm going to try winetools though, it looks like it will work. And if not I'll try getting ahold of the install source. 

I guess this just gives me a great excuse to learn to use gimp :p

thanks for all the help, i really appreciate it :)

edit: well, i do have the setup.exe, so it should work, right? Or do I need something exclusive to the install cd?

---

### Post by akiro.yamamoto on 2006-01-25
It matters little where the install source is hard or CD it should not matter, as long as you have an installation source with the setup.exe or install.exe file as well as your serial or CD key.

---

### Post by akiro.yamamoto on 2006-01-25
Gimp is very good or you can try InkScape which is a Vector Graphics program.

---

### Post by Piggah on 2006-01-25
well, im all for learning new things. Photoshop has always been a little overpowered for me anyways. :p 

I'll probably just leave Photoshop on my windows partition, and if it really comes down to it, just switch over. I would really like to learn gimp and inkscape, so I might just start on them. 

I'll keep messing with this though, but I'm not too worried about it at this point..

thanks for the help

---

### Post by homersbrain on 2006-01-25
There has been a regression in wine with photoshop 7. The last version that runs it is 0.9.2 which works well. All versions after this give the 'hardware error' message and crash out. Try getting wine 0.9.2 instead and all should be ok!

---

### Post by RAOF on 2006-01-25
[QUOTE=homersbrain]There has been a regression in wine with photoshop 7. The last version that runs it is 0.9.2 which works well. All versions after this give the 'hardware error' message and crash out. Try getting wine 0.9.2 instead and all should be ok![/QUOTE]
Tada!  Crazy wine strikes again.  I thought their "beta" status indicated there would be no regressions.  Or at least they'd try ;)

---

### Post by Piggah on 2006-01-25
Ah, ok. I'll just downgrade then. :) 

Thanks

edit: I've looked all over the place, but everytime I find a 0.9.2 download it just takes me to a 0.9.6 download. Anyone know where I could find  one? 

thanks

---

