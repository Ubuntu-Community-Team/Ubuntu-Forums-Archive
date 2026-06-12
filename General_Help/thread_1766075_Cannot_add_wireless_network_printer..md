---
title: "Cannot add wireless network printer."
date: 2011-05-23
forum: General Help
---

### Post by mclizardman on 2011-05-23
I can't add the network printer to Ubuntu 11.04. I click on Windows Printer Via Samba, then browse, then the printer shows up. I click on it, and nothing happens, and I can't hit the OK button. Why???? The printer is shared. Thanks. Here is a screen shot.

---

### Post by Bucky Ball on 2011-05-23
Please more detail. What make/model of printer? Are you using a router? Are you using static IP address for the printer? Is it working okay with a cable and are any other machines accessing it wirelessly? ;)

---

### Post by mclizardman on 2011-05-23
> **Bucky Ball said:**
> Please more detail. What make/model of printer? Are you using a router? Are you using static IP address for the printer? Is it working okay with a cable and are any other machines accessing it wirelessly? ;)

Okay, printer. Cannon MP560. Yes, I am using a router, but am not wireless. Honestly not sure what a static IP address is. There are three other laptops running windows 7 accessing it wirelessly.

---

### Post by Bucky Ball on 2011-05-23
Try:

System>Administration>Printing>Add Printer. In the left panel  of the Add Printer GUI there is a list of printers. Wait! It takes  awhile to pick up all devices. Does your printer pop up there after a  minute or two?

How is it shared (through the router)? You shouldn't need to use samba to access the device in Ubuntu. If the router is not wireless you would be accessing the printer directly. You have the appropriate drivers installed for that printer?

[http://support-au.canon.com.au/P/search?model=PIXMA+MP560&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=PIXMA+MP560&menu=download&filter=0&tagname=g_os&g_os=Linux)

---

### Post by mclizardman on 2011-05-23
> **Bucky Ball said:**
> Try:

System>Administration>Printing>Add Printer. In the left panel  of the Add Printer GUI there is a list of printers. Wait! It takes  awhile to pick up all devices. Does your printer pop up there after a  minute or two?

How is it shared (through the router)? You shouldn't need to use samba to access the device in Ubuntu. If the router is not wireless you would be accessing the printer directly. You have the appropriate drivers installed for that printer?

[http://support-au.canon.com.au/P/search?model=PIXMA+MP560&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=PIXMA+MP560&menu=download&filter=0&tagname=g_os&g_os=Linux)

Ugh. Tried to install that driver, but its a tar.gz. Not exactly a strong point of mine, as in I have no idea how to use those. And, no it didn't show up.

EDIT: oh, and I think it needs to be shared through a connected computer, because it doesn't show up in SAMBA when the other connected computers are on.

---

### Post by Bucky Ball on 2011-05-23
So it is plugged in to another computer? The machine is a wireless printer? You should be able to connect with it directly (unless you have a wireless router in which case it should be connecting wirelessly with that).

I would plug the machine directly into you machine (with USB) and see what pops up re. drivers for it. If it connects 'automagically' and is usable via USB, then you probably have drivers. But ... you are not going to get far without a driver for the machine I don't think. 

So you have four computers, three wirelessly connected (how? directly with the printer?) and your Ubuntu machine which is not connecting. 

Another method is to plug the machine directly into your router via a cable and see what happens on your Ubuntu machine (in add printer, see if it shows up). If it shows up check the details. To get all set IP addresses and wireless configuration I press a button on my wireless printer. If you can output the Printer Settings from your machine you will get all that information. It should give you the wireless IP and details (SSID, security type, etc).

---

### Post by mclizardman on 2011-05-24
> **Bucky Ball said:**
> So it is plugged in to another computer? The machine is a wireless printer? You should be able to connect with it directly (unless you have a wireless router in which case it should be connecting wirelessly with that).

I would plug the machine directly into you machine (with USB) and see what pops up re. drivers for it. If it connects 'automagically' and is usable via USB, then you probably have drivers. But ... you are not going to get far without a driver for the machine I don't think. 

So you have four computers, three wirelessly connected (how? directly with the printer?) and your Ubuntu machine which is not connecting. 

Another method is to plug the machine directly into your router via a cable and see what happens on your Ubuntu machine (in add printer, see if it shows up). If it shows up check the details. To get all set IP addresses and wireless configuration I press a button on my wireless printer. If you can output the Printer Settings from your machine you will get all that information. It should give you the wireless IP and details (SSID, security type, etc).

Yeah I have four machines. Three are connecting to it wirelessly. It isn't physically connected to anything but the outlet. It's wireless. I don't think it has a cable to be plugged into the router directly with it.

---

### Post by Bucky Ball on 2011-05-25
Gotcha. No, not shared through another computer I wouldn't think. Are all other machines using the  IP address of the *printer* and not one of the computers? If so, they are not reliant on one of the machines being on. If you can print from each of the machines without the other two being on you will confirm this.

So; 

System>Administration>Printing>Add Printer. 
Click the arrow next to 'Network Printer' in the pane on the left. 
Wait. It can sometimes take awhile for the printer to come up.

Do you see it there? If so, time to set it up. Let us know. ;)

---

### Post by mclizardman on 2011-05-25
> **Bucky Ball said:**
> Gotcha. No, not shared through another computer I wouldn't think. Are all other machines using the  IP address of the *printer* and not one of the computers? If so, they are not reliant on one of the machines being on. If you can print from each of the machines without the other two being on you will confirm this.

So; 

System>Administration>Printing>Add Printer. 
Click the arrow next to 'Network Printer' in the pane on the left. 
Wait. It can sometimes take awhile for the printer to come up.

Do you see it there? If so, time to set it up. Let us know. ;)

Sorry, but it didn't come up. Sorry for the slow reply, so busy this week.

---

### Post by Bucky Ball on 2011-05-25
Okay, I'd say you need to install the driver and add the printer manually. I'll have a look at it all later today (tonight). You need to check the manual (or their website) and see what kind of printer you need to add it as. For instance, LPD/LPR. In that case, you would need to add the IP of your printer under 'Host' and get the correct details for the other one. 

Just got up and have a busy day myself so check back later.

---

### Post by demonipuch on 2011-05-26
Hello

I've got the same printer (Canon MP560). My printer at home is connected to my wifi network and everything is working fine.

First, check your wifi settings on your printer (SSID, WPA keys). You can print your printer network settings (you should be able to print those settings by using the rolling menu on your printer screen. Something like "Settings > Network settings > Print network settings")

Then, are you printer drivers installed correctly? The drivers provided by Canon come with a script that automated the printer installation. Did you use this script or did you just installed the .deb files?

If you have simply installed the .deb files, you can try to turn off your printer, open the Printing administration window (Systme > Administration > Printing) and click Add printer. Then turn on your printer and in the network printer field type the printer IP address (you got from step 1) if your printer didn't show up. Then click Probe. Add your printer. You'll be asked to choose a .ppd file. Browse to /usr/share/ppd directory and add canonmp560.ppd.

If everything went well you should be able to print a test page. 
Hope it helped a bit.

PS : sorry for my english, I'm french...

---

