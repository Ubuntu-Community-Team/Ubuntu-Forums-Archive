---
title: "How to create a WINE shortcut for a Windows program"
date: 2009-07-20
forum: General Help
---

### Post by dkolars on 2009-07-20
Hi -- fairly new to Ubuntu, like 3 weeks... have figured out a LOT of stuff already (I was an NT support person when I worked for a living)...  BUT...  I can't get WINE to create a valid shortcut for my Eudora e-mail program... I need to keep the Win version as I have about 1200 addresses, filters for indiv. mailboxes, nicknames for addressing e-mails, etc. etc. and nothing will import all of those.

So, I can browse my C: drive (Ubuntu has named that 'HD 1'), find my Eudora sub-directory, Eudora.exe, and WINE will run the program perfectly, showing ALL of my info, just as if I were in Windoze...

I have tried from about 3-4 directions to create a clickable link to start the program, and nothing seems to work...

I usually get the message that the path specified in the DEudora.ini file does not exist... I've changed the path to reflect what I think is reality, but Ubuntu doesn't agree...

Any tips on how to create a working WINE shortcut to a Windows program?

My directory structures appears to be "/media/HD 1/Eudora/Eudora.exe"... I've tried making the shortcut be wine "/media/HD 1/Eudora/Eudora.exe", etc.  I've perused dozens of forum postings and found what purported to be fixes, but nuttin' works...

Thanks in advance!  dk

---

### Post by fragos on 2009-07-20
Right click a Windows .EXE file and select Properties and the "Open With" tab. Click the "+Add" button and select "Wine Windows Program Loader" from the list. Now Wine will be the default application for all .EXE binaries.

---

### Post by michy99 on 2009-07-20
A couple of questions.

What exactly is it you mean by "a clickable link to start the program"? Do you want an icon on your desktop that you can double-click to launch the program?

Is your HD 1 drive automatically mounted when you boot into Ubuntu? That is, is there an entry for it in your /etc/fstab file?

---

### Post by dkolars on 2009-07-20
Thanks... the "Open with WINE..." is already there... so, I can go into the directory and double-click the .exe file and it will open.

But, I'd like either a shortcut on the desktop or a link under the "Programs" under WINE in the Applications link on the bar...  That's what I can't get to work...

As to the mounting of the disks... when I first installed Ubuntu, it mounted the drives automatically... after being gone for a long weekend, when I fired up the system this a.m., the HD 1 (old Win C: drive) and HD 2 (2nd internal drive) did NOT mount automatically... I had to open the "Computer" icon I'd created on the desktop and click "Mount drive" on each one...

Haven't worried about that yet... still figuring out what programs I ~really~ do need and whether they'll work in Linux...  Haven't tried my scanner yet, burning CD's/DVD's, Cool Edit audio edit, etc....  Slowly, but slowly...

---

### Post by michy99 on 2009-07-20
Setting up a desktop launcher should be easy, but it won't work unless the disk is mounted, so you have to mount the disk before using it , or set up the disk to mount automatically.

Right-click on the desktop and select 'Create Launcher.'

For Name put Eudora

For Command put ```
wine /media/HD\ 1/Eudora/Eudora.exe
```

Click OK

Try it and see if it works.

---

