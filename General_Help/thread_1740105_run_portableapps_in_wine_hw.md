---
title: "run portableapps in wine hw?"
date: 2011-04-26
forum: General Help
---

### Post by ottosykora on 2011-04-26
I am frequent user of portableapps (portableapps.com)

I have all apps on fat32 formated usb stick and I used to run them via wine in ubuntu before.

Since the event of locking all exe out, this is not possible any more. The apps are on fat32 drive, so setting up of rights is not possible.

How can I run them anyway and can something be done as defining at least some certain usb flash drive as being allowed to run exe apps from there?

---

### Post by ottosykora on 2011-04-27
any body with an idea how to run windows apps stored on portable drive?

Works perfect on debian, just not on ubuntu.

---

### Post by fdrake on 2011-04-27
> **ottosykora said:**
> I am frequent user of portableapps (portableapps.com)
Since the event of locking all exe out, this is not possible any more. The apps are on fat32 drive, so setting up of rights is not possible.

How can I run them anyway and can something be done as defining at least some certain usb flash drive as being allowed to run exe apps from there?

if it was possible before it should be even now...! are the exe file executable or not . on the directory where your exe file is locate run this command to see the list of its access.
```

ls -al '/media/your flash driver folder/the path of the directory where the exe files are/'*.exe
```
post here the output

---

### Post by ottosykora on 2011-04-27
well the files are exe (windows executables) and are launchers and will call other executable in most cases.
As they are on fat32 media, no executable rights or similar can be assigned to them. 
From 10.10 running executables can be made only with rights set , but fat32 has no rights at all and so it can not be set.
I thought if there would be away to set the particular usb stick as some kind of exeption and allow to execute files on it.

On 10.04 all works fine still.
On 10.10 such media is considered read only, and no executin rights are granted.

I will post the output of the  ls when at home, but as you will know, on fat32 you will see no rights or anything similar.

---

### Post by Morbius1 on 2011-04-27
Right click an *.exe file and select Properties  -> Open With -> Add -> Use a custom command > type in:  wine

In the "Open With" tab mark the "wine"[COLOR=Black] [COLOR=Blue]you added [/COLOR][/COLOR][COLOR=Blue]as  the default[/COLOR] instead of the Wine that's already selected.

---

### Post by corncob on 2011-04-27
Now that you got me looking, I haven't been able to find a good thread to refer you to but I do recall seeing this advice several times in the past with the result of the OP marking the thread as SOLVED:
> You need to edit /usr/share/applications/wine.desktop and change the line that begins with "Exec=" to "Exec=wine start /unix %f"
It however didn't work for me :(  I do have a couple of portable Windows apps on my desktop running just fine with "open with Wine" and "make this file executable" selected under Properties.  I know you'd rather not go through this but you should be able to run these apps (as well as setup.exe from a CD) by opening a terminal, typing in wine (plus a space) and draging the app into the terminal.  That way the program is an argument for wine and doesn't matter whether or not its executable.

---

### Post by Morbius1 on 2011-04-27
That's another way to do this if you don't want to do it from "Open With":

Open up "Properties" on /usr/share/applications/wine. The first thing you see in the Command Box is "cautious-launcher". Change the command from:
```
cautious-launcher %f wine start /unix
```to
```
wine start /unix
```**[COLOR=Blue]EDIT[/COLOR]:** should have noted that you can only modify the "Command" box if you use nautilus as root:
```
 gksu nautilus
```

---

### Post by Claus7 on 2011-04-27
Hello,

> **ottosykora said:**
> I am frequent user of portableapps (portableapps.com)

I have all apps on fat32 formated usb stick and I used to run them via wine in ubuntu before.

Since the event of locking all exe out, this is not possible any more. The apps are on fat32 drive, so setting up of rights is not possible.

How can I run them anyway and can something be done as defining at least some certain usb flash drive as being allowed to run exe apps from there?

I do not know if this will help, yet, navigate to the folder where the executables are and open them via the command:
```
wine *file_name*.exe (where file_name the name of the file)
```

If this does not work, try to do it as root:
```
sudo wine *file_name*.exe (where file_name the name of the file)
```
and give your password.

Hope it helped,
Regards!

---

### Post by corncob on 2011-04-27
> **Claus7 said:**
> 
I do not know if this will help, yet, navigate to the folder where the executables are and open them via the command:
```
wine *file_name*.exe (where file_name the name of the file)
```

