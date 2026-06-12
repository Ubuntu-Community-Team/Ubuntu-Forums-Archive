---
title: "Using a Windows printer in Ubuntu."
date: 2006-02-20
forum: General Help
---

### Post by slavik on 2006-02-20
I have an HP Deskjet 920C which is connected to my WindowsXP system and is set to share. I also have the UNIX Printer Sharing thing installed.

How do I connect to the printer from Ubuntu? (Badger)

---

### Post by abhaysahai on 2006-02-20
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#whatissamba](http://help.ubuntu.com/starterguide/C/faqguide-all.html#whatissamba)

Try this.

---

### Post by ronmarley1 on 2006-02-20
This worked for me:
1.  System-->Administration-->Printing
2.  Dbl. click "New Printer"
3.  Choose "Network Printer"
4.  Choose "Windows Printer (SMB)"
5.  Host=XP box name
6.  Printer=Share name of printer connected to Windows box
7.  Username=name of a user on the Windows box that has rights to print to the printer (I set my printer to share with Everyone); Password=that user's password.
8.  Choose the manufacturer of the printer (in your case, HP) and then choose the model (there's a driver for the 920C included with Ubuntu).
9.  Click Apply
10.  Print whatever you want!

---

