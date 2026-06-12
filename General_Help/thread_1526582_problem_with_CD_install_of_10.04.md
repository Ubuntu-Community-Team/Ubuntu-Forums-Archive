---
title: "problem with CD install of 10.04"
date: 2010-07-08
forum: General Help
---

### Post by pieman711 on 2010-07-08
I've finally finished my exams and I'm taking the plunge to go from 8.10 to 10.04 :)
Because I've played around with my 8.10 so much I decided to go for a clean install rather than an upgrade. I've downloaded the iso file for 10.04 desktop ediiton from the Ubuntu site and burned it to a CD. When I put the CD in and restart (making sure CD is the first boot option) i get a picture in the bottom of a man in a bubble and what looks like a stick of ram then it gives me an error of something like "cd error" and then gives me a button with reboot as the only option.
 thought it may have been a bad burn so I tried burning it again on someone elses computer and neither CDs work on either of our computers. I'm using CD-RW but don't think that should make a difference. 
I also tried creating USB  start up disk but can't find an option to boot from USB in my BIOS or boot loader (pressing F11 during the very first screen when it's turned on)
Any advise would be greatly appreciated
:p

---

### Post by Pidgin on 2010-07-08
Use PLoP Boot Manager to boot from the USB stick.

---

### Post by pieman711 on 2010-07-08
I'v managed to get PLoP burnt on to a CD and through this have got the first menu from the USB start up disk running. Now I appear to have a new problem. I can't get any further than the next screen. If I select 'try Ubuntu' or 'install ubuntu' it goes trough to a loading screen with ubuntu slap bang in the middle and 5 dots undernieth that change fro red to yellow back to red again. It was just doing this over and over so i hit a button on the keyboard and it said
(process:375):GLib-WARNING 8 **: getpwuid_r(): failed due to unknown user id (0)
                                                                                                                                        stdin: error 0
stdin: error 0
stdin: I/O error
stdin: error 0
stdin: I/O error
stdin: error 0
stdin: I/O error
stdin: error 0
stdin: error 0
stdin: error 0
stdin: I/O error
stdin: error 0
 stdin: I/O error
stdin: error 0
 stdin: I/O error
stdin: error 0

then pressinf escape puts me back to the ubuntu red/white dot screen.
pressing ctrl+alt+del restarts the computer.
Any suggestions?

P.S I ran the USB on my asus EEE and it appeared to be working fine

---

### Post by pieman711 on 2010-07-09
I've managed to upgrade! I think my problem is my CD drive is on it's way out. I finally managed to install with PLoP and a USB start up and took the PLoP cd out as soon as the USB bit kicked in. I think the CD drive was causing errors that interrupted the USB installation.

---