On these long involved paths I prefer to drag the file into the terminal  rather than CD to its directory.  Somebody once told me not to use sudo with wine.  Does anybody remember why?  Usually because it puts things into root's home directory where you don't always want them.

---

### Post by dino99 on 2011-04-27
its time to drop msdos and fatxx into bin :)

---

### Post by jithendra89 on 2011-04-27
open Applications>wine>uninstall wine software> Install
and select files of type as exe then select the app you want to run on the usb stick or what ever the media file is in and open then it will open fine.

---

### Post by corncob on 2011-04-27
> **ottosykora said:**
> well the files are exe (windows executables) and are launchers and will call other executable in most cases.
As they are on fat32 media, no executable rights or similar can be assigned to them. 
From 10.10 running executables can be made only with rights set , but fat32 has no rights at all and so it can not be set.
I thought if there would be away to set the particular usb stick as some kind of exeption and allow to execute files on it.

On 10.04 all works fine still.
On 10.10 such media is considered read only, and no executin rights are granted.

I will post the output of the  ls when at home, but as you will know, on fat32 you will see no rights or anything similar.

So you're saying that you have launchers (shortcuts) on this drive to executables on this same drive?  It looks like you got a lot of good ideas already but -- while we're waiting for you to get back to us -- I was thinking about the possibility of making Linux launchers for these programs -- right click the desktop, select create launcher..  You might have to have wine in the command line.  Maybe the launcher can then be moved to your drive along with your windows shortcuts.  I don't know.  I never tried this.

---

### Post by ottosykora on 2011-04-27
> **Morbius1 said:**
> Right click an *.exe file and select Properties  -> Open With -> Add -> Use a custom command > type in:  wine

In the "Open With" tab mark the "wine"[COLOR=Black] [COLOR=Blue]you added [/COLOR][/COLOR][COLOR=Blue]as  the default[/COLOR] instead of the Wine that's already selected.

that did not work, produces the same as the normal wine starter so far.

---

### Post by ottosykora on 2011-04-27
> **Morbius1 said:**
> That's another way to do this if you don't want to do it from "Open With":

Open up "Properties" on /usr/share/applications/wine. The first thing you see in the Command Box is "cautious-launcher". Change the command from:
```
cautious-launcher %f wine start /unix
```to
```
wine start /unix
```**[COLOR=Blue]EDIT[/COLOR]:** should have noted that you can only modify the "Command" box if you use nautilus as root:
```
 gksu nautilus
```


did not work, as this /usr/share/applications/wine does not seem to exist.

---

### Post by ottosykora on 2011-04-27
> **corncob said:**
> Now that you got me looking, I haven't been able to find a good thread to refer you to but I do recall seeing this advice several times in the past with the result of the OP marking the thread as SOLVED:



I tried to change the line in the wine-dektop, but it di not help . Files still can not be executed. It still tells me that the media is read only and thus not possible to run the executable.

---

### Post by ottosykora on 2011-04-27
>sudo wine file_name.exe (where file_name the name of the file)<

 have tried this too, but no help, ubuntu still insists that the drivei sread only and thus it can not run anything from it.
Tried different usb sticks, same result.
Refuses to run anythnig with wine from fat32 formated drive. 
Works fine on ubuntu 10.04, on 10.10 no luck.

---

### Post by ottosykora on 2011-04-27
> **dino99 said:**
> its time to drop msdos and fatxx into bin :)

well yes, but do you have an alternative? Do you have portable apps for linux? Will they run on different computers? No.

This is why I have those now well known portableapps on my usb stick and so I can carry all my data, my mails my browser and other apps with me without the need of a computer. This is the whole reason for having them.

PortableApps run on any win computer, they run also on any linux with wine, except ubuntu from 10.10 upwards.

---

### Post by ottosykora on 2011-04-27
> **fdrake said:**
> if it was possible before it should be even now...! are the exe file executable or not . on the directory where your exe file is locate run this command to see the list of its access.
```

ls -al '/media/your flash driver folder/the path of the directory where the exe files are/'*.exe
```
post here the output

ok here the output of ls -al

