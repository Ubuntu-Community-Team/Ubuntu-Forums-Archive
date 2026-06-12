---
title: "Can't share printer on network anymore"
date: 2009-11-12
forum: General Help
---

### Post by OSX@Linux on 2009-11-12
Ive been a Ubuntu user for a while now (since 6.10) and I suddenly cannot share my printer on my home network. It used to work before I upgraded to 9.10, but the upgrade seems to have broken it.

I have a HP Deskjet F4280 hooked up via USB. My Ubuntu machine is connected to the home network through ethernet. I am using HPLIP.

The computer I am trying to remotely access the printer from is a MacBook running OS X 10.6

Any suggestions?

Thanks for the help.

---

### Post by IndieInvader on 2009-12-27
Bump

I'm having the same problem. I've tried everything I can think of to get this working and read through a myriad of how-to articles for older versions of ubuntu and of os x and still nothing but errors!

---

### Post by terevos on 2009-12-30
I am also having the same problem. Using Mythbuntu 9.10 (server) and Mac OS X 10.5 (client). hplip runs and sets up the printer fine. It prints locally, but I cannot access the printer from the Mac.

No errors or warnings after doing a hp-check -t

---

### Post by x17y19 on 2010-01-16
I ran into this problem on a fresh install of 9.10: after installing all updates, printers connected to this box were not visible on other machines on the network (no Windows boxes, so no samba involved).

In my case, the solution was:
[LIST=1]
[*]Go to System->Administration->Printing
[*]On the 'Printer Configuration' window go to Server->settings
[*]On the pop-up window titled 'Basic Server Settings' check the box saying 'Publish shared printers connected to this system'
[/LIST]

Hope that helps.

---

### Post by terevos on 2010-01-17
That option is already enabled on my setup. Still no luck. I've read a couple places on other forums that seemed to indicate that there are problems with certain HP printers and Ubuntu 9.10.

---

### Post by malibusurfer2 on 2010-11-21
These instructions are for a computer running linux with a USB printer plugged into its USB port.

a) Your computer and printer must be turned on and booted up.
b) Make sure the printer works from your linux computer by printing a test page.

1. In a web browser (Firefox) go to [http://localhost:631/printers/](http://localhost:631/printers/)
2. Click on the Administration tab along the top.
3. On the upper right in the Server section, check “ Share published printers connected to this system”
4. Click on “Change Settings” to save the change.
5. Close the web page.
6. On your Mac computer, open System Preferences, Print & Fax, under Printing click on the “+” sign to add a printer to the printer list. 
7. It should find the printer. Select it and click on Add.
8. Try to print a test page to the printer.

Network enabled printers are becoming more common and cheaper. They can be more trouble to configure to work on your home network, but the big advantage is that they are stand alone devices that allow you to print directly from any computer. A USB printer plugged into a computer will only work when that computer is on.

---

