---
title: "Printing from Ubuntu to shared printer on Win 7"
date: 2009-12-30
forum: General Help
---

### Post by jp317 on 2009-12-30
Ubuntu 8.10

I've been using a shared printer on a Windows XP box for quite some time.  Unfortunately, the owner of the XP PC replaced it with a shiny new Windows 7 PC, and now I cannot get Windows to shared the printer.  I've gone through every sharing option I can find on Windows, and modified the Ubuntu printer to reflect the new PC name and share name, but the printer is stubbornly refusing to be shared.

The Ubuntu error is Tree connect failed (NT_STATUS__ACCESS_DENIED).

The old XP box still exists (for a bit) and when I reattach the printer to it, and use the old XP network printer everything works, so it's definitely related to the Windows 7.

Thanks for any ideas.

---

### Post by Fire_Chief on 2009-12-30
There are several things to check in Win7 that could be causing this...

-Windows Firewall (should be off for the local network)
-Sharing settings (found under Network and Sharing center)
-Homegroup settings for sharing (if one was setup)
-Are you using a username/password to connect to the printer? If so, was this account created on the Win7 box just as it was on the XP box?

Cheers!

---

### Post by Morbius1 on 2009-12-30
The first thing I would do is to temporarily disable any firewall you might have on the Win7 machine and see if you can print.

If that doesn't work you could try this:

Open **Terminal**
Type **sudo cp /etc/cups/printers.conf /etc/cups/printers.conf.bak**
[COLOR=Blue]*This will make a backup copy in case it doesn't work*[/COLOR]

Type [B]gksu gedit /etc/cups/printers.conf
[/B]
Look for a line that looks like this:

> DeviceURI smb://Server_Name/Printer_NameAnd change it to this:

> DeviceURI smb://guest@Server_Name/Printer_NameJust add a guest@ in front of the Server name or ip address that you had set up originally.

Save the file, exit gedit, and back in the Terminal:

Type: **sudo service cups restart**

---

### Post by jp317 on 2009-12-31
When I try to add a printer using the Windows printer via Samba, and just click "browse" instead of putting anything in the smb:// box, the workgroup on the Windows 7 machine shows up, but there is nothing shared there.  So, I don't think there is anything I can do on Ubuntu until the Windows share is visible, and I cannot find ANYTHING on the Windows box that indicates that the printer is NOT shared for the workgroup.  So, I'm stuck.

Going through various Windows groups, it appears a fair number of XP users are having the same problem getting to shared printers on a Windows 7 box, so maybe Microsoft has succeeded in making it unbearably complex for everybody.

Thanks for the suggestions- I've tried them, but nothing has changed, so please-- if anyone has managed to get this to work, please tell me how.

Thanks again...

---

### Post by jp317 on 2009-12-31
The culprit was the $%^^%^! Norton 'free trial offer'.  When I shut it down completely, printing worked  as before.  My apologies to you for wasting your time, and to Microsoft for blaming their Windows 7.

Thank you.

---

