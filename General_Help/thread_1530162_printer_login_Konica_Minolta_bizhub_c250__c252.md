---
title: "printer login: Konica Minolta bizhub c250 / c252"
date: 2010-07-13
forum: General Help
---

### Post by ferarg on 2010-07-13
Hi, I've read this post with help to this printers

[http://ubuntuforums.org/showthread.php?t=530971&highlight=konica+minolta+c250&page=2](http://ubuntuforums.org/showthread.php?t=530971&highlight=konica+minolta+c250&page=2)

but I cant use the authentication option of this printer in Gnome, I configure the authentication option in printer setup, but nothing hapen.

I can print in console using a complicated menu given by konica, but I need to print from OpenOffice or other "X" programs, ever using the authentication method

Thanks for your help

---

### Post by cool_penguin on 2010-07-15
I have the exact same problem with Konica Minolta bizhub 222. My understanding is that we need to modify the ppd file (using a text editor) and include the authentication information in it. I tried doing that, but the ppd file looks very confusing. I hope I get some help on this forum.

Any help will be greatly appreciated. 

Cheers,
Harry

---

### Post by ferarg on 2010-07-16
Hi cool_penguin, I solve it usin cups.

With cups you share the printer and then you can allow/disallow users, and the user must use user & password to print.

---

### Post by cool_penguin on 2010-07-21
Hi ferarg,

Thank you for the idea. However, could you please give me instruction on how you did it?

Thanks again and looking forward to your answer.

Cheers,
Harry

---

### Post by ferarg on 2010-07-22
Hi cool_penguin, it really easy:

First of all, use the last version of CUPS!

Create in the PC that will act as Print Server, the user that you want to permite use the printer

1) The printer must be installed in your system
2) Using you browser go to: [http://localhost:631/admin](http://localhost:631/admin)
3) Click on Share printers connected to this system and save the changes
4) Click on "Printers"
5) Click on the printer you want to manages
6) Click on the right arrow of the "Administraction" and choose "Set Default Options"
7) Click on "Policies" and choose "Authenticated" in "Operation Policies" & save changes
8) Click on "Printers" again
9) Click on the right arrow of the "Administraction" and choose "Set Allowed User"
10) In the blank line write the users that you allow to use the printer, separated with space or comma
11) Choose "Allow these users to print" and save the changes

In the client PC, add the printer via LPD using the IP of the server, if it change the IP with teh name of that PC, change again to the IP to avoid problems, there you can choose the "Print queeu", choose the one that you share.

When a user print something, will ask for user/pass

I hope this help you

---

