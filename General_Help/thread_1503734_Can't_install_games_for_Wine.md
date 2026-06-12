---
title: "Can't install games for Wine"
date: 2010-06-07
forum: General Help
---

### Post by Twentydragon on 2010-06-07
I'm running Wine 1.2, and for some reason I can't install a game from a CD.  I've already tried allowing it to execute (both by right-clicking on the icon and giving the permission, which it rejects, and by giving permission to execute anything and everything on the CD), and nothing has worked.  Any ideas?

If it's at all important, I'm trying to install "The Sims" (original).

---

### Post by madnessjack on 2010-06-07
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=768](http://appdb.winehq.org/objectManager.php?sClass=application&iId=768)

I'm sorry to say, but it looks like The Sims doesn't perform very well under Wine

---

### Post by Twentydragon on 2010-06-07
That's all well and good, but I'm considering removing Wine entirely if installing things from CDs is going to be a problem.  It's the entire reason I installed Wine in the first place.

---

### Post by Bachstelze on 2010-06-07
You say "nothing has worked", but what have you tried exactly (i.e. how are you trying to install your game)?

---

### Post by Twentydragon on 2010-06-07
By "nothing has worked" I was referring specifically to what I listed as having tried:

I opened the properties of Setup.exe itself and attempted to allow it to run as executable.  The change was undone the moment I closed the Properties window.

I opened the properties of the CD as a whole and attempted to allow all files within to run as executable.  It seemed to do nothing until I ejected the CD.  Just prior to it popping out of the drive, a window was shown, telling me it had written changes to the CD.  Seeing that as something potentially dangerous, I decided to come here and ask for help before I accidentally format the thing.

---

### Post by ronnielsen1 on 2010-06-07
Games work from cd. Have you typed in winecfg in a terminal to configure wine?

You might try lincity

---

### Post by ronnielsen1 on 2010-06-07
> Just prior to it popping out of the drive, a window was shown, telling me it had written changes to the CD. Seeing that as something potentially dangerous, I decided to come here and ask for help before I accidentally format the thing.
It's not possible to do that without the cd being a cd-rw

---

### Post by Twentydragon on 2010-06-07
I haven't tried that.  To be honest, I'm not entirely sure I understand you.

Are you saying I should open the Terminal, type "winecfg" (and nothing else), and press Enter?  If so, then what?

I'm really new to Ubuntu, so I need these things in dummy-English.

---

### Post by Bachstelze on 2010-06-07
The command to run a Windows executable in WINE is

```
wine foo.exe
```

So what you need to do is: open a temrinal, browse into the directory on the CD where the installation program and run

```
wine setup.exe
```

or whatever the setup program is called.

---

### Post by Twentydragon on 2010-06-07
I can't seem to figure out how to navigate in the Terminal.  How do I get from my Home folder to the CD drive (I'm assuming it starts me off in my Home folder)?

---

### Post by ronnielsen1 on 2010-06-07
> Are you saying I should open the Terminal, type "winecfg" (and nothing else), and press Enter?  If so, then what?
Yes, this will open another window. On the Applications tab you can choose different versions of windows. Some software works better in other versions. In the drives tab, click autodetect. This should pick up on all of your drives (home files, cdroms etc)
Libraries tab are in case you need to adjust a dll as in the example belos

> In order to run Powerpoint 2007, you must set riched20.dll to (native) in winecfg. Note that you do **not **have to copy the dll from a Windows partition or use winetricks to install it. Office 2007 installs its own version of richedit in a private directory, but Wine will not use it unless you set the override.  Do not set the override globally unless you have Office installed in a separate wineprefix.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813)

Winehq is a great site to tell you how windows software will work and what you have to do to run it

---

### Post by Bachstelze on 2010-06-07
Never mind the terminal, it seems that now you can just right-click on the exe and choose "Open with Wine" in the menu.

---

### Post by retry32 on 2010-06-07
To install Sims 3 Use PlayOnLinux the ´´the sims 3 v2´´ installer

