---
title: "Printing Problems"
date: 2006-03-21
forum: General Help
---

### Post by Studymore on 2006-03-21
I recently installed Kubuntu Breezy on a friends old computer.  Works great, faster than windows, and gives him much more capability to handle his projects.  It even recognized his CD burner, which Windows has not done for years . . . Thanks, Kubuntu!

But, the printer is not working.  I have it configured, the computer recognized it.... even printed a test page.  But, now any print command sent to the printer does nothing.  It shows the printing dialog box, and then goes away.  No print jobs are queued in CUPS, no error dialog.  What did I do between the time I configured his printer and the time I started an app to cause this error?  BTW, now it will not even print a test page.

We have a Lexmark z611, downloaded the driver from Lexmark.  

I am thinking of buying an HP today, but I do not want to have this same problem with a new printer.  What do you guys think?

---

### Post by Swiss on 2006-03-21
I had the same problem, it was solved by reseting the printer. Is the printer digital?

I have an HP, I've printed 38,000 pages and its still going strong!

---

### Post by Studymore on 2006-03-21
Ok, how do you reset the printer?

---

### Post by Studymore on 2006-03-22
The CUPS server will not actually start.  I have read several others forums regarding this, and everything I have done is simply complicating the problem.  I wish I could post the plethora of error messages I am getting.

I did go out and buy an HP 5440 to see if it would solve the issue.  I am angry and very sleepy after some nine hours of working on this bug.  Sombody please help!

---

### Post by Studymore on 2006-03-24
Here are the error messages:

In the KDE Control Center (running as root.)
Peripherals -> Printers ->
Unable to retrieve the printer list. Error message received from manager:
Connection to CUPS server failed. Check that the CUPS server is correctly installed and running. Error:
connection refused.

 From there, we can hopelessly attempt to add a printer.  This will be unsuccessful, of course,

because it can not connect, but I want to show you the error message:

Add -> Add Printer/Class ->

An error occurred while retrieving the list of available backends:

Connection to CUPS server failed. Check that the CUPS server is correctly installed and running.

Then, we can go into the Add Printer Wizard, which (since a retrieval of the available backends was
unsuccessful) will be unfruitful.  Backend selection is empty because backends were not retrieved.

When we try to open localhost:631 in Konqueror, we receive this message:

An error occurred while loading [http://localhost:631/:](http://localhost:631/:)
Could not connect to host localhost (port 631).

Pinging localhost shows the same problem,
localhost:631 does not respond.

Both commands:
sudo /etc/init.d/cupsys restart    &
sudo /etc/rc2.d/S19cupsys restart
yield this response:
* Restarting Common Unix Printing System: cupsd                      [ ok ]

But,. when we run this command:
ps -Al | grep cupsd
We get no reply.

Cups is obviously not running, but Linux is lying to
me....  arrggghhhhh!!!!

---

