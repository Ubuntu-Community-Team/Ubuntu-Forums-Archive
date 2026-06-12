---
title: "unable to connect to CUPS server"
date: 2006-03-22
forum: General Help
---

### Post by corto_maltese on 2006-03-22
I saw a lot of people around the world with this problem...

When I click on System->Administration->Printers an error message occurred: "unable to connect to CUPS server"

First I checked that CUPS was runnign and this was okay...
The I checked that the packages cupsys-driver-gimpprint-data, gnome-cups-manager e cupsys-client were installed and they were.
The I use Firefox to connect to  [http://localhost:631](http://localhost:631), and it works..

I success in installing correctly my printer and in printing a test page... but I can't do anything else from this interface...

My PC is not connected to others, is a simple home-PC with a printer connected to a USB port.

The other software continue "not to seeing" the printer and so I can't print anything... ideas?

I attach my cups.conf file maybe the problem is there...

I think this is a real bad bug...

---

### Post by hajk on 2006-03-22
No bug, access to CUPS via [http://localhost:631](http://localhost:631) is disabled in Ubuntu, you're supposed to use the Gnome print manager (System --> Administration --> Printing), and that should work OK in most cases. 

Now, if you absolutely must use the localhost:631 route, then you could try to edit the /etc/cups/cupsd.conf file and comment out the two lines "AuthType Basic'' and "AuthClass System'' near the very end end of the file. Then restart CUPS with
the command "sudo /etc/init.d/cupsys restart", and you have access via localhost:631. I recommend using the Gnome print manager, though.

---

### Post by corto_maltese on 2006-03-23
Sorry probably I didn't explain well my problem...

I want to use Gnome printer manager, but it doesn't works...

When I click on System->Administration->Printers an error message occurred: "unable to connect to CUPS server"

And only because it doesn't works I tried to use [http://localhost:631](http://localhost:631), overall to check if CUPS server was really running...

I was asking for a solution that make gnome printer system work!!!](*,) 

I don't want to use that interface... but actually it's teh unique interface that "see" the printer...!

---

