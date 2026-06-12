---
title: "Something is constantly loading"
date: 2009-09-22
forum: General Help
---

### Post by Poderoso on 2009-09-22
When Ubuntu has loaded up X the mouse cursor changes after 2 seconds or so into the loading-icon and stays that way until I shut down the computer. I've tried stopping all the processes in System Monitor but it didn't help; something tries still to load and never succeeds.

Any suggestions on how to try and figure this one out? Whatever it is doesn't seem to take up system resources but it is annoying to see the loading cursor all the time.

I'm running Ubuntu persistent 9.04 from a USB-stick.

---

### Post by zkriesse on 2009-09-22
Are you sure nothing is running? No ghost processes?

---

### Post by Poderoso on 2009-09-22
> **Zachk18 said:**
> Are you sure nothing is running? No ghost processes?

I'm a complete n00b when it comes to Linux, all I knew what to do was to check "System Monitor" and that didn't help.

---

### Post by TR14RC3 on 2009-09-22
Hello, 
 
Open a terminal and paste this: sudo gedit /etc/modules

Check to see if there is anything in there that may be causing this.

I suspect that it may be running Ubuntu from the USB stick. 

What kind of machine are you running? There might be some reported bugs with your model, along with some fixes.

Also, Did you get any updates? That might fix the problem. 

If you are just running Ubuntu live every time, you would have to update every time.

I honestly think the problem may be running Ubuntu from the usb stick. There is only one way to find out.

---

### Post by Poderoso on 2009-09-22
> **TR14RC3 said:**
> Hello, 
 
Open a terminal and paste this: sudo gedit /etc/modules

Check to see if there is anything in there that may be causing this.

I suspect that it may be running Ubuntu from the USB stick. 

What kind of machine are you running? There might be some reported bugs with your model, along with some fixes.

Also, Did you get any updates? That might fix the problem. 

If you are just running Ubuntu live every time, you would have to update every time.

I honestly think the problem may be running Ubuntu from the usb stick. There is only one way to find out.

Nope, nothing in /etc/modules. 

Afaik I shouldn't have to do the updates every time, this "live" version is able to save changes (or so they say at least). Now, I forgot to mention that the first times I booted Ubuntu the cursor was normal and didn't "load" all the time. But then I checked the "Automatically remember running applications when logging out"-box in "Startup Applications Preferences" and the next time I booted up I got the constant loading. At the time all I had running was synergyc, a terminal window, and File Browser. I did suspect that the culprit would be synergyc (it tries to connect to the synergy server when you start it up) but even when it doesn't show up in the running processes list I still get the loading icon...

---

### Post by P4man on 2009-09-22
system monitor by default only shows your processes. It might be a process owned by root. In system monitor, go to View > All processes.

---

### Post by Poderoso on 2009-09-22
> **P4man said:**
> system monitor by default only shows your processes. It might be a process owned by root. In system monitor, go to View > All processes.

*sigh*

I did that and went through the entire list and stopped/started all the processes (that you can stop/start manually) but the loading icon never stopped.

Fortunately inside programs (for example firefox or gedit) the cursor is still normal.

---

### Post by glomboi on 2010-05-09
Hi,
I know it's a late reply but since  stumbled across this thread with the same problem, I thought others may do the same.

I am running Netbook Remix 10.04 and had the same loading cursor problem.

It turns out (and it sounds like Poderoso had a similar problem) that one of the processes set to run on startup didn't exist any more.

I had uninstalled the program but the run-on-startup command still existed although didn't show up in "System > Startup Applications"

I ended up reinstalling the application and my problem is now fixed.

I hope this may be of some use to you.

---

