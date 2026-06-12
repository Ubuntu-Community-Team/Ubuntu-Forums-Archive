---
title: "Can I set up Win printer server for Ubuntu clients?"
date: 2009-08-27
forum: General Help
---

### Post by keevill on 2009-08-27
I have a Xerox FxAposport 450i Network printer for which there are no Linux drivers.

Can I set up a Windows PC as a print server and connect the Xerox printer to it and then print thru it with Ubuntu 9.0.4 client machines ?

When I try to set up the printer on the  Ubuntu client machines via the Windoze box, will they still call for the drivers for the printer ?
Thx,
-keevill-

---

### Post by keevill on 2009-09-02
I got nowhere with this question however I did manage to set up the Xerox Apeos 450i using the HP LaserJet 3D Foomatic/ljet3d driver.
I hope this helps others with the problem

---

### Post by jamesisin on 2009-09-02
If you use the Ubuntu machine to serve that printer, I believe you would have to provide the Windows machines with the appropriate drivers.  I am running a printer on a Windows server with varying levels of success (serving for Ubuntu machines).  You can read my post on that:

[http://www.soundunreason.com/InkWell/?p=767](http://www.soundunreason.com/InkWell/?p=767)

Feel free to advise if you come up with better information.

---

### Post by keevill on 2009-09-02
Actually, I think you mis read my post.
I am using UBUNTU clients and there are no linux drivers for the printer.
I was considering using a WINDOWS server just for the printer.
However, that doesn't work cos the Linux clients still need care by way of drivers for which , there are none.
My workaround was , as I said in my previous post, to use HP drivers.
I am facing a similar issue with a Richo GX3000 Gel printer and currently have no solution for that.

---

### Post by jamesisin on 2009-09-03
Ah, close.

Print sharing like this is one weak point in these systems.  I have a terrible time getting the print jobs to move from my Ubuntu machine to my Windows server.  I am considering moving the printer to my Ubuntu machine to see if that helps any.

I had to choose a similar HP driver to my printer because my specific printer was not listed.  Be nice if the manufacturers would just release the drivers to the Linux crowd.  So moving the printer to my Ubuntu machine will help decide if it's the sharing that's forking up or the driver.

---

