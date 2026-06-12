---
title: "Printer Not recognized after going through VMware"
date: 2011-05-25
forum: General Help
---

### Post by william_ia on 2011-05-25
Hi All,

I am testing to see whether after connecting to an Image on a  server with VMware View Open Client I can get it to add a local desktop connected printer(usb). In Ubuntu 10.04 I have made this printer the default and printed a test page just fine, but when I go through VMware to a Windows Image all I can see are the printers that are connected to the local network.
I need to be able to deploy this to any location and add or see printers on the fly. As when it goes into the field it will be on a Wi-fi card to connect to the Windows Image through VMware.
Am I missing a driver, or do I need to add something in the Startup Applications so it see's the printer outside of Ubuntu?:confused:

---

### Post by micael3000 on 2011-05-25
Hi!

I am not an expert at this (sorry), but I will try...
1.0 - Do you see your ubuntu on the windows as a network computer?
1.1 - If so, is the printer listed there?

2.0 - Do you have SAMBA installed? (I believe you are really going to need it)

3.0 - Check on Printing if your printer is shared... And check on Samba if it shares your printer.

[]'s.

---

### Post by william_ia on 2011-05-26
Hi Micael,
 
Once into the Windows Image, nothing on the Ubuntu side is visible. That is our problem. Will Samba take care of that? 
 
When on the Ubuntu side only, I have the printer set as default, with the default software loaded. If finds the printer there and prints a test page fine from the text editor.

---

### Post by micael3000 on 2011-05-27
I think so!
Samba makes the connection between Linux and Windows, sharing folders, printers and so.

Give it a try and then let us know if it works for you :)

---

### Post by william_ia on 2011-06-01
Micael3000,

I added Samba to the laptop, went through the VMware tunnel to see if I could see or add it on the Windows Image. It still is not letting us add or see it in the image.

I tested printing a test page after going through the image and it still works fine on the Ubuntu side. Do I need to activate the Samba on startup??

I also checked again, on your line 1.0 and I do not see Ubuntu on the Windows side as a network computer. I added Samba as a start up application so it is active on start up. So at this point I am not sure what I need to do next.

---

### Post by william_ia on 2011-06-02
After doing some more research on VMware, I have discovered that the problem I am experiencing has to do with the USB Redirect not working through VMware. 

What drivers are there available that will allow me to pass USB devices (printers, flash drives, etc) when using software like VMware to ensure that what is seen on the Ubuntu side is also seen on the Windows side?

I am doing some online searching, but so far have found nothing specific to this problem!
Anyone have any ideas?

---