[CODE]
otto@LAPTOPOTTOS6:/media/CORSAIR/PortableApps/ThunderbirdPortable$ ls -al
insgesamt 544
drwx------   5 otto otto  32768 2011-01-06 00:11 .
drwx------ 253 otto otto  32768 2011-01-05 23:37 ..
drwx------   6 otto otto  32768 2011-01-06 00:13 App
drwx------   7 otto otto  32768 2011-01-06 00:11 Data
-rw-r--r--   1 otto otto   8859 2009-03-19 23:52 help.html
drwx------   4 otto otto  32768 2011-01-06 00:13 Other
-rwxr-xr-x   1 otto otto  57335 2009-01-02 04:16 ThunderbirdPortableAddressBook.exe
-rwxr-xr-x   1 otto otto 150064 2010-03-31 06:26 ThunderbirdPortable.exe
-rw-r--r--   1 otto otto 126595 2009-01-02 15:49 ThunderbirdPortable.gnu

---

### Post by 3rdalbum on 2011-04-27
Sir, you've already had the answer to your question.

Open a terminal and type 'wine ', without the quotation marks. After you've typed the space, drag the program into the terminal. Press Enter. The program will run.

---

### Post by ottosykora on 2011-04-27
>I was thinking about the possibility of making Linux launchers for these programs -- right click the desktop, select create launcher.. You might have to have wine in the command line. Maybe the launcher can then be moved to your drive along with your windows shortcuts. I don't know. I never tried this.<

well I say again, those are PortableApps, as per nowdays defacto standard of PortableApps.com and are placed on a usb flash stick with the aim to carry them around and have them ready where ever I am and have not my own computer with it. I use ut for years so. I could make kind of launcher in the current ubuntu, but first it does not work anyway, only on 10.04 or lower, but not on 10.10 or better say the launcher would have to have some special properties probably to allow the start of the exe form an usb stick.
The I would have to make launchers fro all apps on my usb stick (some 90 at time) on all computers I will ever meet...not very realistic.

I have  no idea exactly if there is a way to change the behaviour of current ubuntu backto that of 10.04 or lower. There have been some extra security measures added, which do prevent apparently to run any exe from external drives or so.

---

### Post by ottosykora on 2011-04-27
> **jithendra89 said:**
> open Applications>wine>uninstall wine software> Install
and select files of type as exe then select the app you want to run on the usb stick or what ever the media file is in and open then it will open fine.

ok did unistall of the whole wine and then install again. The only difference is, that in the context menu is written open with wine core, but otherwise same as before.

It looks like I have to live with the situation that ubuntu is no more accepting portableapps, which is very sad as other distros have no problem with it.

---

### Post by 3rdalbum on 2011-04-27
> **3rdalbum said:**
> Sir, you've already had the answer to your question.

Open a terminal and type 'wine ', without the quotation marks. After you've typed the space, drag the program into the terminal. Press Enter. The program will run.

^ **This. Please read it.**

---

### Post by mc4man on 2011-04-27
> It looks like I have to live with the situation that ubuntu is no more accepting portableapps, which is very sad as other distros have no problem with it.
Not sure what you are/have done wrong, all of the suggestions here are valid, some for all instances.

They only thing that prevents a .exe from being executed is the cautious-launcher script - several ways have been posted on how to bypass.

Additionally - when a .exe is placed on a vfat drive and then that drive is mounted, it is marked/seen  as executable 

Ex. screen 1 - an .exe on the desktop
screen 2  - after copying to vfat flash drive, made no changes in permissions

screen 3 - setup portable apps on the drive - they all work w/ the default  otherwise crippled cautious-launcher enabled 'Wine Windows Program Loader'
> :/media/New Volume/PortableApps$ ls -al
total 64
drwx------ 15 doug doug 4096 2011-04-27 02:56 .
drwx------  4 doug doug 4096 2011-04-27 22:57 ..
drwx------  5 doug doug 4096 2011-04-27 02:56 AbiWordPortable
drwx------  5 doug doug 4096 2011-04-27 02:55 ClamWinPortable
drwx------  5 doug doug 4096 2011-04-27 02:55 CoolPlayer+Portable
-rw-r--r--  1 doug doug  165 2009-02-28 19:20 Desktop.ini
drwx------  5 doug doug 4096 2011-04-27 02:56 FirefoxPortable
drwx------  5 doug doug 4096 2011-04-27 02:55 KeePassPortable
drwx------  5 doug doug 4096 2011-04-27 02:55 Mines-PerfectPortable
drwx------  5 doug doug 4096 2011-04-27 02:55 PidginPortable
drwx------  4 doug doug 4096 2011-04-27 02:55 PNotesPortable
drwx------  5 doug doug 4096 2011-04-27 02:55 PortableApps.com
drwx------  5 doug doug 4096 2011-04-27 02:55 SudokuPortable
drwx------  5 doug doug 4096 2011-04-27 02:55 SumatraPDFPortable
drwx------  5 doug doug 4096 2011-04-27 02:56 SunbirdPortable
drwx------  4 doug doug 4096 2011-04-27 02:56 ThunderbirdPortable

