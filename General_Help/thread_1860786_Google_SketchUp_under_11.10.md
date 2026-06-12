---
title: "Google SketchUp under 11.10"
date: 2011-10-15
forum: General Help
---

### Post by fixerdave on 2011-10-15
Yay, I just got SketchUp to work under 11.10... ran into enough problems that I'd thought I'd share the answers I came up with... save the next person googling all over the internet.

Installing and Running SketchUp Under WINE:

After installing WINE, download Google Sketchup.  
Right-click on the file and “run under wine”.

bug 14045: If you get the error "SketchUp was unable to initialize OpenGL!, run regedit (from the terminal type: wine regedit), open [HKEY_CURRENT_USER\Software\Google\SketchUp8\GLConfig\Display], and change "HW_OK" to 1.
This is from:  [http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)

Printing issue:  I get a blank page unless I **enable high accuracy HLR** in the print window. Also, I can’t get the export 2D graphics to work at all.

Display update issue.  I ran into an issue where the display would not update until the next command/click/zoom.  This is a problem.  The only solution I found that works was a startup script as follows:  
    (source: an anonymous comment on ubuntu-linux-sketchup-using-wine)


```

#! /bin/bash
# Uses xrefresh launched repeatedly using watch within an iconified xterm
# to force Google Sketchup to redraw every 0.3 seconds...
# Stores the PID and kills the xterm on exit from Sketchup!
xterm -iconic -title "Sketchup Refresher (xterm)" -e "watch -n 0.3 xrefresh -geometry 1x1+500+500" & watchPID=$!
echo $watchPID
env WINEPREFIX="/home/<username>/.wine" wine "C:\Program Files\Google\Google SketchUp 8\SketchUp.exe"
kill $watchPID

```

Use as follows:
        Create a text file with the above lines.
        In Properties for this file, mark it as executable
        In the menu (I still use Gnome panels) create a new launcher that points to this file.
It’s not pretty, but it works well enough.

Scene update crashes:
        Turning off - **Use Scene Thumbnails** resolves this.

Hope this saves a few others some trouble.

    David...

