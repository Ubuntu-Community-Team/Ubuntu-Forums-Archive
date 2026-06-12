---
title: "Installing WoW... sigh"
date: 2010-10-12
forum: General Help
---

### Post by altjx on 2010-10-12
Got WINE installed, friend went ahead and installed some components using winetricks, i ran the InstallWoW.exe > World of Warcraft...

About 60%... it says

"Failed to download World of Warcraft Installer. Please close all applications and try again."

Then when I try to re-open InstallWoW.exe, this message comes up

"No installer data could be found. If the problem persists, please contact Blizzard Technical Support."

Any idea? =(

Ubuntu 10.10 (64-bit)

Is it possible for me to just install like Windows 7 in a VirtualBox and play WoW through it?

---

### Post by sendblink23 on 2010-10-12
> **altjx said:**
> Got WINE installed, friend went ahead and installed some components using winetricks, i ran the InstallWoW.exe > World of Warcraft...

About 60%... it says

"Failed to download World of Warcraft Installer. Please close all applications and try again."

Then when I try to re-open InstallWoW.exe, this message comes up

"No installer data could be found. If the problem persists, please contact Blizzard Technical Support."

Any idea? =(

Ubuntu 10.10 (64-bit)

Is it possible for me to just install like Windows 7 in a VirtualBox and play WoW through it?

If your graphics are supported through VBox then do that... but as for Wine... just follow the instruction(read all the info people write) from WineHQ: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421)

---

### Post by altjx on 2010-10-12
> **sendblink23 said:**
> If your graphics are supported through VBox then do that... but as for Wine... just follow the instruction(read all the info people write) from WineHQ: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421)

One problem man. I don't have WoW Discs, I am using the Downloader... it tells you if you're using the Downloader, just jump straight to Configuring... The problem is, I can't get it to download. So that guide isn't really helpful at all for me.

---

### Post by sendblink23 on 2010-10-12
> **altjx said:**
> One problem man. I don't have WoW Discs, I am using the Downloader... it tells you if you're using the Downloader, just jump straight to Configuring... The problem is, I can't get it to download. So that guide isn't really helpful at all for me.

What can't you get to download from the Configuration instructions?
> Configuring

The suggested way to run World of Warcraft in wine is using OpenGL. Although you lose hardware cursor functionality and shadow detail, you will often gain tons of FPS this way. Operation without the opengl flag is often unreliable and will not start with some cards. If you wish, you can install a hack for hardware cursor like functionality here( [http://ubuntuforums.org/showpost.php?p=7643957&postcount=82](http://ubuntuforums.org/showpost.php?p=7643957&postcount=82) ).

Simply add the -opengl flag to the end of your WoW Launcher (recommended) :-

Open the WoW desktop shortcut and add -opengl to the end of the command (leaving a space). (Recommended method).(Recommended for first run after CD or download).

Alternatively, you can either edit your WTF/Config.wtf in your World of Warcraft directory to include :- 

SET gxApi "opengl"

(Note that this file is only created after you have logged in once). 



---

### Post by CharlesA on 2010-10-12
The graphics will be garbage if you are running Win7 in VBox. Direct3D support is experimental at best.

---

### Post by altjx on 2010-10-12
> **sendblink23 said:**
> What can't you get to download from the Configuration instructions?

If all I have is InstallWoW.exe, what am I going to configure? Launcher.exe and InstallWoW.exe are different. There's nothing for me to do under the configuring page to my knowledge. I don't have any folders or files other than installwow.exe

---

### Post by altjx on 2010-10-12
> **CharlesA said:**
> The graphics will be garbage if you are running Win7 in VBox. Direct3D support is experimental at best.

What do you recommend as far as with VirtualBox if I can't get it installed on the host OS then?

---

### Post by CharlesA on 2010-10-12
It doesn't really matter what OS tbh, as VBox doesn't really have very good 3d acceleration. You could try VMWare but there will still be slow downs.

---

### Post by altjx on 2010-10-12
> **CharlesA said:**
> It doesn't really matter what OS tbh, as VBox doesn't really have very good 3d acceleration. You could try VMWare but there will still be slow downs.

Thanks, as far as that WINE guide... I'm misunderstanding something I believe. That guide doesn't provide help for what I'm in need of. I can't get the Installer to even download, so I don't have a launcher to go off of.

---

### Post by CharlesA on 2010-10-12
I don't use Wine, so I can't help you there, unfortunately. :(

Do either of these help:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)

---

### Post by altjx on 2010-10-12
> **CharlesA said:**
> I don't use Wine, so I can't help you there, unfortunately. :(

Do either of these help:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)

Thank you so much! Going to install it on XP in VirtualBox and proceed with the instructions. Will mark as solved once I get it up and running.

---

### Post by Captain Giraffe on 2010-10-12
Im just now updating to the last expansion. Sry I can help you with your problem but Wine and Wow runs very good.

EDIT:
also from the online installer, I tried afew times I think a dotnet dll helped me, but thats all in winetricks.
gl.

---

### Post by altjx on 2010-10-13
Thanks all. I was able to do all the installing inside of Windows XP and transferred it to my local machine. One problem now, the Launcher freezes when I open it. Stops at "Initializing, please wait"

On the other note, if I open the WoW.exe directly, it just makes my resolution all huge and stuff, and it closes out. Nothing else opens. Can someone tell me what's next in the troubleshooting list? I've done the OpenGL thing in the config.wtf too. Not sure what else to try =[

---