### Post by CatKiller on 2009-07-20
Launchers are [.desktop files]("http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec"). Having created your skeleton launcher with the icon that you want and a command that's something like ```
wine "C:\\Eudora\\Eudora.exe"
``` (provided that you've got **winecfg** using your /media/HD 1 drive as C:) you can edit this file to put in entries that aren't included by default, such as a Path key, by dragging-and-dropping the launcher onto a text editor (since the file manager has trouble interpreting that you would want to do anything with a launcher other than launching it). If you haven't got Wine's pretend C: drive set to be your actual Windows partition, you could use ```
wine /media/HD\ 1/Eudora/Eudora.exe
``` I don't know how Wine would describe the program's path to the program itself in that situation, which might be where the problem with Eudora's .ini file comes from.

---

### Post by dkolars on 2009-07-21
The disk is mounted... and, I tried the "wine /media/HD\ 1/Eudora/Eudora.exe", but that gave the same error message:

"The directory specified in the DataFolder entry of the DEudora.ini file:
/home/dkolars/ALLDATA/Eudora/dkolars/
doesn't exist or is not writeable."

I've got all my mailboxes, etc. in that directory -- I copied them over from my Win C: drive as Ubuntu couldn't find them on HD 1 -- The .ini file points to the right location, at least as it shows up in GNOME Commander.

So, I'm wondering if Ubuntu has a different path designation for the "/home/dkolars" directory?

Since I can't see any drive designation for the root drive, I don't really know what the path would look like...  I open "Computer" and I see all my drives: HDD, DVD, USB, etc. and the Ubuntu partition is designated as "Filesystem"... does this need to be specified in the path somewhere?

Pain in keester!!:confused:

---

### Post by nikhilk on 2009-07-21
Just try this from the terminal and let us know if it works
```
cd /media/HD\ 1/Eudora/
wine Eudora.exe
```
In that case instead of an application link put the above two commands in a bash script on your desktop. Then use this wrapper script as youe Eudora launcher. Or you can keep this script some where else and create desktop link to this script.

---

### Post by CatKiller on 2009-07-21
> **dkolars said:**
>  "The directory specified in the DataFolder entry of the DEudora.ini file:
/home/dkolars/ALLDATA/Eudora/dkolars/
doesn't exist or is not writeable."

Windows doesn't use UNIX-style paths. You could try changing that .ini file entry to Z:\home\dkolars\ALLDATA\Eudora\dkolars\

---

### Post by dkolars on 2009-07-21
Well, the terminal input did indeed open the program properly, but left this at the terminal window (I've removed most of the "0 0 0 0..." stuff that was after every header):
0 0 0 0 0 0 0 0 0 0
month
                year=0 0 0 0 0 0 0 0 0 0 0 0
year
year
            total=0
total
total
        whiteList
            current
                day=0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
day
                week=0 0 0 0 0 0 0
week
                month=0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
month
                year=0 0 0 0 0 0 0 0 0 0 0 0
year
year
            previous
                day=0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
day
                week=0 0 0 0 0 0 0
week
                month=0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
month
                year=0 0 0 0 0 0 0 0 0 0 0 0
year
year
            averageSum
        falsePositives
            averageSum
        falseNegatives
            averageSum
        falseWhiteList
            averageSum
        receivedAttachments
            averageSum
        sentAttachments
            averageSum
        readMessages
            averageSum
        forwardMessages
            current
                day=5
<snip> MUCH more </snip>
not well-formed (invalid token) at line 383
junk after document element at line 19
fixme:vxd:VXD_Open Unknown/unsupported VxD L"ifsmon.vxd". Try setting Windows version to 'nt40' or 'win31'.
not well-formed (invalid token) at line 41
err:module:import_dll Library MFC42.DLL (which is needed by L"F:\\media\\HD 1\\Eudora\\Plugins\\Sort32.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"F:\\media\\HD 1\\Eudora\\Plugins\\Unwrap32.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"F:\\media\\HD 1\\Eudora\\Plugins\\UprLwr32.dll") not found
err:statusbar:StatusWindowProc unknown msg 0530 wp=0000 lp=00000000
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:file:ReplaceFileW Ignoring flags 3
fixme:file:ReplaceFileW Ignoring flags 3


Then, the terminal window would not close except by the drop-down command, which killed the process that was running, namely Eudora...  Don't think that's gonna work :-)  

So, I copied the entire Eudora directory to my /home/dkolars/ directory, changed the path in the .ini file, and still receive the message that it can't find the path... doesn't matter which way the / or \ face, nuttin' works...

Also, can't drag a link from the .exe file to the desktop, but can drag one to the program bar, but it generates the error message...

So, guess, for now, I'll continue to simply dig down to the .exe file on the drive, and click on that...  at least that works!!!

---

### Post by todak on 2009-07-21
If you installed Eudora via Wine, then there should be a menu entry in **Applications> Wine> Programs**. If so, then drill down to the menu listing for Eudora, right-click and choose **Add this launcher to desktop** and a shortcut will be created on your desktop. The same applies for any menu item.

---

### Post by jerome1232 on 2009-07-21
Sounds like you'll need to create a small launcher script

I'd put it in ~/bin, if that doesn't exist already create it. Then open gedit.
```
mkdir ~/bin
gedit ~/bin/eudora.sh
```

put this in there, then save the file
```
#!/bin/bash
cd /media/HD\ 1/Eudora/
wine Eudora.exe
```

Make it executable
```
chmod a+x ~/bin/eudora.sh
```

Then make a launcher with a launch command of "eudora.sh" It should work.

---

### Post by dkolars on 2009-07-21
Eudora 7.01 installed via Win XP Home...

Tried the .sh script... can't put it in ~/bin -- access denied, and doesn't show up as even there when I click "Save As..."

So, just put it in my /home/dkolars subdir...  ran the chmod and got:

"dkolars@Desktop:~$ chmod a+x ~/eudora.sh
chmod: cannot access `/home/dkolars/eudora.sh': No such file or directory"

