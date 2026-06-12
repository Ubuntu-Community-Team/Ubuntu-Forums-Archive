---
title: "Printing to Windows-hosted-printer"
date: 2012-03-01
forum: General Help
---

### Post by Lexus45 on 2012-03-01
Hello guys.

We have a network with ActiveDirectory, all Win-PCs are in AD domain.
There is also 1 Ubuntu PC which is not in the AD domain.

The HP P2055d printer is connected to Win 2000 (it's in AD domain) and shared, it's also added to the AD (the checkbox on the Share properties in Win).
It even prints perfectly from Ubuntu. But the problem is that every time it asks to enter the username and the password of the valid AD domain user. (the syntax is domainname\ad_username and his password in the next line).

The user wants his login and password be remembered. But I don't see any checkboxes which will allow this.

The screenshot is in russian, but I hope everything is clear ("You have to authorize to be able to print the document on this printer bla bla bla").

So,** the question**: where it's possible to remember the username and the password?

---

### Post by Lexus45 on 2012-03-01
It seems that I've found the solution.

variant 1 - using GUI:
we need to delete the printer and add it again via built-in Ubuntu 'system-config-printer'.
- When adding network printer, select 'Windows printer via SAMBA'
- enter the path, in my situation the path is smb://ivan/HP
- enter the username and password in the lines . If the user is in AD domain, his login will be 'domainname\username'

variant 2 - editing /etc/cups/printers.conf:

- stop CUPS - sudo service cups stop
- edit /etc/cups/printers.conf . All printers, accessible to your Ubuntu are described there.
- find the line 'DeviceURI ....' , in my case it was "DeviceURI smb://ivan/HP"
- add your login and password there.

PS: in fact, I haven'e edited this file. I just compared it after re-adding the printer via GUI and antering and saving login and password. They appeared in /etc/cups/printers.conf after that. Take a note that the backslash is as '**%5C**' here:

DeviceURI smb://domainname%5Cjohn_doe:pAsSwOrD@ivan/HP

---

