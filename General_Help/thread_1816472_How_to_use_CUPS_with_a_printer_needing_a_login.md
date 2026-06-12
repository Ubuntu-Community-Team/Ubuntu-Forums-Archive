---
title: "How to use CUPS with a printer needing a login?"
date: 2011-08-02
forum: General Help
---

### Post by AussieGuy on 2011-08-02
My work has switched to Fuji Xerox printers, which up to today I've been able to print to simply by sending a PostScript file to their IP addresses.  But as of today printing requires a login.  Here are the (Windows) instructions:

"Start>Settings>Printers and Faxes>R-Click on the printer>Properties>Configuration>Accounting>Change the dropdown box “Use Login Name”  to “Enter owner name”>Type in your staff ID number in the User ID box e.g. “e*******”>OK>Apply"

All very nice, I'm sure - but how do I apply this to CUPS?  Where can I find an owner name in CUPS?

Thanks very much,
Alasdair

---

### Post by zero2xiii on 2011-08-06
A printer (as far as I know) never requier a username with a password, only the password, thus only supply the "Staff ID" as password or equivalent.

---

### Post by tora201 on 2012-04-17
I am also lost on this one. Work requires us to use our office phone numbers as ID when printing over the network to the Xerox Docucentre cs5400. (So they can track how many copies we are printing).

In windows there is an option in the Xerox drivers under "configuration" that allows one to enter the phone number ID.

configuration -> "enable account setup" --> account mode =user

Default user settings
specify job owner name 
Job owner name = 7289    <-- my office number

So how do I set this up in CUPS? Without it, I'm unable to print to the network printer.

---

### Post by chugtairizwan on 2012-04-17
CUPS uses the Internet Printing Protocol (IPP) to send jobs from a client to a server. When printing to legacy print servers you can also use the Line Printer Daemon (LPD) when printing to older UNIX-based servers or Server Message Block (SMB) when printing to Windows servers.

---

### Post by tora201 on 2012-04-17
> **chugtairizwan said:**
> CUPS uses the Internet Printing Protocol (IPP) to send jobs from a client to a server. When printing to legacy print servers you can also use the Line Printer Daemon (LPD) when printing to older UNIX-based servers or Server Message Block (SMB) when printing to Windows servers.

Not sure how that answers my question. Could you explain further? How could I add an ID (my office phone number) when using LPD for example? Sorry if I appear dumb. Still in the dark regarding this.

---

