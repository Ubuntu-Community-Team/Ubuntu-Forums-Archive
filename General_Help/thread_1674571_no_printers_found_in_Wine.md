---
title: "no printers found in Wine"
date: 2011-01-24
forum: General Help
---

### Post by DatBugler on 2011-01-24
I am unable to print from Wine applications (including Notepad) because Wine thinks I have no printers installed. I have a network printer and print-to-file both working fine in normal KDE applications. I did some looking around and found the following:
[LIST]
[*][http://www.witch.westfalen.de/Wine-HOWTO/wineprintconfig.html](http://www.witch.westfalen.de/Wine-HOWTO/wineprintconfig.html)
This is very old, and probably very out of date. I also had trouble following the examples. In any case I don't have anything called *winerc* or *wine.conf*. I just have a *.wine* directory.
[*]Supposedly I should have registry keys for printers in Wine, so I looked where those are supposed to be. I have two keys in *HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Print\Printers*: *(Default)* and *DefaultSpoolDirectory*. Perhaps if I added the right key here I could get Wine to notice CUPS? I wouldn't begin to know what to put though.
[*][http://www.winehq.org/docs/wineusr-guide/misc-things-to-configure](http://www.winehq.org/docs/wineusr-guide/misc-things-to-configure) claims that Wine should "just work" with CUPS. So much for that. It also says that if it doesn't work with CUPS it falls back to look in */etc/printcap*. I have one of those, but it doesn't contain anything except the default comment telling me not to edit the file. Maybe if there's a way to regenerate */etc/printcap* to contain the printers that show up in KDE, Wine would notice. Again, I have no clue how to do that.
[/LIST]
I'm running Kubuntu 10.10 x64, and I'm using Wine 1.2, not Wine 1.0. All my packages are completely up to date.

Any help would be most appreciated. The most important program I use for work is in Wine (Finale 2009), and I don't have an easily accessible non-Linux system to use for printing. The sooner I can get this up and running, the better.

---

### Post by rvchari on 2011-01-24
i m using wine 1.2 and i just copied and pasted the contents of ur msg on to notepad after opening in wine and i could print with a breeze...
just check if wine-printer is set. i am also using network printer, hplaserjet 1020. this is for ur info. i ll check out for further details and post you

---

### Post by rvchari on 2011-01-24
in your wine program, when u issue print command, do u get the window displaying the available printers ? i get my hp1020 and the other option of print to file.

if not then try to re-install the printer on ubuntu and re-run wine to see if u get the printer listed

---

### Post by DatBugler on 2011-01-25
Never go for the simple solution when you can make it complicated! I stupidly had forgotten that I'd set my printer to use postscript instead of CUPS.

---

### Post by rvchari on 2011-01-25
hahaha, good that ur problem is solved....
happy ubuntu ing and... wining !!!:popcorn:

---

