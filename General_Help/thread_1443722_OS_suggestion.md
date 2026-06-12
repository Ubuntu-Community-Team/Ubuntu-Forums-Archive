---
title: "OS suggestion"
date: 2010-03-31
forum: General Help
---

### Post by jazzersaxman on 2010-03-31
I am in need of advice...I have my home server up and running (ubuntu) connected to several MS Vista HP machines...I am having difficulty making stuff cooperate using Vista...needless to say, I liked XP better, but am wondering if anyone has used Windows 7 with Ubuntu and what do you think?  Is it worth the $ to upgrade to Windows 7 to make my whole "network" communicate better?  Vista was a waste and it's a matter of time before I upgrade, but I was wondering if now was a better time? or should I stay with Vista...

Thanks...

---

### Post by new_tolinux on 2010-03-31
First I have to say that Windows 7 is much better in my opinion than Vista ever was. My laptop was pre-installed with Windows Vista and it's running Ubuntu yet (for the past year or so). My computer was pre-installed with Windows Vista and it's running Windows 7 yet (dual boot with Ubuntu 9.10, but Windows is used most).

But what problems do you have with your network communication?
It can be Windows-related, but it can also be something in your hardware or your settings.

---

### Post by jazzersaxman on 2010-03-31
> **new_tolinux said:**
> First I have to say that Windows 7 is much better in my opinion than Vista ever was. My laptop was pre-installed with Windows Vista and it's running Ubuntu yet (for the past year or so). My computer was pre-installed with Windows Vista and it's running Windows 7 yet (dual boot with Ubuntu 9.10, but Windows is used most).

But what problems do you have with your network communication?
It can be Windows-related, but it can also be something in your hardware or your settings.

I am having print-server issues...Vista is giving me a consistent error 0x00000d when trying to connect to my Ubuntu printer.  I've heard through research that it's a vista issue mostly because I have the Premium Home edition, and it's not as cooperative.

---

### Post by new_tolinux on 2010-03-31
It should be perfectly possible to connect Vista to any network printer by the use of \\server\printername

If Vista isn't going to do it, my best guess is that 7 Home Premium isn't going to do it eiter.

---

### Post by jazzersaxman on 2010-03-31
> **new_tolinux said:**
> It should be perfectly possible to connect Vista to any network printer by the use of \\server\printername

If Vista isn't going to do it, my best guess is that 7 Home Premium isn't going to do it eiter.

Yeah, I tried the network printer stuff, and it's not working..I tried tricking windows, etc. nothing is working...I thought if maybe I got the Prof version, networking issues would be easily resolved as opposed to the Home Prem. version...

---

### Post by new_tolinux on 2010-03-31
I'm pretty sure it won't, but I can't test it since the main Linux machine does not have a parallel port to attach my printer.
I don't really know why it's not connecting, but I think it is possibly related to a rights-issue. But then, I can't test that either.

---

### Post by bwitherell on 2010-03-31
Do you have all the latest patches and service packs installed for Vista?
What is the service pack level of the PC running Vista?
Do you have the Windows Vista version of the print drivers installed for the model of your printer?

What is the make and model of your printer?

Can you connect that printer to your Vista PC directly via USB or Parallel port and print? (as a test to see if that PC is working with that printer at all)

---

### Post by jazzersaxman on 2010-03-31
> **bwitherell said:**
> Do you have all the latest patches and service packs installed for Vista?
What is the service pack level of the PC running Vista?
Do you have the Windows Vista version of the print drivers installed for the model of your printer?

What is the make and model of your printer?

Can you connect that printer to your Vista PC directly via USB or Parallel port and print? (as a test to see if that PC is working with that printer at all)

My service pack is SP2, the printer is a Canon MP830 and yes, I was using the printer on my vista system both on my desktop (64bit) and laptop (32bit) vista versions... my drivers were current, but I have since uninstalled all the printers in Control panel and I have no printers listed...but the issue was before and during my having printers on the printer list (hope that made sense)...

---

### Post by burton247 on 2010-03-31
I haven't yet installed windows 7 yet so can't test anything out. It seems expensive to upgrade but if you have to you have to. Could you find someone with a win7 system you can test it with, or even download a trial to test it first? It would be better to not have to spend money but i cannot think of anything, besides win7 is supposed to be a lot better anyway

---

### Post by bwitherell on 2010-03-31
I am assuming that you had this working across the network with XP?
and that you are sharing the printer on Ubuntu via SMB (Samba)?

Is this correct?

---

### Post by jazzersaxman on 2010-03-31
> **bwitherell said:**
> I am assuming that you had this working across the network with XP?
and that you are sharing the printer on Ubuntu via SMB (Samba)?

Is this correct?
yep...this is correct...it's funny...Windows "sees" the printer, but won't connect...don't get it...

---

### Post by bwitherell on 2010-03-31
Try connecting the printer to your computer directly and installing the drivers. Then print a test page to make sure all is well.
Then without uninstalling anything, disconnect the printer and connect it back up to the Ubuntu server and try again.

Also, it might be a good idea to recheck your samba config file.

Also, try using one of the windows boxes as a print server and try printing to it from one of the vista boxes then. This way we can see if it is a vista issue or Ubuntu issue.

---

### Post by jazzersaxman on 2010-03-31
> **bwitherell said:**
> Try connecting the printer to your computer directly and installing the drivers. Then print a test page to make sure all is well.
Then without uninstalling anything, disconnect the printer and connect it back up to the Ubuntu server and try again.

Also, it might be a good idea to recheck your samba config file.

Also, try using one of the windows boxes as a print server and try printing to it from one of the vista boxes then. This way we can see if it is a vista issue or Ubuntu issue.

Beat you to it...I did connect the printer and installed the driver and test print worked fine, reconnected it to the Ubuntu box...no good...still the 0x00000d error...

Prior to using ubuntu I had my 2 vista systems printing back and forth no problem...one reason of many I made a server was so I didn't have to keep my 1 computer on and logged in to print from my laptop somewhere else in the house...I hate windows...

---

### Post by bwitherell on 2010-04-07
Have you setup the samba share where the Vista computers will look for the print drivers? the UNC path for the share should be \\Your-Ubuntu-servername\print$

The Vista drivers for the printers have to be put in this folder.
(the inf,sys,ini files. Not the EXE setup files)

For more info please refer to this link. [http://www.netadmintools.com/art258.html]("http://www.netadmintools.com/art258.html")

Please post your results.

Thanks.

---

