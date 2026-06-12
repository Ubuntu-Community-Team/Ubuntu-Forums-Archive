---
title: "Network Printer Requires Authentication"
date: 2012-07-18
forum: General Help
---

### Post by ewnoo on 2012-07-18
This is NOT a failure on CUPS behalf -- the problem is the printer on-board security.

Printer is a Fuji/Xerox DocuCentre C2265
I have never seen a printer require that "print jobs" themselves provide a userID & pswd, but this printer does.  They have many existing Windows users on this network using this printer so they want to keep the on-board printer security enabled.  This means each Windows computer must identify itself with userID and password for each print job.  Allows them to audit printer usage.  Anyway ...

We added the Linux box to the network, setup CUPS with generic PCL driver with these results:

     Printer on-board security enabled -- No printing from CUPS - no CUPS errors.

     Printer on-board secutiry DISabled -- CUPS is printing fine.

So this is not CUPS error, or driver, or any other issue related to CUPS itself.  The problem is *the printer*.  So the question is, how do we get cups to authenticate to the printer?  Anyone run into this and offer solution?

---

### Post by philinux on 2012-07-18
There should be within the smb setup an option to verify/authenticate with the network printer.

> If the shared printer requires authentication you can choose to be prompted for the login and password each time the printer is accessed, or to store these credentials in the Ubuntu printer manager so that they do not need to be manually entered for each print job.

Having selected the correct printer, click on Verify to confirm that the printer is accessible to Ubuntu. If the verification is successful, a message dialog will report Print Share Verified. Assuming a successful verification, click Forward and follow the steps outlined in the previous section to select an appropriate printer driver.

Once the SAMBA printer is configured, right click with the mouse on the new printer in the Printer configuration dialog, select Properties and click on the Print Test Page button. A test page should then appear on the printer. 

---

### Post by ewnoo on 2012-07-18
Thanks for the reply philinux,
I supposed I might ought to mention we are in run mode 3 so GUI is disabled in the Linux box -- no clicking allowed.  Also, "Samba"?  << Do we need this?  I have no experience with Samba and CUPS obviously works fine if the printer on-board security does not lock it out.

---