---

### Post by ronnielsen1 on 2010-06-07
You can also associate exe files to automatically open with wine. Right click, properties, open with .

---

### Post by Bachstelze on 2010-06-07
> **Twentydragon said:**
> 
Are you saying I should open the Terminal, type "winecfg" (and nothing else), and press Enter?  If so, then what?

Then nothing, don't do that. It will only confuse you, and you shouldn't need it anyway.

---

### Post by Twentydragon on 2010-06-07
> **retry32 said:**
> To install Sims 3 Use PlayOnLinux the ´´the sims 3 v2´´ installer

I'm not installing "The Sims 3".  Thanks, though.

[QUOTE=Bachsteize]Never mind the terminal, it seems that now you can just right-click on the exe and choose "Open with Wine" in the menu.[/QUOTE]
[QUOTE=ronneilsen1]You can also associate exe files to automatically open with wine. Right click, properties, open with .[/QUOTE]

If it were that easy, I wouldn't have needed to make a post about it.  That's the first thing I tried, which led to me reading about the executable bit, which led to me trying to make the files on the CD executable.

EDIT: Okay, I'm trying "winecfg".  It seems to have accepted it, as the cursor moved to the next line, but it's not really doing anything else that I can see, apart from chewing up 90% of my processor power.

---

### Post by ronnielsen1 on 2010-06-07
> EDIT: Okay, I'm trying "winecfg". It seems to have accepted it, as the cursor moved to the next line, but it's not really doing anything else that I can see, apart from chewing up 90% of my processor power.
I'm not sure why you're having trouble. It should open a window called wine configuration like below.


[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-5.png[/IMG]

---

### Post by Breambutt on 2010-06-07
Terminal opens in your home directory by default, but that doesn't really matter. To install Windows games with Wine in Lucid the easiest way is to run them with (like someone already mentioned): 

```
wine /media/[cdrom]/setup.exe
```

Media directory is where you can find the CD drive but it has a habit of changing it's name depending on the CD you put in it. For example the full path for the Diablo II installer */media/INSTALL/setup.exe* but the expansion disk was */media/EXPANSION/setup.exe*. You can just enter *wine /media/* and hit tab to see the available options under */media/*.

In case of multi-CD installers you should do it exactly like this and not navigate into the CD drive directory, otherwise you might not be able to eject and switch the disks properly. This is a little clumsy, but when an installer prompts for a second disk, open up another terminal and type *wine eject* to poop it out.

---

### Post by rwmjd007 on 2010-06-07
my issues is different i can get wine to work but during the install process where you can change to file locations it keeps coming up with this will cause the system to become unstable.

---

### Post by 3rdalbum on 2010-06-07
Go to this page about how to run programs in-place on Ubuntu, and follow the bit about Windows programs:

[http://www.chrislees.info/ubuntu/easy-run-files.shtml](http://www.chrislees.info/ubuntu/easy-run-files.shtml)

---

### Post by Twentydragon on 2010-06-07
> **Breambutt said:**
> Media directory is where you can find the CD drive but it has a habit of changing it's name depending on the CD you put in it. For example the full path for the Diablo II installer */media/INSTALL/setup.exe* but the expansion disk was */media/EXPANSION/setup.exe*. You can just enter *wine /media/* and hit tab to see the available options under */media/*.

In case of multi-CD installers you should do it exactly like this and not navigate into the CD drive directory, otherwise you might not be able to eject and switch the disks properly. This is a little clumsy, but when an installer prompts for a second disk, open up another terminal and type *wine eject* to poop it out.

Thanks, this sounds like it should help a lot.  I'll try it, and if it doesn't work, I'll be back.

---

### Post by Twentydragon on 2010-06-09
It started to work, but toward the end of installation, I received an error: "Please insert disk 0 that has data3.cab."  It should already have it, since I'm using the physical DVD-ROM to install.  (If it helps, I'm trying to install "Fallout 3".)

---

