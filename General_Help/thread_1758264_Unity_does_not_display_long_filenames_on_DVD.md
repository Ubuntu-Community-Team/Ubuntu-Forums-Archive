---
title: "Unity does not display long filenames on DVD?"
date: 2011-05-14
forum: General Help
---

### Post by eltonw on 2011-05-14
I made a few data DVD's in OS/X 10.6.7 on my Macbook, using **[COLOR="DarkRed"]Burn[/COLOR]** [http://burn-osx.sourceforge.net]("http://burn-osx.sourceforge.net").
... with the *option* "burn _[COLOR="DarkRed"]for PC and Mac[/COLOR]_"

To my surprise when I load the DVD's in my **ubuntu** netbook, Unity displays the filenames abbreviated and renamed [COLOR="Navy"][U].:confused: Some of the original filenames are similar, but unity restricts the filenames to about 22 ~ 50 characters.

As such, I can't get a true (correct) file listing of the DVD's contents in **Natty**. :?

I don't recall this happening with Karmic. Is this some problem with Nautilus?

**P.S.** FWIW, these were done using double layer 8.5 DVD-R disks. However, [FONT="Georgia"]I did NOT select overburning, so the contents fit well into the allowed capacity, to permit inclusion of any hidden files.[/FONT]

As soon as I load the disks on my Mac, I am able to see the full filename.

---

### Post by TeoBigusGeekus on 2011-05-15
Someone correct me if I'm wrong, but burning your dvd with windows support, limits the filenames to 64 characters - Joliet file system.

---

### Post by eltonw on 2011-05-21
> **TeoBigusGeekus said:**
> Someone correct me if I'm wrong, but burning your dvd with windows support, limits the filenames to 64 characters - Joliet file system.

I selected:: "Burn for PC AND Mac". OS/X is a *nix system, and the long filenames of the DVDs display correctly on my Macbook. It doesn't explain why the names are foreshortened to about 30 characters (maximum) ... even with Joliet [64 characters], the filenames should display correctly in Nautilus, no?

FWIW: Disks were burnt on the Macbook's internal CD/DVD drive, and being read (with names shortened) on an external drive when on the ubuntu netbook. 
Could this be a bug in nautilus?

IIRC, I feel quite certain that I've previously burnt data DVD's on my Mac (OS/X) and have the long names correctly display in ubuntu (Karmic).

... still mystified...:???:

**[COLOR="Red"]ADDENDUM:[/COLOR]**
I have just checked previous Fuji DVD's burnt in the aforementioned manner, and in Natty, they DO display the full long names.

IMPORTANT NOTE: [FONT="Verdana"]The 'problematic' DVD's are Memorex [COLOR="Red"]**8.5 Gb**[/COLOR] rather than standard 4.7 Gb DVD's.[/FONT] On these the filenames are shortened to 26 characters [including spaces] 
Is it possible that Nautilus has a problem _reading long names on higher capacity DVD's_?:confused:

---

### Post by linuxinstalledfromhdd on 2011-05-21
I would try to find a better way to migrate data, like using a file server or even a external hdd that is formatted correctly with linux partitioning and linux formatting.  It should work in a MAC that way with no issues in the future as well.):P

---

### Post by eltonw on 2011-05-21
> **linuxinstalledfromhdd said:**
> I would try to find a better way to migrate data, like using a file server or even a external hdd that is formatted correctly with linux partitioning and linux formatting.  It should work in a MAC that way with no issues in the future as well.):P
While I *appreciate your comment*s,_ it does not help_ me _solve the problem_.](*,) I am using DVD's because 'my pocketbook prohibits the use of other alternatives' 

... *IF you get my drift*...

---

### Post by meloade on 2011-05-21
Use Ubuntu Classic. Problem solved.

---

### Post by eltonw on 2011-05-21
> **meloade said:**
> Use Ubuntu Classic. Problem solved.
Really? ... too bad. I rather like unity. 
I also came across a bug with Nautilus HERE:[https://bugs.launchpad.net/ubuntu/+source/libarchive/+bug/396949]("https://bugs.launchpad.net/ubuntu/+source/libarchive/+bug/396949")

... and **NO**, it still **does*_ not_* work for m**e. I did a soft boot selecting Ubuntu Classic, and the filenames are STILL shortened. 

NOTE: This an EXTERNAL Samsung DVD writer. I downloaded the latest firmware, but I don't have a Windows machine. Would it be possible to do the firmware update under WINE? The drive is powered via its additional USB connection, and is sometimes slow to the 8.5 GB disks... [COLOR="DarkRed"][FONT="Tahoma"]I am wondering if a firmware update might solve this problem.[/FONT][/COLOR]

---

### Post by eltonw on 2011-05-22
**SOLVED:**

Using Burn ver. 2.5.1 (24) [http://burn-osx.sourceforge.net]("http://burn-osx.sourceforge.net"), 
I did a test using an RW DVD in OS/X: 

...burn as:
1) PC + Mac = Result A ](*,)
2) PC (Joliet) = Result A ](*,)
3) Mac (HFS+) = Result A ](*,)
4) **UDF** = Result B 8-)

Result A= Nautilus truncates file names to about 30 characters (including spaces) ](*,)
Result B= _Filenames are correctly displayed *in full*_ 8-)

/REM: [FONT="Verdana"]I am quite sure that previous disks were burnt with the 'PC + Mac" option, and they did display correctly in Nautilus.[/FONT] There is an apparent 'change in policy' and now, _*only*_ **UDF** will properly display long filenames in Nautilus.:confused:

/REM: Apparently, if you create a 'burn folder' in OS/X the *default* is UDF.

Perhaps someone would care to test this with a disk burned under Microsoft Windows?

---

