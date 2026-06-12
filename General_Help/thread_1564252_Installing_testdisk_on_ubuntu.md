---
title: "Installing testdisk on ubuntu"
date: 2010-08-30
forum: General Help
---

### Post by PianoGrand on 2010-08-30
Some background info : When I installed Ubuntu, I installed it over Windows Xp.

I saw a thread on how to use testdisk however it was based on using the program Linux where as I have Ubuntu.

Do the directions for using teskdik for Linux apply for Ubuntu as well?

Question number two, Installing testdisk on ubuntu.
I extracted the contents of the testdisk.rar file onto my computer which currently has ubuntu installed on it however I cannot run testdisk..

It came up with this error message after I tired to run trestdisk.exe.

Archieve: /home/nathan/desktop/testdisk-6.11.3/win/testdisk_win.exe
[/home/nathan/Desktop/testdisk-6.11.3/win/testdisk_win_.exe]
End-of-central-directory signature not found. Either this file is not a zipfile, or it constitutes one disk of a multi-part archive. In the latter case the central directory and zipfile comment will be found on the last disk(s) of this archive.
note: /home/nathan/Desktop/testdisk-6.11.3/win/testdisk_win.exe may be a plain executable, not an archive zipinfo: cannot find zipfile directory in one of /home/nathan/Desktop/testdisk-6.11.3/win/testdisk_win.exe or /home/nathan/Desktop/testdisk-6.11.3/win/testdisk_win.exe.zip, and cannot find /home/nathan/Desktop/testdisk-6.11.3/win/testdisk_win.exe.ZIP, period.


Edit : Also, when I go into my computer on Ubuntu, I cannot see my C:/ drive/ Hard Drive.

---

### Post by hewjr1000 on 2010-08-30
If you have Ubuntu 10.04 installed you can find testdisk in the Ubuntu software center.

Just go to applications>software center>and type in testdisk, then install

---

### Post by PianoGrand on 2010-08-30
lol I just realized what the title of my post is.
Anyway.
I have that version however I cannot find the file in Software Centre??
Also if you can answer this, I tired to install scalpel but I don't have permission it says, can you teach me how to add full administrator capability?

---

