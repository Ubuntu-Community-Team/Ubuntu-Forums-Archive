---
title: "cli install of Brother HL-2240"
date: 2012-06-16
forum: General Help
---

### Post by Pat Brown on 2012-06-16
I recently bought a Brother CL-2240 and I need some information. Following some clis I found online, but none work. I have the correct driver installed and used some info on Ubuntu forums. I'm on Ubuntu 12.04

There it's suggested I begin with this sudo as-complain cupsd 
I also tried this line sudo aa-complain cupsd
I do and get this message Command not found on both

Please, how do I install the printer -- and since I've never installed a printer this way before so treat me like someone who barely knows what Ubuntu is. (not true, but this has me puzzled) I'd love a step by step install instructions. As I said I have the driver

---

### Post by Zill on 2012-06-16
> **Pat Brown said:**
> ...Please, how do I install the printer...
Linux systems (unlike other OS's) generally include many drivers by default, or will automatically download them if required.

I do not know for sure if this is the case with your HL-2240 but I simply plugged my HL-2130 in and it installed itself automatically.

I suggest you just try connecting the printer USB cable, switch the printer on and wait a minute or two and see what happens.  Please make sure your internet connection is up throughout this process in case any downloads are required.

Then try a test print.  Please let us know how you get on, reporting any messages if necessary.

---

### Post by wallaroo on 2012-06-16
If Zill's suggestion doesn't work ...

By 'I have the driver', I assume you mean you have installed the files 'hl2240lpr-2.1.0-1.i386.deb' and 'cupswrapperHL2240-2.0.4-2.i386.deb' available from the Brother web site.

Usually just installing these is all you need to do.

However if you are running on a Ubuntu 64bit system you may also need to install the 'ia32-libs' package (see your Package Manager) because the Brother printer drivers are still only 32bit.

If you have already installed the CUPS driver you can check to see the CUPS status through your browser by entering 'localhost:631' as the address and look in the 'Printers' tab.

---

### Post by sandyd on 2012-06-16
> **Pat Brown said:**
> I recently bought a Brother CL-2240 and I need some information. Following some clis I found online, but none work. I have the correct driver installed and used some info on Ubuntu forums. I'm on Ubuntu 12.04

There it's suggested I begin with this sudo as-complain cupsd 
I also tried this line sudo aa-complain cupsd
I do and get this message Command not found on both

Please, how do I install the printer -- and since I've never installed a printer this way before so treat me like someone who barely knows what Ubuntu is. (not true, but this has me puzzled) I'd love a step by step install instructions. As I said I have the driver

Browse to [http://localhost:631](http://localhost:631) .
Go to "Manage Printers".
If it isn't listed there (it should be), click on "Add New Printer", and see if it is there.

If it is, continue on with the steps.

If it isn't, post the ouput of
```

lsusb
```

---

### Post by Pat Brown on 2012-06-18
:KS It finally worked. I now have a printer. Much thanks to all!

---

### Post by daslinkard on 2012-06-18
Please mark as 'Solved'.

---

### Post by Pat Brown on 2012-06-19
> **daslinkard said:**
> Please mark as 'Solved'.

The issue is solved. Thanks to all.

---

### Post by Zill on 2012-06-19
> **Pat Brown said:**
> :KS It finally worked. I now have a printer. Much thanks to all!
I am pleased you got the printer working.  However, as other users may find this thread via search engines, it will be helpful if you report back *exactly* what you needed to do to achieve this.  This will help other users to know if the HL-2240 works "out of the box" or if they need to do anything else to get it working.

Regarding "marking the thread as solved", this is done via the "Thread Tools" menu near the top right of the screen.  Note that this can *only* be done by the originator as it sets a "flag" on the thread to help other users see, from the title, if a thread is solved or not.

---

### Post by caseyjeaux on 2012-10-08
I found these instructions from a 2007 post for a different Brother model. I amended them to suit the HL 2240. I hope it will help others as it helped me. My strongest advice is to be very aware of letter case when typing into Terminal. 



Step 1:
Open Terminal by selecting Applications ---- Terminal from the task bar. 

Step 2:
Type or Copy & Paste the following into Terminal and press enter:  
 
sudo apt-get install tcsh

Step 3: (don't know if it matters but I did it anyway)
From the task bar go to: System ---- Administration ---- Printing, select your printer that's not working then select edit and click delete.

Step 4:
Download the LPR Driver and CUPS Wrapper. Locate your model & download your "Debian" (The deb format) LPR printer driver from HERE: ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)).
 
Locate your model & download your "Debian" (Again, The deb format)  CUPS wrapper from  the same page.
 
Step 5:
Now change to the directory to which the drivers were downloaded. Presuming you downloaded the driver to your desktop Type or Copy & Paste the following into Terminal:
 
cd Desktop (In my case cd Downloads)

Step 6:
Create the lpd directory. This is the first I have encountered this but in Hardy the directory had to be created. Skip this and move on to Step 7 if you're using Gutsy or below. In terminal Type or Copy & Paste the following command:

sudo mkdir /var/spool/lpd

Step 7:
Install the LPR Driver. In terminal Type or Copy & Paste the following command: 

sudo dpkg -i --force-all hl2240lpr-2.1.0-1.i386.deb

Step 8:
Create the model directory. As with the lpd directory this is the first I have encountered this but in Hardy the directory had to be created. Skip this and move on to Step 9 if you're using Gutsy or below. In terminal Type or Copy & Paste the following command:

sudo mkdir /usr/share/cups/model
 

 If you get error message: mkdir: cannot create directory `/usr/share/cups/model': File exists
 

 This is OK. Go on to step 9. 


Step 9: (This is the part that drove me crazy. The original instructions had a driver for another printer model that I had to delete, and then type in my printer driver file name. After the lpr file went so smoothly, I couldn't see why the cupswrapper file wasn't found. Then it finally dawned on me. The model number of my saved file was in caps HL2240. After I entered that into terminal, all was well again.)
 

 Now install the CUPS wrapper driver. In terminal Type or Copy & Paste the following command:
  
sudo dpkg -i --force-all cupswrapperHL2240-2.0.4-2.i386.deb
 

 Step 10: From the task bar go to: System ---- Administration ---- Printing, select your printer and click Print Test Page.  
 

 Or from Unity, click on dash; type printers; click on printers icon. The HL 2240 should be there. Click on the printer, and click print test page.  That's It.


Good Luck,
Gary

---

