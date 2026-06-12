---
title: "ubuntu laptop cannot print on ubuntu server"
date: 2009-09-16
forum: General Help
---

### Post by watsonsun on 2009-09-16
I have a ubuntu 9.04 desktop server with MFC210C printer attached.  I have installed SAMBA software on this.  I have a laptop installed with dual boot ie. Ubuntu 9.04 and Win 7.  On either system on my laptop,  I can access  directories/files from my desktop server. I can print from my laptop when on Win 7.  However, I cannot print when I dual boot to Ubuntu. 

On my SAMBA samba.conf on the desktop server,  I have the following for printers:

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
  printing = cups
   printcap name = cups

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700
   printcap name = /etc/printcap
   print command = /usr/bin/lpr -P%p -r %s
   printing = cups

On my web browser 'http://localhost:631/printers/'
I get this message
**[MFC210]("http://localhost:631/printers/MFC210") "Connection failed: NT_STATUS_BAD_NETWORK_NAME"**

    [URL="http://localhost:631/printers/MFC210"] 
[/URL]  **Description:** MFC210
**Location:** 
**Printer Driver:** Brother MFC-210C CUPS v1.1
**Printer State:** processing, accepting jobs,  published. 
**Device URI:** smb://watson/print/  
I used to be able to print but recently,  it just refused to.  Can someone pse help me.
thanks

---

### Post by watsonsun on 2009-09-17
bump

---

