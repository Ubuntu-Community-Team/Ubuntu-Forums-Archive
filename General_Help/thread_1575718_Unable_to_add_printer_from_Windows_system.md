---
title: "Unable to add printer from Windows system"
date: 2010-09-16
forum: General Help
---

### Post by healee on 2010-09-16
I am using the latest version ubuntu desktop 10.04 LTS.  I am trying to add printers attached to a Windows 7 system.  I can see the Windows system but I can't see the attached printer.  I log on as required after I change the domain to the appropriate workgroup that the Windows system belongs to.  The log-in seems to be unsuccessful.  Do I need to change the ubuntu desktop system to the same workgroup?  If I do, please tell me where I can change?

I've just checked.  I don't seem to be able to access any shares on any Windows systems on the network including the Windows system on the same computer where this ubuntu is installed.  I installed ubuntu using wubi, so it is an application inside Windows system.

---

### Post by Mark Phelps on 2010-09-16
You mentioned Win7.  Are you sure it's WorkGroup? Not HomeGroup?

If it's the latter, you're out of luck, for AFAIK, there is no implementation of HomeGroup outside of Win7.  Even Vista and XP can't share in HomeGroups.

---

### Post by healee on 2010-09-17
> **Mark Phelps said:**
> You mentioned Win7. Are you sure it's WorkGroup? Not HomeGroup?
 
If it's the latter, you're out of luck, for AFAIK, there is no implementation of HomeGroup outside of Win7. Even Vista and XP can't share in HomeGroups.
 
It is definitely workgroup.  I have tried homegroup.  I didn't like it.  It gave me more problems than benefit.  In fact there was no benefit to me at all.  Moreover homegroup has no name.  Workgroup does.  All my Windows 7 systems are not in any homegroup.

---

### Post by Mark Phelps on 2010-09-17
As an alternative, you could look into getting a network-based print server and connecting your printer to that.  Then, ALL the machines will be able to use that printer.  And, with the CUPS version provided with 10.04, installing a network printer has been made very simple.

---

### Post by dougalkerr on 2010-09-17
You should be able to connect to the printer just fine. Although, I can't remember off-hand what the correct name protocl is, you need to add a Networked printer from the options to add a printer.
Go to Administration/Printing and Add New Printer.
Select Network Printer and then Windows Printer via Samba (at least this is how I do it at work).
On the right-hand side you will see a Text Entry box for smb:// in here is your path to the printer.
if I can remember I think mine is smb://galba/hpdj5900

The galba bit is the PC name of the machine the printer is attached to and hpdj5900 is the printer.

Make sure you know the exact printer name.
I also make sure 'sharing' is selected on the Windows machine.
Apart from that you will just need your username and password for the Network.

Hope this works for you. If not it may be because it is not a Samba server set-up but, the priciple is the same for other server types.

---

### Post by Morbius1 on 2010-09-17
Windows Live Sign-In Assistant.

Do you have it installed on Win7 by any chance? If you do you might consider uninstalling it:

[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

There's a fix for it in an upcoming Samba update but for now the only recourse is to get rid of it.

---

### Post by healee on 2010-09-19
> **Mark Phelps said:**
> As an alternative, you could look into getting a network-based print server and connecting your printer to that. Then, ALL the machines will be able to use that printer. And, with the CUPS version provided with 10.04, installing a network printer has been made very simple.
 
Thanks for your advice!  I will certainly look into that option when I next get a printer.

---

### Post by healee on 2010-09-19
> **dougalkerr said:**
> You should be able to connect to the printer just fine. Although, I can't remember off-hand what the correct name protocl is, you need to add a Networked printer from the options to add a printer.
Go to Administration/Printing and Add New Printer.
Select Network Printer and then Windows Printer via Samba (at least this is how I do it at work).
On the right-hand side you will see a Text Entry box for smb:// in here is your path to the printer.
if I can remember I think mine is smb://galba/hpdj5900
 
The galba bit is the PC name of the machine the printer is attached to and hpdj5900 is the printer.
 
Make sure you know the exact printer name.
I also make sure 'sharing' is selected on the Windows machine.
Apart from that you will just need your username and password for the Network.
 
Hope this works for you. If not it may be because it is not a Samba server set-up but, the priciple is the same for other server types.
 
I did go through all this.  I was expecting to see the printer on the configuration pane but I didn't.

---

### Post by healee on 2010-09-19
> **Morbius1 said:**
> Windows Live Sign-In Assistant.
 
Do you have it installed on Win7 by any chance? If you do you might consider uninstalling it:
 
[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)
 
There's a fix for it in an upcoming Samba update but for now the only recourse is to get rid of it.
 
I do not know if I can afford to go without the Windows Live Sign-In Assistant.

---

