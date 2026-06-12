---
title: "networked printer says it is working, but it isn;t"
date: 2009-08-11
forum: General Help
---

### Post by LinuxBob on 2009-08-11
It works using my Laptop with Fiesty but using same install for my Zareason with Jaunty it says the job is gone to the printer but nothing prints out.

OK success acessing HP LaserJet via DLink print serve doing the following from another thread:

*** the localhost:631 option worked perfectly when installing my networked HP Photosmart P1000 printer using a DLink DP-311U print server. For those of you new to Linux (as I am!), here's how:

* Open your web browser and type in "http://localhost:631" into your address box.
* Click on the "Add Printer" button.
* On the "Add New Printer" page, enter the following information:
- Name: <name for your printer, BUT DON'T USE ANY SPACES! For example, mine is simply "HP1000">
- Location: Doesn't matter. Leave blank, if you want. Or enter the location of Jimmy Hoffa's body, for that matter. Yer choice.
- Description: Doesn't matter. I entered the full name of my printer, which is "Photosmart P1000".
* Click "Continue"
* You should now see a box marked "Device". It's a drop-down menu. Since I'm using a DLink print server, I chose "LPD/LPR Host or Printer". You may have a different device.
* Click "Continue"
* You should see a box named "Device URI". Again, if you're using a DLink 311U (as I am), type in "socket://<DLink IP address>. For example, the IP address of my DLink is 192.168.100.55. So, I typed in "socket://192.168.100.55".
* Click "Continue"
* You now need to enter the manufacturer of your printer. I scrolled down and selected "HP".
* Click "Continue"
* Yet another page that might trip you up. You need to select the particular model of your printer. The problem is that there are several models of "HP Photosmart P1000" listed. I selected the "HP Photosmart P1000 Foomatic/hpijs (recommended) (en)". There seems to be one that is "recommended" for each model. I suggest going with that for the first try. If it doesn't work, you will have to try others.
* Click "Add Printer"
* If everything works, you should see a message such as, "HP1000 successfully added!"

You should see a tab along the top of the page that says, "Printer". Select that, then look for a button "Print Test Page". If you press that button and get a proper print-out, you're set!***

Now the weird part. Doing the samer thing from my new Zareason Ion Breeze I can set up the networked printer but when I hit print tests page the Ion Ubuntu tells me everything printed out fine, no wait, no delay, all is cool. But it isn;t. Nothing printed out. I changed the 4L device and same thing.

Any ideas????????

---

### Post by LinuxBob on 2009-08-17
bump

need to get this working would appreciate any insights

---

### Post by LinuxBob on 2009-08-18
The network printing problem is solved.  I bought a new all in one wireless capable printer and it worked first time with the Zareason using the localhost:631 network printer setup.  That led me to believe the Dlink printer server had a permission issue.  That was the case.

The DP-301P+ requires a mac address when the user permission feature is turned on.  The Dlink accepts a mac address with a space between the hexadecimal pair of numbers, not a colon.  

Thanks for all the helpful responses to my posts.

---

