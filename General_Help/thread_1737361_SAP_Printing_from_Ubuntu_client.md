---
title: "SAP Printing from Ubuntu client"
date: 2011-04-23
forum: General Help
---

### Post by eskayes on 2011-04-23
Hi

We have a SAP SERVER running on Windows 2003 64 Bit Server

We created a client system on a desktop machine in Ubuntu 10.10. 

This system has got SAP GUI for Java 7.20 Rev 5

The printer is a network printer Canon IR 3300.

I have created an output device using SPAD with the following field values

Output device        : CANONIR3300
Short nane        : CA33
Device type        : POST2 
Device class        : Standard printer
Host spool access method : G: Frontend print with control technologies
Host printer        : __DEFAULT    (two underscore characters)                      


Problem is when I print any document from this terminal using this output device, the printer prints a garbage page. scan attached of the print.

Can anyone help me in resolving this?

PS: Other windows xp terminals are printing perfectly using:
   Output device        : LP01
   Short nane        : LP01
   Device type        : SWIN
   Device class        : Standard printer
   Host spool access method : G: Frontend print with control technologies
   Host printer        : __DEFAULT    (two underscore characters)                      

regards

---

### Post by amityadavmt on 2011-05-20
I am also trying

---