What does /etc/mtab show after mounting your drive?

---

### Post by ottosykora on 2011-04-28
>Open a terminal and type 'wine ', without the quotation marks. After you've typed the space, drag the program into the terminal. Press Enter. The program will run.<

no, does not

---

### Post by ottosykora on 2011-04-28
ok , mc4man

will try again later have to hurry to work now, but at least someone here who knows what I am talking abt ;-) ( portableapps )

---

### Post by Morbius1 on 2011-04-28
Is this a possibility?
> **gc2712 said:**
> Many thanks Morbius1 for your follow up. I tried  your last solution - still no go. But I then discovered the cause of the  problem. I tried running other *.exe programs from the same external  drive and they worked! It turns out that I had installed a beta version  of Portable Apps which works in Windows, but not in wine. (I had  forgotten I installed a beta). So I reinstalled the stable version and  lo! It all works as expected.

I am grateful for the solution to the nagging about "executable bit"  that has arisen in recent versions of Ubuntu. Making that change to the  wine loader properties was really worth it. Sorry about the 'red  herring' chase though from my incorrect diagnosis. Help of everyone  greatly appreciated.

---

### Post by 3rdalbum on 2011-04-28
> **ottosykora said:**
> >Open a terminal and type 'wine ', without the quotation marks. After you've typed the space, drag the program into the terminal. Press Enter. The program will run.<

no, does not

If that doesn't work, then the program does not work in Wine. Not all programs are compatible, you know.

---

### Post by ottosykora on 2011-04-29
Ok just quickly here again.

The program, and any other on my usb stick , do work in wine indeed, but only on versions up to 10.04.
From 10.10, nothing works.
I have no ptoblems running the same app from the same stick on my old dell with ubuntu 10.04.

Inserting it to any of my 3 10.10 installation fails to run anything.

I read here something abt setting the excutable bit, well how is this done for whole drive?
The problem is, that portableapps are started by a launcher which is exe by itself and it calls up the actual app which is then an exe again.

---

### Post by mc4man on 2011-04-29
I don't think this has anything to do with the exec. bit - your post with the ls -al shows it being set (as should all .exe's on vfat drives

> started by a launcher which is exe
Right click on that .exe > properties > permissions, I'll bet it is shown as executable.
(if not then copy to desktop, delete from drive, copy it back and it will

Why don't you try creating a new pa flash drive setup from 10.10?

---

### Post by Morbius1 on 2011-04-29
From one of your earlier posts:
> /usr/share/applications/wine does not seem to existFrom [http://packages.ubuntu.com/maverick/i386/wine1.2/filelist](http://packages.ubuntu.com/maverick/i386/wine1.2/filelist) :

> /usr/share/applications/wine-browsedrive.desktop
/usr/share/applications/wine-notepad.desktop
/usr/share/applications/wine-uninstaller.desktop
/usr/share/applications/wine-winecfg.desktop
[COLOR=Blue]**/usr/share/applications/wine.desktop**[/COLOR]For reasons that have never been explained to me coherently, Nautilus will not show the file extension ".desktop" so it should just show "wine".

If it's not there then I'm thinking that wine is not installed correctly. I suppose you've already tried reinstalling it?

---

### Post by corncob on 2011-04-29
There is so much good info in this thread that I'm going to save the link to it.  Maybe it would help if you told us what some of these portable apps are (not all 90 but a couple to make sure we have the right picture).  10.04 will be supported for another two years so there's no hurry to switch from it if its working for you.

---

### Post by ottosykora on 2011-04-30
Oh well, many apps from the [www.portableapps.com](www.portableapps.com) and few others more.

Basic ThunderbirdPortable, Browsers like Opera and Firefox portable, some graphic editors, libre office, some pdf utils , and many others. They are all portabilized, that means they run in themselves, something like an old dos exe or so.
I have some 90plus apps on my stick. The apps are actually tested on wine prior release, so yes they work on it.
As I say, they work on my 10.04, they work on my old debian leny, and also on old fedora 12.
Refuse to run on 10.10 so far.
I tried all the 'tricks' in this thread, but somehow no luck. Have no idea, just some other user of the portable apps complained also some problems.

---

