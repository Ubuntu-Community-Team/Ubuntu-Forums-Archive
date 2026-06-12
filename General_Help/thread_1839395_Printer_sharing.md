---
title: "Printer sharing"
date: 2011-09-05
forum: General Help
---

### Post by Mikeriggin on 2011-09-05
I am new to Ubuntu. I have it installed on a desktop computer with a HPOfficejet Pro 7650 all in on printer attached via USB. The printer works fine on this computer. I need to share this printer with three laptops which connect via wireless. One runs WinXP and the other two run Win7. I have selected the share printer option, the printer shows up on the other computers but  won't print. Says spooler not running. Any ideas? If I can't get this to work, I am afraid Linux will be just a novelty to me. I really want to make this work. I welcome any advice.

---

### Post by cap10Ibraim on 2011-09-05
search and learn more about samba server , you can use it to share files and printers
you can find samba server in Synaptic Package Manager

---

### Post by Mikeriggin on 2011-09-05
OK, I found and installed samba, now what? I can't find it anywhere, but it said it was installed...

---

### Post by garvinrick4 on 2011-09-05
What are you running on the host machine for the printer?

---

### Post by Mikeriggin on 2011-09-05
Host machine is running Ubuntu 11.04

---

### Post by cap10Ibraim on 2011-09-06
you can check if samba server is running with 
```
service smbd status 
```
to start it 
```
sudo service smbd start
```
to stop it 
```
sudo service smbd stop
```
and visit this doc (the manual section)  [https://help.ubuntu.com/community/Samba/PrinterSharing](https://help.ubuntu.com/community/Samba/PrinterSharing)

---

### Post by Mikeriggin on 2011-09-07
OK, I tried that. It says Samba is running, but still can't print. Do I need to configure it or something? How do I fnd it?

---

### Post by Mikeriggin on 2011-09-07
Again go to System -> Administration -> Printing 
Click "New Printer" in the upper right. In the next menu select "Windows Printer via SAMBA". Now enter your Ubuntu Samba Print Server (set up as above) IP address in the box on the left titled "smb://". Click the "Browse" button. 
Select the printer in the "SMB Browser" window (Click on the little arrows). Once you have selected your printer, check the "Authentication required" and enter your samba user name and password. Then click the "Verify" button. You should see confirmation that the share is available. 
Click the "Forward" button and install the drivers for your printer as you would for any other printer.

I don't understand this. What is samba print server (set up as above) IP address. How do I find it?? When I follow the first steps above, it shows one computer on my network, not the other two and certainly no printer. This is very frustrating, It shouldn't be this hard.

---

### Post by Mikeriggin on 2011-09-11
Well, I've been trying to make this work for a week. Still no joy. I have come to the conclusion that, sadly, Linux is just not for me. For years I have wanted to give it a try. I have now tried it and will now go running back to Microsoft joyously. I guess if you just surf the net and read email, it's great. I, however need to have a printer shared with three other computers. I also need to run Quickbooks for my business. I tried Virtualmachine and couldn't figure out how to make that work either. So, in conclusion, I will say thanks for the precious little help I received here. In the future, I will never be so naive as to believe that something free will be as good as a mainstream product.

---

### Post by markMDW on 2011-12-03
"I am new to Ubuntu."  ..  "I don't understand this." .. "Linux is just not for me"
<hr>
-----------------------

Sorry to hear that this isn't as easy as you hoped and that as a result you will be switching back to Windows.  Most folks with Windows have accumulated hundreds if not thousands of hours learning the Windows way of doing things.  Also, they've accumulated many hours of frustration during the process. Some have endured those many long hours without realizing that there *IS* an alternative out there (besides *just* MacIntosh.)    For those that give up on Linux, I imagine their investment in this system is much smaller than with Windows, comparing Time, Money and Learning Experiences slowly but steadily over the years.

If you learn just one thing from Linux during your venture with it, I hope its not just some step by step click or command, but rather that Linux is the Epitome of Freedom in Software, and that users DO have a choice.  If you ever attempt Linux again, be sure not to immediately assign it the most important function of system network until you accumulate a roughly equivalent amount of time with it as you had from the system you are replacing.  Start small and grow big in knowledge little by little.  We all learned to walk before we ran.  Much of the Linux World is dig, find, learn (over and over).  That's how Windows users learned Windows, over vast amounts of time, frustration and learning.  

I hope you try converting an old pc you are about to discard into an Xubuntu system, just for browsing, and I can then imagine you slowly learning the skills you need one step at a time at your own pace without the frustration of getting a crucial function to work.  Over the months your knowledge will expand without even a realization.  That's the way it works with MacIntosh, Windows and Linux, and lesson be learned, Linux is no exact replacement for either, but as the owners of Google Android Kindle etc, have learned, Linux works and Linux makes them $$$, and without it there would not have them in our vocabulary today.


I'm no expert in Linux, but  I now use it (Ubuntu) more often than Windows, including Windows7, mainly because I value Freedom in Software most of all, and I feel trapped inside their domain constantly telling me its time to renew their Word, their Office, their Spyware, their AntiVirus, their Games, their popups galore..  But it makes some folks feel they have something important installed when they have to punch in their credit card numbers every year to keep using it.
 
And so over time, ever since first discovering OpenOffice.Org,  I've learned much of what I needed to know to get things done.  Just today I tried to find out how to install the SAMBA Server for Print Sharing with Windows machines.  I don't know if it will work for me, but I probably have a better chance at it because I've already read many of the Ubuntu guides and know a lot of the background that may seem to technical to a complete newbie.  

Good Luck, and just remember to tell folks who curse their Windows machine that there is something else they can try for free.  Tell them to install it (Xubuntu) on a computer they are about to give away or throw away, and surf they net all they want.  Let them learn little by little, starting with the excellent word processors and spreadsheets.  And tell them that there will never be a popup asking them to enter their credit card number to renew their expired Trial Software.  And tell them that once they spend a similar amount of time with this system as they have with their other, that if they value Freedom, then they will find that the Linux way of doing things is especially Superior.

Now I'm going to make a stab at using this tread to setup my print server to print Non-Freedom operating systems.

---

### Post by oldtimer7777 on 2011-12-03
Here is how I have my Printer configured to share over the network. It cost me about 10 dollars for a ethernet printer adapter on Ebay.

I installed a router, and I attached a Ethernet network USB adapter to my router, and then I connected the printer to that Printer Adapter which is attached to my router switch.  Now anything that connects to my router wifi, regardless of whatever OS is running on those other machines is able to see and print from that network printer.  Any other method is slippery from my own experience and you don't have to always have a computer running to act as a printer server this way either, and makes things more convenient and trouble free.

> **Mikeriggin said:**
> I am new to Ubuntu. I have it installed on a desktop computer with a HPOfficejet Pro 7650 all in on printer attached via USB. The printer works fine on this computer. I need to share this printer with three laptops which connect via wireless. One runs WinXP and the other two run Win7. I have selected the share printer option, the printer shows up on the other computers but  won't print. Says spooler not running. Any ideas? If I can't get this to work, I am afraid Linux will be just a novelty to me. I really want to make this work. I welcome any advice.

---

### Post by markMDW on 2011-12-05
My printer shares across the network.  I have it connected to a Ubuntu 10.04 Desktop.  Connected through Wi-Fi to the network is a laptop that can print to it (while running Xubuntu 10.04).  It has a dual boot and can run it's original Windows Vista, but if booting from Windows it can't discover the printer shared with the SAMBA network.  It searches and searches and searches for it.  When I run the laptop as usual under Xubuntu (which boots, runs and shutdowns MUCH faster than Windows)  The printer is automatically available to the Xubuntu-laptop anytime the Ubuntu-desktop is on. 

I suspect the problem is with an insufficiency inside Windows.  That same laptop prints just fine whenever I run under Linux Xubuntu.  I haven't really really troubleshooted the Windows installation though.  It ought to just work, period -- no effort required.  I should have known Window's would need you to buy something else to get it to work, even after already making $Billions on their products.

Thanks for the advice.  I think I will buy the printer adapter so Windows will work too.  :P
:lolflag:

---

