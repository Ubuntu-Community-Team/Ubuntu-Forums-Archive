---
title: "USB printer server with HP printer issues."
date: 2010-08-05
forum: General Help
---

### Post by Labhrain on 2010-08-05
I've been working at this for a few days.  I've searched all over and  as far as I can tell, I'm setting up my printer correctly.  I have  hpcups (latest version.)  My printer is an HP Officejet 5610. It works  perfectly if I set it up directly (USB to Ubuntu machine.)  No  configuring is required.  I just plug it in and it already has the  drivers.  However, when I set it up through the print server, it acts  very strangely.  It appears to start sending the file, the printer  starts to pull the paper, then it just hangs.  The printer states  "printing" and stays in that state until I turn it off.  CUPS states  that the printer is "processing" and it stays that way until I cancel  the print job. 

 So, I really don't know what more do to.  The way I set up the  printer was by going to System->Administration->Printing.  I added  and chose LPD/LPR Host or Printer.  I put in my IP address for the  print server, clicked "probe" (it came up with the queue name  "PASSTHRU") then hit "Forward."  I chose "HP" and then chose "HP 5600  Series."  Everything seems right, but then it all goes wrong.  
 Any ideas would be great.  I've done lots of trying and lots of  searching before finally deciding to post to a forum.  Every tutorial I  find leads me to believe I've set this up right.

On the advice of someone, I also tried setting it up as IPP, but that didn't work at all. 

My print server isn't wireless.  It's a USB print server that connects to the router with  Cat-5 and then you plug the printer into it via a USB cable.  The computers then communicate with the printer via the network through the router.

I really don't want to make one of the computers on the network the printer server, requiring me to leave it on all the time.

Any ideas are welcome.  I'm at a loss.  Thanks.

---

