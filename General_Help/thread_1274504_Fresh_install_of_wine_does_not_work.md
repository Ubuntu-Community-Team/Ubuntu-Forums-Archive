---
title: "Fresh install of wine does not work"
date: 2009-09-24
forum: General Help
---

### Post by hwttdz on 2009-09-24
I purged wine, wine-gecko, and winbind, removed my ~/.wine, reinstalled wine and tried opening up internet explorer and I get a whole bunch of errors, and no internet explorer.  What should I be trying here?

```
> wine iexplore.exe 

fixme:ole:CoResumeClassObjects stub
fixme:shdocvw:go_home stub
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d2929e8, overlapped 0x7d2929cc): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x101ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12fadc)->((null) 1 0x32f19c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->((null) 25 2 0x32f1b0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->((null) 26 2 0x32f1b0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12fadc)->(0x32f1ec)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32f2c0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f350)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->((null) 29 2 0x32fca0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12fadc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32fbe8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32fbe8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->((null) 26 2 0x32fc80 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->((null) 29 2 0x32fc90 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->((null) 28 2 0x32fbe8 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12fadc)->(0x32fb2c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12fadc)->(0xf7de9db5)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->((null) 25 2 0x32fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->((null) 26 2 0x32fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fadc)->((null) 21 2 (nil) (nil))

```

---

### Post by c0mput3r_n3rD on 2009-09-24
try a:
```

sudo apt-get remove wine

```
 
then:
```

sudo apt-get install wine

```

---

### Post by hwttdz on 2009-09-24
So purge is actually stronger than remove, removing any associated files as well.  So purging and reinstalling (which is what I did), did not work.  It's safe to assume that remove and install would not work.

---

### Post by MTGap on 2009-09-24
Have you tried any other windows applications, and what version are you using.

---

### Post by mrjerryk on 2009-09-24
Have you updated your sources.list to add the winehq repository?

For Ubuntu Jaunty (9.04):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"

For Ubuntu Intrepid (8.10):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

For Ubuntu Hardy (8.04):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"

```
sudo gedit /etc/apt/sources.list
```

Then add one of the above depending on which flavor of Ubuntu you are running


```
sudo apt-get remove wine
```

```
sudo apt-get install wine
```

This worked for me.

---

### Post by hwttdz on 2009-09-24
Tried both ubuntu repo 1.0 I believe, and wine repo 1.1.29? Don't have access to the machine at the moment so can't be entirely sure there.  

IE didn't work at all (which is what I was using it for).  Notepad gave no errors, I was able to install firefox, which worked (was even usable), but gave a bunch of errors.  Was planning on testing a few other programs, but I don't feel like I would be giving anything a fair test if IE isn't working.

Also, it's nice that it worked for you, but I've already given that not only did a remove reinstall not work, but neither did a purge, rm -rf .wine, reinstall.

---

### Post by mc4man on 2009-09-24
> IE didn't work at all (which is what I was using it for)

Does this mean 'why you installed wine' or does it mean 'at one point I had a working IE thru wine'?

While possibly something has changed in wine,( I only use it for 2 unrelated progs), from what I see there is and never has been a working real IE in wine, you need to install it. ( and do several other things if you want it to actually run

---

### Post by hwttdz on 2009-09-24
So I was planning on using IE and testing wine with a few programs.  I thought I remember using i.e. before, but it is possible I jumped through all the hoops to get it working.

---

### Post by haveaswiss on 2009-09-24
Yeah... on my fresh install of wine, IE doesn't work either. :(

---

### Post by mc4man on 2009-09-24
There are probably dozens of pages on ie in wine, ie6 or ie7
A few
[http://wiki.winehq.org/FAQ#head-987c38148f3068191d3cc922d5cf6310c547c5aa](http://wiki.winehq.org/FAQ#head-987c38148f3068191d3cc922d5cf6310c547c5aa)

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

[http://wine-review.blogspot.com/2009/02/ie-7-on-linux-with-wine.html](http://wine-review.blogspot.com/2009/02/ie-7-on-linux-with-wine.html)

not so positive rating from appdb

[http://appdb.winehq.org/appview.php?versionId=469](http://appdb.winehq.org/appview.php?versionId=469)

Alt.
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

ect. ect

---

### Post by hwttdz on 2009-09-24
Yup, I got a sort of haltingly working version of ie6, but I think I surrender, maybe I'll try again in 6 months.

---