P.S.  I wrote a SketchUp tips page here:
[http://fixerdave.blogspot.com/2011/05/google-sketchup-notes.html](http://fixerdave.blogspot.com/2011/05/google-sketchup-notes.html)

---

### Post by CRIMPS on 2011-10-29
Great work!  Thanks for sharing.

---

### Post by coldraven on 2011-10-30
"P.S.  I wrote a SketchUp tips page here:
[http://fixerdave.blogspot.com/2011/0...hup-notes.html]("http://fixerdave.blogspot.com/2011/05/google-sketchup-notes.html")
"

Nice! Bookmarked :)
Sketchup is the reason I keep a VM of XP

---

### Post by Electraglider on 2011-10-30
I decided to give this a try and it worked. Playonlinux was a total bust. Thanks for this post fixerdave. You have changed my opinion about  the wine project.

---

### Post by madjr on 2011-10-30
> **Electraglider said:**
> I decided to give this a try and it worked. Playonlinux was a total bust. Thanks for this post fixerdave. You have changed my opinion about  the wine project.

maybe is good idea if someone can contribute some of those fixes to the playonlinux scripts for sketchup or report it to the team, i think thats why POL was created, to have workarounds or tweaks for as many apps as possible.

---

### Post by NTL2009 on 2011-10-31
I have seen this regedit tip, and used it on previous installs of Sketchup and it runs fine (under 10.04/lucid). However, on a test machine and external drive, I installed 11.10 (and installed Kubuntu kde-desktop), installed WINE and SketchUp8 - but when I go into regedit, there are no folders under HKEY_CURRENT_USER\Software\Google\SketchUp8 , so I can't edit the KEY as I did before. Sketchup won't load, I get an "encountered a serious problem and needs to close" dialog.

Oddly, NOTEPAD opens and runs fine, but when I select "Browse C : Drive" it errors and is looking in ~/Document/.wine, rather than where it actually is at ~/.wine .

I'm lost - are there other libraries and/or dependencies I need? How would I go about finding them?

-NTL2009

---

### Post by dierde on 2012-02-06
i face the same problem as @NTL2009

is there a solution for that?

i installed sketchup 8 on an kubuntu 10.04 LTS installation

hope i can warm up this thread,

thanx
roland

---

### Post by Rocketman4God on 2012-02-26
> **fixerdave said:**
> Yay, I just got SketchUp to work under 11.10... ran into enough problems that I'd thought I'd share the answers I came up with... save the next person googling all over the internet.

Installing and Running SketchUp Under WINE:

After installing WINE, download Google Sketchup.  
Right-click on the file and “run under wine”.

bug 14045: If you get the error "SketchUp was unable to initialize OpenGL!, run regedit (from the terminal type: wine regedit), open [HKEY_CURRENT_USER\Software\Google\SketchUp8\GLConfig\Display], and change "HW_OK" to 1.
This is from:  [http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)

Printing issue:  I get a blank page unless I **enable high accuracy HLR** in the print window. Also, I can’t get the export 2D graphics to work at all.

Display update issue.  I ran into an issue where the display would not update until the next command/click/zoom.  This is a problem.  The only solution I found that works was a startup script as follows:  
    (source: an anonymous comment on ubuntu-linux-sketchup-using-wine)


```

#! /bin/bash
# Uses xrefresh launched repeatedly using watch within an iconified xterm
# to force Google Sketchup to redraw every 0.3 seconds...
# Stores the PID and kills the xterm on exit from Sketchup!
xterm -iconic -title "Sketchup Refresher (xterm)" -e "watch -n 0.3 xrefresh -geometry 1x1+500+500" & watchPID=$!
echo $watchPID
env WINEPREFIX="/home/<username>/.wine" wine "C:\Program Files\Google\Google SketchUp 8\SketchUp.exe"
kill $watchPID

```Use as follows:
        Create a text file with the above lines.
        In Properties for this file, mark it as executable
        In the menu (I still use Gnome panels) create a new launcher that points to this file.
It’s not pretty, but it works well enough.

Scene update crashes:
        Turning off - **Use Scene Thumbnails** resolves this.

Hope this saves a few others some trouble.

    David...

P.S.  I wrote a SketchUp tips page here:
[http://fixerdave.blogspot.com/2011/05/google-sketchup-notes.html](http://fixerdave.blogspot.com/2011/05/google-sketchup-notes.html)

Do you think that you could help me? I have Ubuntu 11.10 64 bit. I have downloaded Wine and the Windows installer version of SketchUp 8. I have tried to get Wine Tricks to install SketchUp, but I get this message... Checksum for /home/adam/.cache/winetricks/sketchup/GoogleSketchUpWEN.exe did not match, retrying download. I hit OK, and Wine Tricks goes to work downloading GoogleSketchUpWEN.exe  Then, it eventually throws me the same error. Does anyone know what I need to do?

---

### Post by fixerdave on 2012-02-27
> **Rocketman4God said:**
> Do you think that you could help me? I have Ubuntu 11.10 64 bit. I have downloaded Wine and the Windows installer version of SketchUp 8. I have tried to get Wine Tricks to install SketchUp, but I get this message... Checksum for /home/adam/.cache/winetricks/sketchup/GoogleSketchUpWEN.exe did not match, retrying download. I hit OK, and Wine Tricks goes to work downloading GoogleSketchUpWEN.exe  Then, it eventually throws me the same error. Does anyone know what I need to do?

Have you tried just downloading SketchUp from the Google page and then doing a Right-Click, Open With, Wine windows program loader?

I didn't use Wine Tricks.  I just installed Wine and used it to run the SketchUp installer.

Another option, if the above doesn't work, is to use the console.  Just change to the folder where you downloaded SketchUp and type: 
  **wine GoogleSketchUpWEN.exe**
and it will run.  This way, you can at least see any error messages that might come up and those might give you a clue, or at least a string to google.

David...

---

### Post by agb253 on 2012-03-09
I think I screwed everything up:
I downloaded Google SketchUp 8 and Wine 1.2.3.  
1. I tried opening with Wine and it gave me the OpenGL error.
2. I tried updating the video card drivers under "additional drivers" under settings.  Some error occured so update failed
3. I tried updating the driver using suggestions from [http://ubuntuforums.org/showthread.php?t=1724456](http://ubuntuforums.org/showthread.php?t=1724456)
4. Tried updating drivers under "additional drivers"; this time drivers were updated successfully.
5. Now trying to open Google SketchUp 8, will not launch, nothing happens.
6. I tried the registry change "HW_OK" to 1 and still nothing.  
7. Thought I would delete SketchUp and try again. Wouldn't delete.
8.  I deleted the registry for SketchUp, and tried to reinstall SketchUp. Only allowed "repair". The registry didn't come back. 
9. Tried reinstalling wine. No change.

I'd like to just start over, but I don't know how to set everything back to how it was.
Please help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by fixerdave on 2012-03-09
> **agb253 said:**
> I think I screwed everything up:
...
I'd like to just start over, but I don't know how to set everything back to how it was.
Please help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

You can remove wine by uninstalling it and also deleting the .wine directory in your home folder.  Cntr-H will show hidden if you're working in nautilus, the gui file manager.

Next, I'd recommend you get your 3D graphics working... won't get anywhere without that.  There is a tool call glxgears that is available in the mesa-utils package.  It makes for an easy test once you know how to use it.  It won't get your 3D graphics working but it will let you know when it is.  Getting your 3D graphics working is way beyond my abilities and I'd advise searching the forums for people using the same hardware as you.

Then, install wine, and then use wine to install sketchup.  There's no point doing that until you get 3D graphics working.  You need to get the foundation set before any of the fixes I mentioned will be of any help.

   David...

---

### Post by gmharris on 2012-05-29
Two additional workarounds (a little cleaner than the 'watch a pixel and
continuously refresh'.

Workaround 1 (slow): Run using the command line:
env LIBGL_ALWAYS_SOFTWARE=1 WINEPREFIX="" wine
SketchUp.exe

Workaround 2 (awesome): Run using the command line:
vblank_mode=0 WINEPREFIX="" wine SketchUp.exe 

These both absolutely fixed the problem for me of having the screen not update
correctly.
My configuration:
Sketchup8 installed via WineTricks
Wine 1.5.5
Ubuntu 12.04 64bit
Intel i915 driver (i965 DRI)

Things I tried that *didnt* work:
Using my .drirc to set the vblank_mode to 0
Changing options of INTEL_STRICT_CONFORMANCE
Setting LIBGL_ALWAYS_INDIRECT
And about a thousand other things.

---

### Post by fixerdave on 2012-06-08
> **gmharris said:**
> Two additional workarounds ...

Workaround 2 (awesome): Run using the command line:
vblank_mode=0 WINEPREFIX="" wine SketchUp.exe 
...

I just tried this and it worked for me, though I had to eliminate the WINEPREFIX="" part and add the full path to SketchUp.exe.

Much cleaner than the script approach.  Thanks for doing the research on this and sharing the result.

David...

---

### Post by C Martin on 2012-10-14
11.10 Oneric, wine 1.4 & 1.5 tried, 32 bit HP pavilion dm4 => SketchUp 8

There is no 'google' directory under 'software' to make the change  > Using regedit change

>"HW_OK" = 1 in key > HKEY_CURRENT_USER\Software\Google\SketchUp8\GLConfig\Display  



I uninstalled and reinstalled wine 1.4 & 1.5 several times.  Although I never erased the .wine file. 
 
I attempted to uninstall and reinstall SketchUp 8 with sketchup.com, although uninstall appeared totally unsuccessful.  

First install of SkU I did an 'open' but 'w/ a wine application' was not an option although wine 1.4 was installed (I'm pretty sure).  This option did show after a restart I did after my first SkU install attempt. 
 
Second install of SkU I did a 'save file' (I may have done this one with Wine Tricks)  

Third install of SkU => 'Open w/ wine"


I'm not sure if I am dealing with a user error or a change in SkU software install.


Ideas?  Thoughts? (I'm a complete and total newbie/idiot) Much appreciated!

---

### Post by fixerdave on 2012-10-14
> **C Martin said:**
> 11.10 Oneric, wine 1.4 & 1.5 tried, 32 bit HP pavilion dm4 => SketchUp 8

There is no 'google' directory under 'software' to make the change  > Using regedit change

>"HW_OK" = 1 in key > HKEY_CURRENT_USER\Software\Google\SketchUp8\GLConfig\Display  
...
Ideas?  Thoughts? ...

When you start SketchUp after the install, does it complain about OpenGL?  If so, then both wine and sketchup are installed.

Are you using the terminal to start regedit via wine?  (**wine regedit**)  Regedit is the registry editor... just making sure you're not looking for google\software in the file system or something.  The registry is a Windows configuration database thing (some would call it a mistake :(, I think Bill said something to that effect :lolflag:)

David...

---

### Post by C Martin on 2012-10-15
Are you using the terminal to start regedit via wine?  (**wine regedit**)  Regedit is the registry editor... just making sure you're not looking for google\software in the file system or something.  The registry is a Windows configuration database thing (some would call it a mistake :(, I think Bill said something to that effect :lolflag:)

David...[/QUOTE]


Thanks for the reply.

Well I gave up on 11.10 Oneric and went to 12.04 Precise w/ wine 1.5.x (whatever the current is).  Sketch Up 8 is now working in 12.04 with the GL Config fix.  Now I'm attempting to deal with the "one mouse event behind" issue.

I never figured out why I didn't have a google file.  Yes, I was running regedit from the terminal.  Yes, SketchUp ran in the previous condition (11.10/1.4).  It started to run to the point of allowing me to select a template type then crashed.  So the usual idiot mistakes weren't made (this time).... it was actually installing.  However, in the 11.10 installs SkU did not ask me for a location to unpack files.... so I still don't know if I some how missed a step and confused it while installing or this is a new change with the SketchUp install files.  

Either way its running now - and so far I haven't really broken anything....  I'm now searching for the fix to the "mouse one event behind" issue....  Let me know if you have tips on that!!!! :)

Thanks for going on the ride with me!!!  :)

---

### Post by C Martin on 2012-10-15
Bugger.... :I

Re: the mouse event behind thing...

Comment 38 & 39 on [http://bugs.winehq.org/show_bug.cgi?id=25912](http://bugs.winehq.org/show_bug.cgi?id=25912)  :

           [Comment 38]("http://bugs.winehq.org/show_bug.cgi?id=25912#c38")                   2012-08-06 13:36:57 CDT         
(In reply to [comment #37]("http://bugs.winehq.org/show_bug.cgi?id=25912#c37")) > Try > optirun env vblank_mode=0 WINEPREFIX="<prefix>" wine <path to sketchUp.exe > or >  > vblank_mode=0 WINEPREFIX="<prefix>" optirun wine <path to sketchUp.exe  I have tried those already. Unfortunately both of them result in sketchup being one action behind 

[Comment 39]("http://bugs.winehq.org/show_bug.cgi?id=25912#c39")                                                  2012-09-27 12:13:05 CDT                
    I have been having this trouble since I have upgraded to ubuntu studio 12.04, and followed this guide [http://ubuntuguide.net/install-google-sketchup-cad-style-app-in-ubuntu-using-wine](http://ubuntuguide.net/install-google-sketchup-cad-style-app-in-ubuntu-using-wine) and still had the trouble. So googled some more and got here and read all your responses, so I have had a play around and tried all manor of fixes and managed to break the video output of sketch-up.  following that I uninstalled everything to do with wine and sketch-up and reinstalled wine, then installed sketch-up just by right clicking and run in wine.  once installed I DID NOT OPEN IT! I went to wine-tricks and installed the DLL's from the guide as mentioned, then I had a thought about when I use to run different programs on windows it's self and thought about installing all the C++ run-time libraries available. As have always seen them all installed in windows as updates. and guess what IT WORKS!!!!!!!!!! No lagging mouse clicks. Not sure this is the root of all your problems but windows has been broken for so many years and there has been so many fixes (e.g. C++ libraries all being installed) that one of the libraries might just have the fix. sounds crazy I know but it works     
            
I don't know how to load DLLs!!!!  Or where to find them!!!   ....bugger... bugger...



Ok... switching back to the fix which should work on my Intel driven machine.....  This is gonna be an idiot question here....

> Workaround 2 (awesome): Run using the command line: > vblank_mode=0 WINEPREFIX="<whatever the prefix is>" wine SketchUp.exe 

What do we mean by "prefix"?

---

### Post by fixerdave on 2012-10-16
> **C Martin said:**
> ... What do we mean by "prefix"?

Not a clue.  No clue why a command can start with that vblank_mode=0 thing either.  No idea why it works, but here's what worked for me:

```
vblank_mode=0  wine "/home/fixerdave/.wine/dosdevices/c:/Program Files/Google/Google SketchUp 8/SketchUp.exe"
```

Obviously, it needs to be changed for your circumstances.  But, in general, I skipped the prefix thing entirely and had to provide the full path to SketchUp.exe.  Your path will be different in at least the username part and possibly in other places as well.

The above will need to be run from a terminal session.  If it works, you can create a script, make it executable, and then create a launcher that points to said script... Running from a terminal and just using the up-arrow for commandline recall might prove easier at the start.  You will also get to see the error messages that come up, which can be useful in figuring out where all that "bugger" is coming from.

More details on this here:
[http://fixerdave.blogspot.ca/2011/05/google-sketchup-notes.html](http://fixerdave.blogspot.ca/2011/05/google-sketchup-notes.html)

I'm no expert in this... just reporting what worked for me,

David...

---

### Post by Dabo Ross on 2013-01-06
All this seems to work fine, and I have it running on my computer! Thank you!

All of it is working except that when I try to upload to the 3D warehouse, it asks me to sign in and brings up a window with a blank white background, and no way to sign in. Any suggestions?

---

