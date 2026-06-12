---
title: "UNR &quot;Thin&quot; clients?"
date: 2009-09-22
forum: General Help
---

### Post by Beltaine on 2009-09-22
Set up a new student lab here at work using Lenovo S10e Netbooks.

Used Windows XP and XP Lite to make it fit on the 4GB SSD.

Using Windows Steady State, the student user is automatically logged in and locked out of doing anything on the local machine.

A startup script opens the Remote Desktop Client and automatically connects the student to our Windows Terminal Server. If/When the student logs out of the Terminal Server, the script logs the user out of the local machine to prevent any attempts at tampering.

This is working well, but Windows is a resource hog and the performance of the machines is lackluster, particularly during startup. We also are running into issues with costs due to licensing and looking for an Open Source alternative.

Looking for some advice and/or help in getting an extremely minimal UNR build that will automatically connect students to our Windows Terminal Server over a wireless network, and allow them to save their files to a USB stick local to the netbook.

---

### Post by Beltaine on 2009-09-23
Well, ok. Let's start one step at a time.

How can I configure UNR to restrict the default user to just basic functions. (i.e. open programs on desktop and menu, prevent them from accessing files on the system, prevent them from making any changes, allow them to save files to a USB drive.)

---

### Post by mixmaster on 2009-09-23
The traditional way to do this is to use a chroot jail.  This isolates the user in his own sandbox and prevents him wandering at will through the rest of the system.  Combined with a restricted shell (eg rbash) you can also prevent the use of most shell-level commands.

Chroot jails are easy to build but making them completely secure is non-trivial.  There are a lot of articles on the web about how best to go about this.

---

