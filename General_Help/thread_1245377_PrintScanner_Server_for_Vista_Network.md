---
title: "Print/Scanner Server for Vista Network"
date: 2009-08-20
forum: General Help
---

### Post by jperez on 2009-08-20
Hi all!

I'm working on a little project while doing some community service/volunteering here at my local Salvation Army.  We're switching to Vista laptops and as where the old XP laptops in the computer lab and basically through out the building all connection to a LinkStation Media/File/Print server and work with XP, it won't let us connect the Vista x64-bit laptops with the printer and we can barely see the Media/File server itself.  So, upon learning that, I suggested to the Lab Director that we use a Linux computer as a print/scanner server.  It's basically an eMachine that had WinXP on it, but is now running Xubuntu 9.04 on it.

What I want to know is what would I need to do, aside from installing **cups**, **sane** and **samba** onto the system to get it working on the "soon to be" Vista network for the lab?  The other computers in the building will be using the old print server, I believe, but we need the lab computers running x64 Vista to connect to the Linux computer and send all their printing and scanning jobs to it.  Printer and Scanner are separate machines, I don't know if that makes a difference.

So, am I missing anything, need to change something or am I good to go?  Also, what steps do I need to take to get started setting it all up?

Thanks for any and all info I receive on this matter! :D

Jesse~

---

### Post by epsolon77 on 2009-08-20
I do not think the issue is with your file and print server.  While I am sure that a Linux file and print system will have it's advantages, I don't think this is the direction you will want to go.  Check to make sure you have a Vista x64 driver loaded on the file and print server for your printer.  Check to make sure the file and print server is in the same work group as your vista laptops (Note that the default work group has changed from MSHOME in XP to WORKGROUP in Vista) and make sure the server has a hole in your Vista firewall, and that you have completed all the Microsoft recommended steps to read shared files.  [http://technet.microsoft.com/en-us/library/bb727037.aspx](http://technet.microsoft.com/en-us/library/bb727037.aspx)
IMO Vista's shared networking is not stable, nor easy to configure.  From what I know you are on the correct track to set up a shared system, but if the issue is in the Vista config, your samba share still won't work.

---

