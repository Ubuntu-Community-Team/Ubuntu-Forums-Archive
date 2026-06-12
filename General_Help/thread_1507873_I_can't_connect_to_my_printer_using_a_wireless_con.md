---
title: "I can't connect to my printer using a wireless connection."
date: 2010-06-12
forum: General Help
---

### Post by BurningSludge on 2010-06-12
[FONT=Comic Sans MS][SIZE=3]I have been fiddling around with getting my printer (HP Officejet 6500 Wireless All-in-one Printer - e709n) connected to laptop (Toshiba Satellite L455D) for nearly a month. I am running Ubuntu 10.04. I have never been able to successfully connect it using the ad hoc but the printer always worked using a USB connection. It is a shame because this may be the only thing preventing me from going all Linux.[/SIZE][/FONT]

---

### Post by bobcollard on 2010-06-12
> **BurningSludge said:**
> [FONT=Comic Sans MS][SIZE=3]I have been fiddling around with getting my printer (HP Officejet 6500 Wireless All-in-one Printer - e709n) connected to laptop (Toshiba Satellite L455D) for nearly a month. I am running Ubuntu 10.04. I have never been able to successfully connect it using the ad hoc but the printer always worked using a USB connection. It is a shame because this may be the only thing preventing me from going all Linux.[/SIZE][/FONT]
Connect your printer and modem to a router.  Then look for the printer under Printing in System Menu checking Networked Printers.  Your laptop will work with it as well.

---

### Post by BurningSludge on 2010-06-21
[FONT=Comic Sans MS][SIZE=3]That is a no can do because my strongest source of Internet available is Mobil broadband.[/SIZE][/FONT]

---

### Post by bobcollard on 2010-06-21
> **BurningSludge said:**
> [FONT=Comic Sans MS][SIZE=3]That is a no can do because my strongest source of Internet available is Mobil broadband.[/SIZE][/FONT]
I take it this means your modem is attached and portable with your laptop?  Within range of your printer's wifi can you see the printer in your wireless network when you click on the icon in the Panel?  If so you would not need an AdHoc connection.  See my connection to my router as yours might be for your printer in this screen shot:

---

### Post by BurningSludge on 2010-06-21
[FONT=Comic Sans MS][SIZE=3]The printer seems to disconnect itself when I attempt to connect to it and I never get a full connection no matter how strong the signal is.[/SIZE][/FONT]

---

### Post by bobcollard on 2010-06-21
> **BurningSludge said:**
> [FONT=Comic Sans MS][SIZE=3]The printer seems to disconnect itself when I attempt to connect to it and I never get a full connection no matter how strong the signal is.[/SIZE][/FONT]
In "Printing" under System try adding a printer, (+) then under Network Printer see if it found your printer, the driver should install itself, then, make it your default printer.  See if that has any effect.

---

### Post by BurningSludge on 2010-06-21
> **bobcollard said:**
> In "Printing" under System try adding a printer, (+) then under Network Printer see if it found your printer, the driver should install itself, then, make it your default printer.  See if that has any effect.

[FONT=Comic Sans MS][SIZE=3]I was not able to find the printer on network.[/SIZE][/FONT]

---

### Post by BurningSludge on 2010-06-21
[FONT=Comic Sans MS][SIZE=3]I think 10.04 mis-configured the network to just this printer. Just today I was able to connect to someone else's HP printer and print to it. Is there some way to re configure this connection.[/SIZE][/FONT]

---

### Post by x C0MMAND0 x on 2010-06-21
If you are connected via mobile broadband on your laptop, then your printer will not be connected via mobile broadband, it sounds like that could be the issue.

---

### Post by bobcollard on 2010-06-21
> **BurningSludge said:**
> [FONT=Comic Sans MS][SIZE=3]I think 10.04 mis-configured the network to just this printer. Just today I was able to connect to someone else's HP printer and print to it. Is there some way to re configure this connection.[/SIZE][/FONT]
Yes, remove it and do the search again, it should come up.

