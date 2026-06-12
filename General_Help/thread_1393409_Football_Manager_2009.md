---
title: "Football Manager 2009"
date: 2010-01-29
forum: General Help
---

### Post by sam_robbo on 2010-01-29
hi,

 im relatively new to linux and was wondering whether anyone could give me a step by step guide on how to get fm 09 working on ubuntu 9.10

Thanks

---

### Post by c0mput3r_n3rD on 2010-01-29
Is this a microsoft game or application?  If so check out wine.

---

### Post by realzippy on 2010-01-29
It seems to run on wine:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14555&iTestingId=33763](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14555&iTestingId=33763)  :

How to throw away your social life...

Installation:
Use Steam (see instructions for installing Steam on wine) - you can insert your CD key from retail versions to download and install via Steam.

You must have directx9, dotnet20 and msxml3 installed to run FM2009, these can all be installed with winetricks.

Activation:
Download the fixed activator ([http://www.footballmanager.com/fixv2.zip](http://www.footballmanager.com/fixv2.zip)), run the program to extract activator.exe over the one at (default) ~/.wine/drive_c/"Program Files"/Steam/steamapps/common/"football manager 2009"/activator.exe.

Run the new activator from the command line as follows:
wine ~/.wine/drive_c/"Program Files"/Steam/steamapps/common/"football manager 2009"/activator.exe -activate ufhw8eff89ff0nwf08ww

Where ufhw8eff89ff0nwf08ww is the key printed on your manual (if you bought the game through Steam, right click it in My Games and click 'Show CD key' - do NOT paste directly from here, it will not work in uppercase)

Make sure your CD key is all lowercase, and watch out for 1's that look like l's, or o's that look like 0's (use [http://keycheck.fm2009.softanchorinsight.com/](http://keycheck.fm2009.softanchorinsight.com/) to check your key).

You should now be able to launch the game via Steam. I'll be testing Network mode later and will report back with my findings.

If for some reason it doesn't work, please check ~/.wine/drive_c/windows/profiles/"All Users"/"Application Data"/"Sports Interactive"/"Football Manager 2009 Certificate"/HttpCheck.log and make sure that the end reads something like:

SI Activator: Activation succeeded
Activation reads success.

kEvalTestNumComponents: 1
kEvalTestMatches: 1
kEvalTestTier1Matches: 1
kEvalTestMismatches: 1
kEvalTestInvalidItems: 1
kEvalTestNonces: 1
kEvalTestTier2Matches: 1
kEvalTestNonceDiffs: 1
License reads success.
License key: YOUR_CD_KEY 

see also:

[http://ubuntuforums.org/showthread.php?t=967618](http://ubuntuforums.org/showthread.php?t=967618)

but,you have to read a little,since it is not only running the setup.exe....

---

### Post by MelDJ on 2010-01-29
you would WINE, a compatibility layer to run windows programs, to be able to run it.
see: [http://www.winehq.org/](http://www.winehq.org/)

---

