---
title: "Graphics Help Needed"
date: 2010-03-02
forum: General Help
---

### Post by A85 on 2010-03-02
Alright, let me try to make this one clear and sweet.

I left Windows because of bad customer service 3 days or so ago, Yes, I have 3 days Ubuntu experience - So far so good though, it really is great.

One thing I did notice though, the gaming. Apparently gaming on Linux - though possible - isn't exactly a piece of a cake, at least not an easy cake.

On that note, I have been trying to get my Borderlands to work for the better part of these 3 days.

For being the noob I am, I am actually happy with the progress I have made. I managed to install all of my latests graphics card drivers. Installed the latest wine and used winetricks to load some extras such as winruntime, managed to get the 3D acceleration thing to work... All of this was thanks to the very helpful guides all over these forums, seriously, I am not that smart, I couldn't have made it without them.

Back on track though. The reason I am posting this is... even though I have followed every guide I can find, I have installed and upgraded/updated so much... I still have one problem - borderlands looks like [this]("http://img30.imageshack.us/img30/773/screenshotdefaultwinede.png").

I followed a WoW guide to try to get my Borderlands to work, so I messed around with my winecfg. I tried, quite literally, every option possible, still no luck.

Could anyone suggest something please? Anywhere from a winecfg configuration, to maybe a special driver I might be missing.

Any help would be greatly appreciated.

P.S. Remember I am still very new, so if you could maybe give the Terminal Commands along with your suggestion that would be great. 

Thanks in advance guys,

A.

---

### Post by davec64 on 2010-03-02
HI,

Have you looked here:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=10539]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=10539")

Having a look myself, it seems it depends on which version you are running as to how well it will run under wine. :)

---

### Post by A85 on 2010-03-02
I went check the website you told me, to see around.
But the problem I am having seems to have something to do with either the winecfg settings or my graphics settings.

I mean the version I have of the game was running flawlessly on Windows, and for some reason when I run it on wine it _sounds_ perfect, doesn't even sound laggy whatsoever. But then, there is the graphics. It looks like 3D Polygons of all colors.

I really don't know what to do about that one. So I thought/think I might be missing some files or maybe some dlls or even the right setting. 

Help would be much appreciated.

To try to get my thing to work, I'm trying to install vcrun2008 but every I run the set up I get an error message saying "Function Failed" and the set up ends, then I get a pop up message saying "Note: command 'wine /home/a/.winetrickscache/vrun2008-ms09-035/vcredist_x86.exe' returned status 91.Aborting."

I did a little research, I couldn't really find much on the subject, but one solution seems to be installing vcrun2008 before you install the d3dx9 from wine tricks

Update : Seems deleting the .wine folder and reinstalling, this time vcrun2008 before d3dx9 works perfectly. 

Now to continue trying to solve this borderline not working thing. lol

---

### Post by A85 on 2010-03-02
So, in continuing with my journey to solve this graphics problem with my Borderlands, I stumbled up on my ATI drivers CD.
I browsed through it, and found a folder named "LinuxDrivers". I go in it and there are 3 folders, Audio, LAN and SLED.
Since there is nothing wrong with the audio, nothing wrong with the LAN, I went straight to the SLED... that's the birth of these questions I will ask :

What exactly does the "SLED" do? The description is : "It is the driver disk of SB700 for SUSE10(kernel2.6.16.46-0.12)."

What exactly does that mean?.... Does it have to do anything with my graphics?

And if so, can you guys help me translate this installation guide?

> (1) Copy the *.bz2 file to a linux system.
(2) Use ¡°bunzip2 *.bz2¡± to unzip the file. It should generate a *.img file.
(3) Plug in a usb flash disk and make sure it is not mounted automatically.
Check it by command ¡°mount¡±, there is no ¡°sdb related item exists. ( note: 
I suppose the ¡°usb flash disk¡± to be ¡°sdb¡±, if not, please change to the 
right device name)
(4) Use ¡° dd if=*.img of=/dev/sdb¡± to make a driver disk.
(5) Start installing OS by pressing F3 and pressing F5 to choose "Driver-Yes"
(6) Choose "sdb" to update the sata driver


Because when I read it, every time I read it, I go "Huh?" It's like Germanussian to me.


Thanks in advance.

---

### Post by gordintoronto on 2010-03-02
If you went through Administration/Hardware Drivers, you almost certainly have a later version of the driver than what is on the CD.

I don't think you have mentioned what video card you have. I would Google something like "borderlands nnnn linux" where nnnn is the video card model.

---

### Post by davec64 on 2010-03-02
Following on from gordintoronto, I would also double ceck you haven't Compiz running as well when your trying to run Borderlands. (set Desktop affects to none).

Is Borderlands V 1.0?

And Wine version 1.1.32 is reported as working, might be worth installing an older version of wine and trying that if it's applicable.

Also do you meet these requirements:

> 2,4 Ghz, 1 GB ram, dvd-drive 8x, 8gb space on hdd, 256 mb video card ram, Sound card win comp.

Rec. hardware:

2,4 Ghz, 2 GB ram, dvd-drive 8x, 8gb space on hdd, 256 mb video card ram, Sound card win comp.

Geforce 9 or better Radeon R700 or better

Supported video cards:

Gforce 200, Gforce 9, Geforce 8, Gforce 7, Radeon R600 (HD 2400-2900)
Radeon R600 (HD 3000) , Radeon R700 (HD 4000)

Other req.

Visual C++ runtime 2008
directx9

---

### Post by A85 on 2010-03-02
My card is ATI HD3200, the drivers are the latest version (feb, 16 2010).
Wine 1.1.39.
Borderlands v1.0.0.0
 
Meet the hardware requirements,
Got vcrun2008
Got d3dx9
Got DirectX9
 
Ran the computer with "None" special effects.
 
I already spent way too many hours just trying to get Borderlands to work... I love Linux, I really do, but truth be told, I am too lazy for it... for that latter, I am switching back to Windows. Might be buggy and it sucks, and the customer service blows, but it's easier for lazy people like me.
 
Any mod can close this thread if you like. 
 
Thank you guys.

---

### Post by Nordite on 2010-03-02
Have you checked the Wine database for the program you are trying to run?
Nordite

---

