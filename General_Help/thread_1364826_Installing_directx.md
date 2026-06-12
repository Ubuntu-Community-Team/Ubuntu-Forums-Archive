---
title: "Installing directx"
date: 2009-12-26
forum: General Help
---

### Post by hakermania on 2009-12-26
Hi!!!
I want to know 
1st: How can I install DirectX in ubuntu 9.10 (I have wine and playonlinux but i have no idea how to use playolinux but i use wine to load e.g. winrar)
2nd: How can I play a game, for example what must I have from the game to play? The installation of the game or something? because I click on PlayOnLinux the install button, it goes to a menu, I select games and "age of empires 2" and click apply and then what? it asks me for a file and I don't know what it is talking about!

Notes: I have downloaded DirectX from filehippo and I have downloaded the 2 required dlls from a site with many free ddls, and I've put them to system32 folder. So, don't explain anything about these things.

Generally I need to understand the way PlayOnlinux behaves, because i haven't understand it at all!!!:sad:

---

### Post by Babuloseo on 2009-12-26
Why dont you try installing Runes OF Magic from PlayOnLinux?

---

### Post by ankspo71 on 2009-12-26
Hi,

 In playonlinux, if a game requires directx, msfonts, etc, it will automatically install it for you.  Some of the games and programs require that you have downloaded the exe file yourself first (or have the game cd etc), but for some others it doesn't require this. Winamp in playonlinux can be downloaded by playonlinux, but "Track Mania Nations Forever" requires you to have already have the tmnationsforever_setup.exe downloaded from the tmnations site. So if it asks you for a file, go find the file on the internet, download it, then click on forward (or apply) in playonlinux, show it where you downloaded the file, then finish the installation. 

Wine is good because it is not limited to a certain number of programs like playonlinux, but on the other hand, playonlinux is good, because the scripts know what to install to make the program or game work best. I have both installed. :P

You also have the option to install Directx and other things to games already installed through playonlinux.
I hope this helps.

---

### Post by hakermania on 2009-12-26
> **Babuloseo said:**
> Why dont you try installing Runes OF Magic from PlayOnLinux?

yeah, OK, Runes of Magic is being downloaded when you press "next" but what's happening if I have the installation file (exe) in my hard drive?

---

### Post by hakermania on 2009-12-26
yeah this really helped!
But I have on other question:
i donloaded Age Of empires 2 in direct play and, surprisingly, I opened the exe file with wine and the game plays normally? Is possible for Wine to load a game like this or PlayOnLinux loaded the file in reality?:confused:

---

### Post by Babuloseo on 2009-12-26
Wine should be able to automatically install the game and put it on the Program Files folder.

---

### Post by hakermania on 2009-12-26
> **Babuloseo said:**
> Wine should be able to automatically install the game and put it on the Program Files folder.
the game needn't to be installed.It was "Direct Play".
You run the exe and then play normally without any installation!

---

### Post by RickJC on 2009-12-26
HI Guys I have a similar problem as the original post. When I tried to install EVE Online using Wine it installed the game fine but it said it couldn't install DirectX and that I should download the .exe file of directx and install myself.

Having downloaded the directx exe file and tried to install it I get a error message in Wine saying "This program requires Windows NT version 5.01.2600 or later", anyone any idea's as to how I sort this?

---

### Post by ankspo71 on 2009-12-26
Hi,
I can use either 'DirectX 9.0c Redistributable for Software Developers' or 'DirectX Redist (March 2009)'. You can find either of them by searching for direct 9.0c on the MS download site. I had some trouble with the web-updater types, so the larger redistributable ones are a plus for me. 

Also make sure your wine application preferences is set to windows xp or newer. You can also make these settings for any individual exe that you have trouble with. That's like compatibility mode for exe files. If you don't have the shortcut to "configure wine" you can launch it by typing winecfg in the terminal.
hope this helps.

---

### Post by hakermania on 2009-12-27
> **ankspo71 said:**
> Hi,
I can use either 'DirectX 9.0c Redistributable for Software Developers' or 'DirectX Redist (March 2009)'. You can find either of them by searching for direct 9.0c on the MS download site. I had some trouble with the web-updater types, so the larger redistributable ones are a plus for me. 

Also make sure your wine application preferences is set to windows xp or newer. You can also make these settings for any individual exe that you have trouble with. That's like compatibility mode for exe files. If you don't have the shortcut to "configure wine" you can launch it by typing winecfg in the terminal.
hope this helps.

And what's happening when you have downloaded the directx9 from filehippo and you want to install it? I think you must go and press install on PlayonLinux and then select directx 9 in your hard drive and continue with installation?:confused:is that right?

---

### Post by ankspo71 on 2009-12-27
Hi,
Install that one from filehippo into wine, because playonlinux downloads directx for you when you install it to a game that was installed by playonlinux. Keep in mind that playonlinux won't download all other things though, as sometimes it asks us where we downloaded certain files.

I don't completely understand playonlinux, but it appears to me to be a completely independent program from wine, although it does use wine to make windows programs run in linux. Anything I install in playinlinux, does not get installed into wine's program files directory. So installing Directx in wine won't help games in playonlinux (as far as I know), and neither will installing Directx in playonlinux help games in wine (as far as I know). If you have games installed in wine and playonlinux, install directx in both wine and playonlinux. 

Wine Doors is also something to consider. I haven't used it in a year probably, but it was good to use in addition to wine when I used it. [http://wddb.wine-doors.org/node/3](http://wddb.wine-doors.org/node/3)

---

### Post by RickJC on 2009-12-29
> **ankspo71 said:**
> 
Also make sure your wine application preferences is set to windows xp or newer. You can also make these settings for any individual exe that you have trouble with. That's like compatibility mode for exe files. If you don't have the shortcut to "configure wine" you can launch it by typing winecfg in the terminal.
hope this helps.
 
 
Thanks, I forgot that I set it to windows ME so I could play an old game duh :P
 
Putting it to XP solved the issue, thanks.

---