But, eudora.sh IS in the /home/dkolars directory.

So, a brick wall again...

---

### Post by jerome1232 on 2009-07-21
access denied... in your users home folder? That shouldn't be...

What does ls -l show

```
ls -ld ~/bin
```

edit: after creating ~/bin you may need to logout then log back in for it to be in your $PATH and the script to work.

---

### Post by dkolars on 2009-07-21
Well, I get this:
dkolars@Desktop:~$ ls -ld ~/bin
ls: cannot access /home/dkolars/bin: No such file or directory

dkolars@Desktop:~$ ls -ld /bin
drwxr-xr-x 2 root root 4096 2009-07-14 01:42 /bin

As I said, I've been using Ubuntu for not even 3 weeks... so, I'm not at all sure of the meaning of the result!  As well as not knowing any of the basic terminal commands... I used DOS 2.1 up thru 6.0, then Win 3.1 came along and command line living kinda disappeared from my life...  Just trying to get things working well enuf to use right now...  I'll probably have to life with Windows some of the time, as several of my Win programs don't run on Linux:  Street Atlass 2008, Cool Edit, etc.

One thing that i've thought of is finding a way to re-name the HDD's on the system...  Ubuntu calls them HD 1, HD 2, and FreeAgent Drive...  I know that, in reality, HD 2 is now H:... it's my 2nd internal drive, and was F: under Windows...  HD 1 should be C:?  And my FreeAgent external used to be H:... no idea what it might be now...

I get the feeling that Linux doesn't like the space in the name...???

---

### Post by jerome1232 on 2009-07-21
Ahhh you forgot to create the directory. Btw the tilde symbol (~) means /home/yourusername, so ~/bin = /home/yourusernamehere/bin, very different from /bin.


So just go back to my post and start from the first spot which creates the directory (the mkdir command) and you should be golden.

---

### Post by dkolars on 2009-07-21
OK... making a bit more sense now... And, hooray, it worked!!!  Oh frabjous day, calloh, callay...  I did have to browse to the file to get the right path in, but I now have a working shortcut!  Thanks so much...:popcorn::KS:D:P:KS:popcorn:

---

### Post by jerome1232 on 2009-07-21
> **dkolars said:**
> 
One thing that i've thought of is finding a way to re-name the HDD's on the system...  Ubuntu calls them HD 1, HD 2, and FreeAgent Drive...  I know that, in reality, HD 2 is now H:... it's my 2nd internal drive, and was F: under Windows...  HD 1 should be C:?  And my FreeAgent external used to be H:... no idea what it might be now...

I get the feeling that Linux doesn't like the space in the name...???

Linux and Windows use very different Methods to name drives. Windows assigns each partition a different Drive letter. Linux assigns them mount points, which are essentially folders in the file system. The automounter will name partitions if they have a file system label, in your case your drives were named HD 1, HD 2, and FreeAgent Drive. It also mounts them to /media/drivelabel, if no drive label it will just label it by volume size. 

You can change the file system labels if you want. here's a little how to about it.
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by dkolars on 2009-07-22
Thanks... while driving home this a.m., it suddenly hit me that this was the case... the drive is not named "HD 1"... it's identified as a Hard Drive (HD), as since it's the 1st one, it's #1...  Yep, a tad different than Windoze!!  Thanks....:)

---

