---
title: "Need to admin CUPS for a network printer"
date: 2011-08-11
forum: General Help
---

### Post by Francis4344 on 2011-08-11
Hello all!

I cannot navigate my windows network because of a unresolved issue.
see [http://ubuntuforums.org/showthread.php?p=11131098#post11131098]("http://ubuntuforums.org/showthread.php?p=11131098#post11131098")

 The workaround is to use the IP address of the computers.

Problem is that CUPS has the printer address with the computer name as opposed to IP addresses.

CUPS will not let me manage the network printer. It asks for a user and password. My sudo name and password dont work.

I think the solution lies in the cups.conf but I am unsure how to fix it so that I can manage the printers.

A solution to my networking or printing problems would be nice!

Thanks,

Francis

---

### Post by dino99 on 2011-08-11
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

[http://www.cups.org/documentation.php/network.html](http://www.cups.org/documentation.php/network.html)

---

### Post by Francis4344 on 2011-08-11
The first two links do not answer my question.

The CUPS documentation is way over my head.

Is there a terminal command that could assign a IP address to my printer?

Why is it that I dont have permission to manage the printer?
Is there a way to manage cups (through localhost:631) as a super user?

Thanks again

---

### Post by Morbius1 on 2011-08-11
>  Why is it that I dont have permission to manage the printer?Because you are not a member of the lpadmin group?

Run the following command and see if "105(lpadmin)" is listed:
```
id
```
If not add yourself to the group:
```
sudo gpasswd -a user-name lpadmin 
```Unfortunately you need to logoff ( not reboot ) and log back in again for the group membership to change.

As for accessing the Windows printer by ip address you can do that through Printers > Add Printer > Network Printer > Windows Printer via Samba. 

Don't use the "browse button" just enter in the "smb://" field:
```
192.168.0.100/windows-printer-name
``` And then select "Verify".

You may have to play with capitalization and such to make sure the names match exactly.

---

### Post by Francis4344 on 2011-08-11
Morbius1, you are a savior, once again.

Instead of going through CUPS, all I had to do is select the printer, then properties, and simply change the network name to the IP address. Et voilà!

Still dont know why CUPS does not recognize it's Master but I will settle that later.

Ah, the joy of being green once again... reminds me of that impressive first 286 running dos 5... :)

Francis

---

