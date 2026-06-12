---
title: "WINE Can't open SoundForge"
date: 2010-03-14
forum: General Help
---

### Post by kazakore on 2010-03-14
Right clicking and Open With Wine does nothing.

Using Terminal and browsing to the folder and putting in $ wine AudioStudio90.exe brings up these errors. Is it going to be possible to run it through Wine at all and what will I have to do?

> fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\AudioStudio90k.dll") not found
err:module:import_dll Library AudioStudio90k.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\AudioStudio90.exe") not found
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\AudioStudio90k.dll") not found
err:module:import_dll Library AudioStudio90k.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\frgusr.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\frgusr.dll") not found
err:module:import_dll Library frgusr.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\AudioStudio90.exe") not found
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\AudioStudio90k.dll") not found
err:module:import_dll Library AudioStudio90k.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\frgvid.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\frgvid.dll") not found
err:module:import_dll Library frgvid.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\AudioStudio90.exe") not found
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\AudioStudio90k.dll") not found
err:module:import_dll Library AudioStudio90k.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\frgplugs.dll") not found
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\AudioStudio90k.dll") not found
err:module:import_dll Library AudioStudio90k.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\frgusr.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\frgusr.dll") not found
err:module:import_dll Library frgusr.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\frgplugs.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\frgplugs.dll") not found
err:module:import_dll Library frgplugs.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\AudioStudio90.exe") not found
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\sfspti.dll") not found
err:module:import_dll Library sfspti.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\sfspti2.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\sfspti2.dll") not found
err:module:import_dll Library sfspti2.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\sfscsi.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\sfscsi.dll") not found
err:module:import_dll Library sfscsi.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\sfcdix.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\sfcdix.dll") not found
err:module:import_dll Library sfcdix.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\AudioStudio90.exe") not found
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\sfs4rw.dll") not found
err:module:import_dll Library sfs4rw.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\AudioStudio90.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\AudioStudio90.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\D4C89D4CC89D2E2C\\Program Files\\Sony\\Sound Forge Audio Studio 9.0\\AudioStudio90.exe" failed, status c0000135



(Does this site have e a tag on here similar to the Spoiler one that hides some or all text before clicked on? Useful for bug reports and entering reams of information.

---

### Post by Enigmapond on 2010-03-14
This programme, to my knowledge, will not run well on Linux. Too many Windows dependencies. I have found Audacity to be comparable and actually better than this. It may be more trouble than it's actually worth.

---

### Post by kazakore on 2010-03-14
I really don't like Audacity's interface. I spent months using different free editors and trying demos of the pay ones before I finally forked out for the Audio Studio version of SoundForge (fairly reasonable at £45 although was £30 when I started my research.)

This page seems to imply it should run well but has a fair few dependancies, such as winetricks, which I can see where to download (not in 9.10 repository.)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15447&iTestingId=36617](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15447&iTestingId=36617)


EDIT: But I will probably give rezond and SND some time as people have recommended them as well.

---

### Post by solitaire on 2010-03-14
There's a "bug" in wine where it will not see Visual C runtimes (or something like that)
```

fixme:actctx:p****_depend_manifests Could not find dependent assembly  L"Microsoft.VC80.CRT"
```

If you use wintricks to install the correct Visual C runtimes it might work. 

Only way I've ever fixed it is to grab the "/WinSXS/" folder from a working WinXP install and copy it into the /windows/ folder in "~/.wine/drive_c/"

---

### Post by kazakore on 2010-03-14
OK this machine is dual boot, WinXP SP3 and SP9.10.

I have to admit that I currently know about as close to zero about Wine as possible. In fact I was starting to struggle with this /.wine/drive_c business when it was time to stop searching the internet and come home from work.

Should I be moving files I want to execute over into this special folder? (Just clicked now the ~ is Home and the dot prefix is a hidden file.) Or should I execute from the XP installation? Which is what I've currently been trying and thought would be the correct way to do it, but then, as you say, there are likely Registry problems, amongst other things.

---

### Post by cchhrriiss121212 on 2010-03-14
Wine is just a program that allows you to run windows programs on a linux OS, but you probably knew that already. To do this it makes a windows type c drive within your ubuntu partition. You don't need a windows installation to run wine. You can run an .exe file from anywhere on your ubuntu partition, it doesn't need to be from xp or in any special folder to execute and install. 
You can probably get this to work but be prepared to take some time with it. The  working example on wine hq also show it running for 8.10 which can be important as you are on 9.10.
I'd spend some time trying out some native editors if you are commited to using ubuntu, otherwise I'd just stick with using it on xp.

---

### Post by solitaire on 2010-03-14
Ok first go to your home folder and press "ctrl+h" (that will show you hidden files and folders in Ubuntu)
look for the ".wine" folder and open it.
open the "drive_c" folder
the open the "windows" folder.
you should see a folder called "WinSXS" right click and rename it to "winsxs.old"

Next

Go to "Places" then "Computer" then mount your "XP" partition.
Browse the XP folder and go to "Windows" in there you'll see the "winsxs" folder
Right click on "winsxs" and select copy.

Follow the instructions to find ".wine" again, then browse to the windows folder (~/.wine/drive_c/windows/)
Then right click and select "paste"

That will copy the winsxs folder from your windows partition to the wine folder.

Try the install again.

---

### Post by kazakore on 2010-03-15
> **solitaire said:**
> Ok first go to your home folder and press "ctrl+h" (that will show you hidden files and folders in Ubuntu)
look for the ".wine" folder and open it.
open the "drive_c" folder
the open the "windows" folder.
you should see a folder called "WinSXS" right click and rename it to "winsxs.old"

Next

Go to "Places" then "Computer" then mount your "XP" partition.
Browse the XP folder and go to "Windows" in there you'll see the "winsxs" folder
Right click on "winsxs" and select copy.

Follow the instructions to find ".wine" again, then browse to the windows folder (~/.wine/drive_c/windows/)
Then right click and select "paste"

That will copy the winsxs folder from your windows partition to the wine folder.

OK done that, renamed to same capitalization as the original Wine winsxs folder. Clicking on the executable now seems to get further. Takes me as far as the Registration part, now this has already been registered on this computer (also on my old desktop) and think Sony can be quite strict at times. Filled it in anyway but then it fails, thinking there is no internet connection.

I have Wine Gecko, which I believe is for Wine Internet, is this all I should need for the online registration through Wine (actually can register from other computer so will try this.)

> Try the install again.

Did you mean install? Or the executable, already installed file like I tried above? I should still have the install files if I need to run it again in the Wine folder...

---

### Post by kazakore on 2010-03-15
OK after registration it work and I can load and play files but it does not display the waveform.

Guess this might be a little beyond here to fix but if you have any ideas I would love to hear it.

Many, many thanks for your help!

---

### Post by kazakore on 2010-03-15
> **kazakore said:**
>  it does not display the waveform.


Doh! The solution to that was in the link I gave earlier

> 
By default, the graph displaying the audio spectrum of a opened audio clip is not shown. Fix this by enabling &#8220;Preferences &#8594; General &#8594; Compatible draw mode (for broken video drivers)&#8221; checkbox.
Thing is most of the Menus aren't working so I can't do or access a lot of stuff!

Although I can set ones I want on the Toolbar as Menus show up once on loading.

Have just found out none of the Processing (Effects) actually load when clicked on though :(

---

