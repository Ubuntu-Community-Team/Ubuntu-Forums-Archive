---
title: "Printing to CUPS server via Windows 7"
date: 2011-08-13
forum: General Help
---

### Post by theotheraether on 2011-08-13
Okay I've been scouring the interwebs for an answer here, and so far I've followed every instruction with no luck.

I've got a Lexmark x2500 installed in CUPS - it works and prints locally with some hacked x2600 drivers (see [this]("http://ubuntuforums.org/showthread.php?t=1243920") - it took some modifications because lexmark changed their package structure, but that's another discussion).  So far I've tried to add the printer in Windows 7 with samba and I've had a host of errors there, so I decided to try CUPS ipp.  So far I can connect the printer and everything looks fine, but nothing ever makes it to the CUPS queue.  I am entering the correct URL for the printer when I set it up in Windows.  I read one forum where someone was having this same issue, but all anyone could offer is check the URL - URL <> URI so yeah no help there...

This is what I'm seeing in the logs:
E [13/Aug/2011:14:09:43 -0700] Missing printer-uri, job-uri, or ppd-name attribute!
E [13/Aug/2011:14:09:43 -0700] Returning IPP client-error-bad-request for windows-ext (no URI) from 10.69.81.3
E [13/Aug/2011:14:15:26 -0700] Missing printer-uri, job-uri, or ppd-name attribute!
E [13/Aug/2011:14:15:26 -0700] Returning IPP client-error-bad-request for windows-ext (no URI) from 10.69.81.3

Is IPP just totally borked in Windows or is there something I'm missing in the CUPS config?  All sharing options are enabled and permissions are set to allow my LAN.

Anyway if anyone has any ideas, it'd be much appreciated!  This is a temporary issue anyway...I just need ink for my WiFi printer which works wonderfully with everything...At this point it's really more a matter of wanting to solve the issue or just chalk it up to a horrible IPP implementation in Windows 7.  Has anyone got Windows 7 printing to CUPS?  Again any input would be greatly appreciated!

---

### Post by drdos2006 on 2011-08-13
Yes, I have printing working from Windows 7 through Virtualbox USB connection to Canon iP4300 printer. However, I had to change some settings in Samba with:-
From a terminal...
gedit  /etc/samba/smb.conf
In the PRINTERS section :-
###
   load printers = yes
###;
   printing = cups
###;
   printcap name = cups
###
use client driver = yes

Save and restart samba.  sudo /etc/init.d/smb restart
On the Windows 7 computer, add a printer.

regards

---

### Post by theotheraether on 2011-08-13
Yeah I had previously nuked my RPC experimenting with some other samba stuff..  I deleted /var/lib/samba and reinstalled the samba package and restored the defaults..

FYI a 'net rpc rights grant <Samba-User> SePrintOperatorPrivilege -U <Windows-User>' will allow an XP machine to upload printer drivers along with the write list directive.  [More about that here]("http://wiki.samba.org/index.php/Samba_as_a_print_server") (It's a huge pain, trust me).  Like I said I've nuked my RPC fiddling around with that stuff a couple times now, but I love experimenting so hey.

I stripped the comments out of my smb.conf and backed up the original for reference so it's easier to read and edit:

Note that this machine accesses all it's shared resources on my file server via NFS.  Those resources are also available via samba to the other windows computers and all I want off this thing is its printer.

```

[global]
   workgroup = ZERONULL
   server string = %h server (Samba, Ubuntu)
   wins server = gatekeeper
   dns proxy = no
   name resolve order = lmhosts host wins bcast

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   log level = 3
   debug uid = no

   security = user
   username map = /etc/samba/smbusers
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   map to guest = bad user

   load printers = yes
   printing = cups
   printcap name = cups

   usershare allow guests = no

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   use client driver = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
  comment = Printer Drivers
  path = /var/lib/samba/printers
  browseable = yes
  guest ok = yes
  read only = yes
  write list = @lpadmin


```

It seems to work, but these crappy Lexmark (it's my wife's printer, don't ask...) drivers don't seem to want to communicate (they give a "communication not available" error with a picture of a printer and a computer with red arrows on the usb cable just to be extra helpful).

So all that being said...anyone know if Windows 7 can print directly to CUPS over IPP using the MS Publisher Imagesetter driver or am I beating a dead horse here?

---

### Post by theotheraether on 2011-08-14
Hah!  Got it working. 

Navigate to HKEY_CURRENT_USER\Printers\Settings
Add a DWORD "PreferredConnection" with a value of 0
New printer, network printer, printer isn't listed, etc
[http://ubuntu-server:631/printers/PrinterName](http://ubuntu-server:631/printers/PrinterName) in the location box and use the MS Publisher Imagesetter driver from the Generic category.

Voila!  Native UNIX printing in windows...good bye smbd :popcorn:

Apparently Win7 and Server 2008 default to RPC IPP printing...the PreferredConnection setting reverts it to HTTP!

---

### Post by mickza on 2011-11-22
> **theotheraether said:**
> Navigate to HKEY_CURRENT_USER\Printers\Settings
Add a DWORD "PreferredConnection" with a value of 0
New printer, network printer, printer isn't listed, etc
[http://ubuntu-server:631/printers/PrinterName](http://ubuntu-server:631/printers/PrinterName)

Many thanks :D, I was tearing my hair out trying to print to a Oki B4400 which is no problem to set up on XP. Like you I tried numerous "solutions" with no success (I think I'm still running a pre-SP1 inetpp.dll, must still test this solution on another Win 7 SP1 system).

The MS Publisher Imagesetter driver didn't work for me but the official Oki B4400 Vista/7 driver did the trick.

Tested on CUPS 1.4.2 & 1.4.8

---

