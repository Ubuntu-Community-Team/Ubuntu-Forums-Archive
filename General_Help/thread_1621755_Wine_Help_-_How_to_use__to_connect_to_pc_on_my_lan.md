---
title: "Wine Help - How to use \\ to connect to pc on my lan in Ubuntu"
date: 2010-11-14
forum: General Help
---

### Post by greavette on 2010-11-14
Hello,

I've used Wine to install a windows application that uses an .ini file to connect to a server on our lan.  In the .ini file we have the following types of references:

Server=\\Server1\FolderA

How would I modify this .ini to point to Server1 on our network when running this application through wine on my Ubuntu pc?  I'm running Lucid Desktop version on this PC.

I also have references to registry locations for this windows application:
[Keys]

;Root1=HKEY_LOCAL_MACHINE

;Path1=SOFTWARE\Microsoft\Office\11.0\Access\RefLibPath

Which references MS Access.  Does Wine have a type of registry where the above would be valid when running from Ubuntu?

Thanks in advance for any help you may provide.

Charles.

---

### Post by spiky001 on 2010-11-14
Can you explain your setup better is it windows to ubuntu or what. And what are you trying to do ?

---

### Post by greavette on 2010-11-14
Sorry, it's Ubuntu to Windows.  The application is a windows application that has successfully installed on Ubuntu using Wine.  When we install this on Windows, the shortcut to start the app points to a .ini file and in this .ini file is the location of the server for the SQL Server database.  On Windows we map a drive (L:) to where this .ini files lives.  

Maybe what I need is to see if I can map a drive (L:) in Ubuntu using Wine like we do in windows...or maybe it's the application command instruction (wine created on Ubuntu) that needs to be modified?

We use this application on our Windows XP PC's.  I'm just testing this application to see if it will run on Ubuntu too.  For some of our workstation PC's in our lab, this application is the only thing running on them so if I can get it to work on Ubuntu, we can save the cost of buying and installing Windows.

Thanks,

Charles.

---