### Post by hhoyt on 2010-08-30
Two recommendations:
1) ALWAY backup your data (5 years lost ?)
2) Run testdisk from a standalone utility. My recommendation is PARTED MAGIC. Do NOT run from windows or ubuntu on your H.D. !
[http://partedmagic.com/](http://partedmagic.com/)

Howard

---

### Post by PianoGrand on 2010-08-30
Yes , 5 Years! My computer has never had a problem so I guess I didn't really think about it... until now =3

anyway, can you please elaborate on how to use a standalone utility. Sorry, I'm not that good with computers, mainly use it for media. Please help..

Also can you boot parted magic from an external harddrive/USB?

---

### Post by hhoyt on 2010-08-30
" can you please elaborate on how to use a standalone utility. Sorry, I'm not that good with computers, mainly use it for media. Please help..

Also can you boot parted magic from an external harddrive/USB?"


Sure.
Yes, you want to write parted magic (download the .ISO) to either a USB stick (recommend) or cdrom. 
Another utility called UNETBOOTIN can be a real help. You may find it under SYSTEM TOOLS (will write the ISO directly to your USB stick).
The big picture is you boot your standalone linux utility up off the usb stick or cd and then can access your linux partition--uh, in this case tho, you want to run TESTDISK off the standalone linux utility (parted magic)and access what WAS your Win partition.
Testdisk is great but your data may not be recoverable.

If it was in a separate partition you are probably in good shape.

You might want to peruse:
[http://partedmagic.com/documentation.html](http://partedmagic.com/documentation.html)

Best of luck, Howard

Howard

---

### Post by hhoyt on 2010-08-30
oops, one other note. 
---------------------------
If you can access internet off another pc, I would not use the linux that overlaid windows. 
---------------------------
Certainly no maintenance installs.
Until you have determined whether you can recover your data, you do not want any additional writes to occur in what was the windows partition !

You want to boot up a CD or USB recovery utility that can look at your hard drive w/o any addl changes (writes) to the hard drive...

---

### Post by PianoGrand on 2010-08-30
" can you please elaborate on how to use a standalone utility. Sorry,  I'm not that good with computers, mainly use it for media. Please help..

Also can you boot parted magic from an external harddrive/USB?"


Sure.
Yes, you want to write parted magic (download the .ISO) to either a USB stick (recommend) or cdrom. 
Another utility called UNETBOOTIN can be a real help. You may find it  under SYSTEM TOOLS (will write the ISO directly to your USB stick).
The big picture is you boot your standalone linux utility up off the usb  stick or cd and then can access your linux partition--uh, in this case  tho, you want to run TESTDISK off the standalone linux utility (parted  magic)and access what WAS your Win partition.
Testdisk is great but your data may not be recoverable.

If it was in a separate partition you are probably in good shape.

Wait Howard before you go! I still have a few questions, please if you will take the time, your efforts will be much appreciated.
Firstly, is parted magic my standalone linux utility?
Once I boot the standalone linux utility from my USB stick, do I select TESTDISK after it boots? Or do I have to select it while I'm in the boot menu.

Also, I installed ubuntu OVER windows xp, is there still a chance I can recover data or dose this process eliminate the possibility of any data being recovered.
ALSO do you have a link for TESTDISK in which is compatible with ubuntu version 10.4 I think(latest), I cannot find any. Other than that I think I can find the rest. Thanks so much Howard.

---

### Post by hhoyt on 2010-08-31
"Wait Howard before you go! I still have a few questions, please if you will take the time, your efforts will be much appreciated.
Firstly, is parted magic my standalone linux utility?
"

Also, I installed ubuntu OVER windows xp, is there still a chance I can recover data or dose this process eliminate the possibility of any data being recovered.
ALSO do you have a link for TESTDISK in which is compatible with ubuntu version 10.4 I think(latest), I cannot find any. Other than that I think I can find the rest. "

Yes, standalone as in booted.
Select testdisk after parted magic boots.
This is a standard linux boot, just of parted magic which is a current linux kernel with many utilities.
Well, I am hoping Ubuntu does a quick format. In which case the data (may) be there- certainly not pointed to my the linux tables tho. I really (at a minimum) depends on what Linux overlaid.
Sorry to say this is probably a longshot, but worth trying in the case of 5 yrs of data.

"Once I boot the standalone linux utility from my USB stick, do I select TESTDISK after it boots? Or do I have to select it while I'm in the boot menu."

I think you miss the point, you want to run Testdisk as a standalone (not installed to your disk that you want to scan).
Possibly too late, but you really do not want to download parted magic or anything else to the linux that overlaid windows.

You really DO NOT want to boot up your new linux at all.
Boot up a O/S (like Parted Magic) containing TestDisk from some medium other than the partiton where you are having trouble. Typically USB stick or a CD. 
I would recommend you download Parted Magic on another PC. 

Recommend:

1) Download PM on another pc
2) Using unetbootin write PM to USB (or CD)
3) Boot up PM off the USB stick or CD
4) Now you can select TestDisk utility

ref: [http://www.ultimatebootcd.com/forums/viewtopic.php?t=1833](http://www.ultimatebootcd.com/forums/viewtopic.php?t=1833)

Good luck,

Howard

---

### Post by hhoyt on 2010-08-31
when you boot up parted magic, testdisk is under System Tools.
Also note that chrome browser/internet connect is included in PM, so you can be online whilst things are running. If you already run Chrome, you can even sync with your bookmarks ;-)

In test disk--
Choose CREATE
select your media
Typically your partition table type is the default of INTEL
Now run Analyze. This will take some time.

Here is a detailed step-by-step for you to follow:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Howard

---

