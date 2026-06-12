---
title: "How Do I &quot;Publish&quot; A Printer?"
date: 2011-05-07
forum: General Help
---

### Post by stevedude on 2011-05-07
Upgrading to Natty from Maverick broke ,among other things, my ability to print. I have a Brother HL-2140 laserjet printer that is shared from a Windows 7 Professional Desktop.

I cannot see the printer listed from my Windows 7 desktop PC. If I go to Add Printer>Network Printer>Windows Printer via SAMBA then Browse, the workgroup we have is shown in the list, but not the printer itself. All was fine in Maverick.

So I setup the printer using the Printer Setup, but using "Other" and entering the device URI [smb://MyWorkgroup/MyDesktopName/Brother%20HL-2140]. I tried to print a test page, but got an error that stated: 
"Connection failed: NT_STATUS_BAD_NETWORK_NAME"

Now if I Right-click on the printer icon and go to "Properties" then
"Policies", I see that there is a message that states "Not Published
 - See Server Settings"

I've tried to use [http://localhost:631](http://localhost:631) to access the CUPS configuration &
publish the server, but I don't see that anywhere and I am at a loss to 
solve this.


** EDIT **
I feel like an idiot!  With the new GlobalMenu in Natty, if you open up "Printers", a window appears showing any connected printers, but if you place your mouse in the upper-left corner next to the Ubuntu symbol, the Printing Menu appears and "Server" is one of your choices. From there you can edit the settings to Publish the printer.  

Now that I've published the printer, and rebooted, it still does not show the printer that is shared on my Windows 7 system so I can access it in Ubuntu. Can anyone help?

---

### Post by Bobby Infinity on 2011-12-13
Don't feel like an idiot; if it wasn't for this post I'd still be banging my head against the wall trying to figure out where to to change server settings. Thank you very much sir.

---

### Post by zero298 on 2012-01-02
Wow, thank you so much.  Totally missed that when trying to configure.

---

### Post by kgr132 on 2012-12-10
Ditto. I missed this completely. Upgrading from 11.10 to 12.10 un-published my previously published printer and I couldn't remember what I done in the first place when I set up the share. Thanks.

---

### Post by Sef on 2012-12-10
Closed. Necromancing. Please start a new thread instead of posting to the old one, if the thread is around a year old.

---

