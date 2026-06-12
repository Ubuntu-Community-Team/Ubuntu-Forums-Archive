---
title: "Wine Application installation"
date: 2006-04-24
forum: General Help
---

### Post by tamarku on 2006-04-24
OK, I'm still considering myself a nOOb, I have finally made the jump to 100% Ubuntu because out of all the Distro's I've tried I like Ubuntu the most.  BUT, I have been really struggling on learning this WINE thing.  I would like to be able to still run WORD and EXCEL, for work purposes.  Plus, there are some news websites that have embedded video that I would like to be able to still view.  Everything I have read on WINE is that you start 'winecfg' and find the .exe you want to run.  I do not find the .exe files for Word, Excel, or Internet Explorer5.5 or 6 whichever.  How do I get these applications into Wine????  I've downloaded a tar.gz of winetools file and extracted it into a TEMP folder but now I don't know what to do with it.   I searched for wine-utils in synaptic and made sure I had the repository but synaptic didn't find this.  So can someone hold my hand and talk me through getting the .exe files for these applications?  I would greatly appreciate any and all help I can get.  I've tried, honestly, I have googled and searched everything and still can't seem to find the plain english I must need. 

:confused:

---

### Post by hezral on 2006-04-24
wine only provides the layer for windows emulation. the programs you said needs to be installed thru wine. so basically wine doesnt install Word or Excel or Internet Explorer. try checking this website [http://frankscorner.org/index.php](http://frankscorner.org/index.php)

---

### Post by tamarku on 2006-04-24
This has gotten me closer.  BUT now when I type 'wine IEXPLORE.EXE' I see my screen flash then nothing.  Here is the output: 

fixme:shdocvw:IEWinMain "" 1
fixme:shdocvw:iecs_QueryInterface unknown interface {00020400-0000-0000-c000-000000000046}
fixme:shdocvw:iecs_QueryInterface unknown interface {9c2cad80-3424-11cf-b670-00aa004cd6d8}
fixme:shdocvw:is_CanInPlaceActivate
fixme:shdocvw:is_OnUIActivate

Any ideas on this? 

Thanks for the quick response.

---

### Post by hezral on 2006-04-25
im not sure about that. maybe you could check this thread [http://www.ubuntuforums.org/showthread.php?t=149585&highlight=howto+setup+wine](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=howto+setup+wine)

---

### Post by tamarku on 2006-04-25
OK, I'll check that out. Thanks for your help.

---

### Post by justleen on 2006-04-25
check out the [ap DB on winehq.com]("http://appdb.winehq.org/appview.php?versionId=8"), they have some info how to run the apps under when therer too

---

