---
title: "how does root access user folders/applications??"
date: 2011-03-14
forum: General Help
---

### Post by Amused2Death on 2011-03-14
Hi,
Installed The Witcher via playonlinux.
All went well but when i go to launch it wants to install drivers and says i must have administrator privileges. I must be an administrator when i run this game for the first time.

But when i use gksudo nautilus i am unable (with my experience) to access playonlinux so i can run the game the first time as an administrator.

I know there must be a solution out there somewhere :)

---

### Post by 3Miro on 2011-03-14
> **Amused2Death said:**
> Hi,
Installed The Witcher via playonlinux.
All went well but when i go to launch it wants to install drivers and says i must have administrator privileges. I must be an administrator when i run this game for the first time.

But when i use gksudo nautilus i am unable (with my experience) to access playonlinux so i can run the game the first time as an administrator.

I know there must be a solution out there somewhere :)

No way. There is absolutely no reason or whatsoever for a wine program to require "administrative privileges" under Linux.

You could install the game using gksudo playonlinux, then move the /root/.playonlinux_or_whatever_the_name_of_the_folder_is to /home/your_username, then use chown command to make the files "yours", however, this is way too dangerous and totally necessary.

What drivers is it trying to install exactly and have you searched the playonlinux forums for this particular game?

---

### Post by Amused2Death on 2011-03-14
It doesn't tell me what drivers it wants to install and i dont remember having this problem about 2 years ago when i originally installed it under an early Ubuntu distro.

The game is listed in the playonlinux games menu.

I will check their forums as well :)

Thanks

---

### Post by 3Miro on 2011-03-14
> **Amused2Death said:**
> It doesn't tell me what drivers it wants to install and i dont remember having this problem about 2 years ago when i originally installed it under an early Ubuntu distro.

The game is listed in the playonlinux games menu.

I will check their forums as well :)

Thanks

They probably want to install directx, for which you don't need root. Either that, or I have no clue. Can you post a screenshot where the thing is asking for "privileges"? Or you can also go to a more knowledgeable forum.

---

### Post by blueridgedog on 2011-03-14
See:

[http://wiki.jswindle.com/index.php/General_Wine_Troubleshooting#Administrator_Privileges](http://wiki.jswindle.com/index.php/General_Wine_Troubleshooting#Administrator_Privileges)

Run as win98

---

### Post by Amused2Death on 2011-03-15
Thanks blueridgedog,

this quote from your link answers my question :)

[I]Administrator Privileges

If your application asks for Administrator rights.. File a bug with wine. H. Bostick: Sorry to say that sudo won't help you-- the program is looking for *Windows* Administrator privileges, not Linux root privileges. The cause of this problem is most likely a combination of 2 factors:

   1. The fact that Wine now defaults to 'emulating' Windows 2K by default,rather than Windows 98; and
   2. The fact that many Windows programs of a certain type, when they were updated to work with Win2K from previous compatibility with Win98 (which does not have an Administrator), began to require Administrator privileges under 2K and higher to install. This usually happens with utilities like defrag utilities or other scanners/blockers/repair utils that can be run as a service. This at least makes sense, as in order to run as a service, the application has to hook into the M(icrosoft)M(anagement)C(onsole), which is an Administrator-only system application. But I have, oddly enough, seen programs which would seem to have no use for administrative privileges require them on installation; recent versions of PaintShopPro are one example of this. The 'solution' is to tell the application that it's being installed under Win98 (assuming that the program is willing to install under Win98), rather than 2K. Since as far as I know, there is no implementation of Windows' fairly sorry implementation of user privilege separation in Wine (meaning that, afaik, you cannot become the Windows Administrator under Wine), the only other option is to go back to the 'good old days' where it didn't exist (Win98). 

Try running winecfg (I assume your version of Wine is later than 20050628, and therefore has the winecfg utility replacing the config file), and change your "Windows version" settings on the first tab (Applications) from "Automatically detect required version" to "Win98". If you don't want to change the setting globally, you could also add a per-application default for the setup by (on the same tab), choosing "Add Application", browsing to the setup for the app and selecting the installation executable. [...] (this will likely affect all setup executables with the same name, since the name is likely not unique[/I]

Cheers

---

### Post by 5149.5 on 2011-03-15
> **3Miro said:**
> They probably want to install directx, for which you don't need root. Either that, or I have no clue. Can you post a screenshot where the thing is asking for "privileges"? Or you can also go to a more knowledgeable forum.

Wine already has DiectX included and it should not be loaded even if an app thinks it should be.

---

### Post by Amused2Death on 2011-03-15
FAIL :(

Even making wine config default win98 and reinstalling it istill get the following messages when trying to launch The Witcher for the first time.

About page claims wine is 1.2.2, playonlinux claims wine version 1.3.9. Both claim wine default is windows98.

Wine claims its latest version is 1.3.15 so i am confused.

There could be tears :cry:

---

### Post by 5149.5 on 2011-03-15
I can relate; I tried to get a windows app running in Wine today. It was a simple app that didn't even require installation. I struggled for a while just figuring out where to drop the files. Once I got them there, the exe refused to run. I gave up and scrubbed wine off of my drive.

---

### Post by 3Miro on 2011-03-15
> **5149.5 said:**
> Wine already has DiectX included and it should not be loaded even if an app thinks it should be.

This is both true and false. Wine does have an implementation of DirectX, but it is incomplete and sometimes applications have to install their own versions and/or you have to use winetricks and/or overwrite the wine implementation with native windows .dll files.

Also, running an application with wine is tricky and should be viewed in a case by case basis. If one application is garbage, another one may run flawlessly even if the first one seems simpler.

---

### Post by 3Miro on 2011-03-15
> **Amused2Death said:**
> FAIL :(

Even making wine config default win98 and reinstalling it istill get the following messages when trying to launch The Witcher for the first time.

About page claims wine is 1.2.2, playonlinux claims wine version 1.3.9. Both claim wine default is windows98.

Wine claims its latest version is 1.3.15 so i am confused.

There could be tears :cry:

You are being asked for windows privileges, which is totally unrelated to Linux administration privileges. You should never run wine with Linux administrative privileges.

For The Witcher in particular, here is the winehq entry. WineHQ is THE place for figuring out problems like that. It seems that being asked for administrative privileged is related to DRM. Their advice seems to be to install a no-CD crack.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10468](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10468)

---

### Post by Amused2Death on 2011-03-16
cheers 3Miro,

long work days are making it hard to track down and fix.

---

