---
title: "Photoshop/WINE Path Question"
date: 2006-02-11
forum: General Help
---

### Post by fishmorg909 on 2006-02-11
I'm trying to give Wine and Photoshop a go, but I can't get Wine to start PS. I have everything installed, but I'm having trouble with the path.

--------------------------

wine /home/<me>/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe
wine: cannot find '/home/<me>/.wine/drive_c/Program'

--------------------------

I should, apparently, change folder 'Program Files' to 'Program_Files', and similar to  'Photoshop 7.0' -- but the .wine folder won't give me pemission.

How do I rename those folders? Any other advice? Thanks.

---

### Post by SWAT on 2006-02-11
This is actually more a question for the wine-user maillinglist or the #winehq on irc.freenode.net. Nevertheless, let's move on.
Could you please copy/paste the wine commands/directories from your terminal in here? I guess you have some small typo somewhere. And please give us the output of "wine --version".
Note: You could also go to the directory and when you're there you could do a "wine Photoshop.exe"

---

### Post by fishmorg909 on 2006-02-11
Well, actually, I got to the Photoshop.exe with a cd line:

cd "/home/<me>/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/"

And then PS started to fire right up! But then I got an "unrecoverable error" message and PS shut off. Terminal said:

fixme:actctx:QueryActCtxW stub!
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme:actctx:QueryActCtxW stub!
fixme:actctx:QueryActCtxW stub!
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:actctx:QueryActCtxW stub!
fixme:actctx:QueryActCtxW stub!
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\<me>\\Desktop"'.
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
<me>@myname:~/.wine/drive_c/Program Files/Adobe/Photoshop 7.0$ wineserver: could not save registry branch to /home/<me>/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/<me>/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/<me>/.wine/user.reg : Permission denied

-----------------------

How do I set permissions for the registry branch?

---

### Post by SWAT on 2006-02-11
Dude, you're doing some things that are really wrong, somehow. I recon you reinstall Wine and install it correctly, and you still didn't tell me which Wine version you are using???

---

### Post by fishmorg909 on 2006-02-11
I thought I did install Wine correctly... I used Automatix. It's Wine 0.9.7

Looking at various threads, googling, etc., indicates that PS is hard to get running on Wine, though I saw a few thumb-up reports. I was pretty excited when the ol' PS logo came up and everything loaded... only to get the "unrecoverable error" message at the very end. :???:

---

### Post by Joey French on 2006-02-11
Okay, here's the deal. When you use the path to the directory, "Program Files" cannot have a space between the two words. The shell does not know how to handle it. You must do something like rename "Program Files" to "Program_Files", then try the path. You will see it start no problem.

Let me know how it goes.

---

### Post by dcstar on 2006-02-11
[QUOTE=Joey French]Okay, here's the deal. When you use the path to the directory, "Program Files" cannot have a space between the two words. The shell does not know how to handle it. You must do something like rename "Program Files" to "Program_Files", then try the path. You will see it start no problem.

Let me know how it goes.[/QUOTE]
No need to rename, just enclose the whole string in quotes:

wine "/home/<me>/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe"

---

### Post by Joey French on 2006-02-12
Yes, you can do that as well. I ran into this problem early on, so I just went ahead and renamed it.

---

### Post by fishmorg909 on 2006-02-12
How do I rename the folder? All the PS7 files are in the Wine folder, which is locked -- and says I don't have permissions to rename.

---

### Post by jackwhite on 2006-02-12
I have Adobe Indesign installed on my machine, I'd guess Photoshop would open in a similiar manner.

To start Indesign up I just right click on Indesign.exe.

I do this by opening Home in the file browser, then going to View and selecting the option for viewing hidden files.

Indesign.exe is found by going to the .wine folder > Cdrive >Program Files > Adobe > Indesign.
Photoshop should also be located in the Adobe folder.

Then just right click photoshop.exe and select 'open with wine'.


Good luck!:)

---

### Post by fishmorg909 on 2006-02-12
Ah -- I got Photoshop working. I removed Wine 0.9.7, then installed version 0.9.2. Then I unlocked the Wine folder with the terminal:

sudo chmod -R 777 .wine

Ahh, success, it fired up and worked! (Before unlocking .wine, Photoshop/Wine could not write to any PS files, thus I kept getting "unrecoverable error" message.)

AND after unlocking .wine folder, I was then able to rename "Program Files" to "Program_Files," which the application menu likes better.

Also set up desktop launcher by right-clicking desktop, selecting "create launcher," etc. Hey, I'm gettin' the hang of this.

(On a different note, I used Synaptic to remove powernowd -- it's a CPU energy-conserver that seems to be meant for laptops. I was having slowdowns and lockups on my old Optiplex box, and after removing it, all seems well!)

---

### Post by fishmorg909 on 2006-02-13
...and here's the first thing I knocked together in Wine/PS. These are very helpful forums. Thanks, all! 

[IMG]http://i33.photobucket.com/albums/d56/mntcorr57/mratomic_2.jpg[/IMG]

---

### Post by Joey French on 2006-02-14
> (On a different note, I used Synaptic to remove powernowd -- it's a CPU energy-conserver that seems to be meant for laptops. I was having slowdowns and lockups on my old Optiplex box, and after removing it, all seems well!)

Man, you're telling me! I had to remove powernowd on my box, after I started a big long thread about it here! It seems it does not like my Athlon at all, and once I removed it, not one problem since.

As a sidenote, It is almost amazing to see how stable a linux box can be when properly configured. I am truly in awe of the fact that I haven't had one single performance issue with my box in months... No blue screens, warnings, crash dialogs, nothing.

Awesome.

---

### Post by closeyourwindows on 2006-02-15
I have been having the same issues.  I was able to use image ready but photo shop would not load up.  I uninstalled wine .9.7 and installed .9.2 and now it is working.  thanks for the tips.  
by the way, according to the winehq site, there is a tool that will work called winetools for the current version, so I gave it a try and that did not work either for me.  i am just glad that I am able to have the two best apps now.  the gimp and photoshop both on linux.  its gonna be a great day.

---