---

### Post by bobcollard on 2010-06-21
> **x C0MMAND0 x said:**
> If you are connected via mobile broadband on your laptop, then your printer will not be connected via mobile broadband, it sounds like that could be the issue.
We are trying to get the computer to recognize the printer like a normal wifi connection which it is capable of doing.

---

### Post by BurningSludge on 2010-06-21
> **x C0MMAND0 x said:**
> If you are connected via mobile broadband on your laptop, then your printer will not be connected via mobile broadband, it sounds like that could be the issue.

[FONT=Comic Sans MS][SIZE=3]Okay, I want to connect to it via my RTL8187SE Wireless LAN Controller which is in my laptop and connects to every other source of WLAN.[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=3] How do I make this happen.[/SIZE][/FONT]

---

### Post by BurningSludge on 2010-06-21
> **bobcollard said:**
> Yes, remove it and do the search again, it should come up.
[FONT=Comic Sans MS][SIZE=3]Am I suppose to stick the Printer's USB in first because my connection to the printer drops before it is fully established.
[/SIZE][/FONT]

---

### Post by bobcollard on 2010-06-21
> **BurningSludge said:**
> [FONT=Comic Sans MS][SIZE=3]Am I suppose to stick the Printer's USB in first because my connection to the printer drops before it is fully established.
[/SIZE][/FONT]
Sorry, I don't quite understand.  Do you see the printer as already accepted in "Printing" under System?  That is where you should remove it and then restart Printers to find it and reinstall it.  See attached.

---

### Post by BurningSludge on 2010-06-21
> **bobcollard said:**
> Sorry, I don't quite understand.  Do you see the printer as already accepted in "Printing" under System?  That is where you should remove it and then restart Printers to find it and reinstall it.  See attached.
[FONT=Comic Sans MS][SIZE=3]I have removed the printer but re-installing it wirelessly is impossible because my connection to the printer drops to quickly, even if I'm right next to the printer. I want to make it so I can connect to the printer long enough to print something.[/SIZE][/FONT]

---

### Post by bobcollard on 2010-06-21
> **BurningSludge said:**
> [FONT=Comic Sans MS][SIZE=3]I have removed the printer but re-installing it wirelessly is impossible because my connection to the printer drops to quickly, even if I'm right next to the printer. I want to make it so I can connect to the printer long enough to print something.[/SIZE][/FONT]
Try hooking it up via USB and start a long text so it will stay long enough to connect, I'm getting out of my depth here. running out of ideas, sorry.

---

### Post by BurningSludge on 2010-06-21
> **bobcollard said:**
> Try hooking it up via USB and start a long text so it will stay long enough to connect, I'm getting out of my depth here. running out of ideas, sorry.
[FONT=Comic Sans MS][SIZE=3]Not possible because I can never actually connect wirelessly. Every time I click on the icon it cycles and then report that it has disconnected. Don't worry about running out of ideasbobcollard. I have been out of Ideas for nearly a month. I went to a couple experts and they said that I didn't have a problem. I am pretty close to swapping out the hardware but I'm not sure that would work because if the problem is from some kind of mis-configuration which I suspect is the problem, the problem may still persist after I changed the Hardware.[/SIZE][/FONT]

---

### Post by bobcollard on 2010-06-21
Just a thought, do you know the address of the printer, something like 192.168.1.3?  You might connect to it without using adhoc, use Infrastructure.  Make the IPv4 setting "link local only" or shared instead of DHCP.

---

### Post by BurningSludge on 2010-06-21
[FONT=Comic Sans MS][SIZE=3]Thank you [/SIZE][/FONT][FONT=Comic Sans MS][SIZE=3]bobcollard for helping me think. I finally have a stable connection the the printer by playing with the configurations. I changed the printer's connection setting to link local only in both IPv4 and IPv6, but kept the printer's SSID and left it in Ad-hoc mode. 
[/SIZE][/FONT]

---

### Post by bobcollard on 2010-06-21
Great, glad to help.

---

