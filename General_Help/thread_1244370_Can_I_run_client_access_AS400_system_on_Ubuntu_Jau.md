---
title: "Can I run client access AS/400 system on Ubuntu Jaunty?"
date: 2009-08-19
forum: General Help
---

### Post by usmc7356 on 2009-08-19
Hello everyone.

I am an absolute noob with ubuntu/linux.  My computer experience is mainly with xp and have recently decided to give ubuntu a shot.  I am trying to get it running on a few work computers with our ibm as/400 series so that we can still do all of our daily functions at work and have a free os.  I am tired of flashing pcs every 2 weeks with xp and having to call microsoft and tell them to renew my key on each of the comps.  I have quite a few 40-65 year old employees at work who have a hard time logging in to email and can manage to damage a registry no matter how many group policies are in place.  I have the client access windows installer for pc and used WINE to open it and get it to install.  Using WINE I can get the program up visually and see that it is establishing a connection to the AS/400, however I can not actually get the 5250 emulator to run.  It gives me an error: CWBEMCFD.DLL could not be loaded system error 126: module not found when trying to run a new session.[IMG]http://ubuntuforums.org/home/conquistador/Desktop/Screenshot-PC5250.png[/IMG]  Forgive me for being such a noob but I have now been around ubuntu for about 2 weeks... Any help would be greatly appreciated.  For all I know I can't even run this on ubuntu.

---

### Post by The Cog on 2009-08-19
There is a package called tn5250 in the Ubuntu repositories taht should do the trick for you. 
Menu System->Administration->Synaptic Package Manager, then search for tn5250. Mark for installation and apply. Apparently there is a script called **xt5250**, or you might be able to run **tn5250** from gnome-terminal.

---

### Post by usmc7356 on 2009-08-19
Ok i installed the tn5250 thing and it looked like it was trying harder to get into the system, but it still didn't work.  I get the same "system error 126" saying it can't find that .dll file.  I am not sure what a gnome terminal is or how to run anything in it.  Please feel free to talk to me like I am an idiot as I have no experience in ubuntu.  I am still trying to figure this terminal thing out for all its apps...  Thanks for the quick reply though!  I am not sure what to do with the xt5250 script either, or how to even find it or what it even is...

---

### Post by usmc7356 on 2009-08-19
here is the screenshot error...

---

### Post by mjwalfredo on 2009-08-19
Hi usmc7356, what The Cog suggested, tn5250, is actually a 5250 emulator that runs natively on Linux. It is not going to help you to run Client Access through Wine.  Maybe someone else can chime in on how to get the missing DLL to get Client Access working.

What I can tell you is that tn5250 is a "terminal application".  To run it, go to Applications --> Accessories --> Terminal.  Once that loads type "tn5250" and press enter to get a list of options for the command.

If you don't need to specify any special options, you should be able to connect to you AS/400 by typing: "tn5250 as400ipaddress" and pressing enter.

I have not tried tn5250 but I am curious to hear how it works out for you if you try it.  I am sure it won't have all the features that Client Access has, especially things like iSeries Navigator but it should get you a basic terminal.

I hope someone can help you get Client Access running in Wine, that would be awesome.  Good luck.

---

### Post by usmc7356 on 2009-08-19
I have actually found the .dll that it says it is missing, in the folder that it should be on if it was 95-xp, so it actually isn't missing anything...

---

### Post by mjwalfredo on 2009-08-19
Well curiosity got the best of me and I tried tn5250.  It seems to work just fine.  I attached a screenshot so you can see.

---

### Post by mjwalfredo on 2009-08-19
> **usmc7356 said:**
> I have actually found the .dll that it says it is missing, in the folder that it should be on if it was 95-xp, so it actually isn't missing anything...

Where did you find the DLL?  Is it in one of these locations that the Wine Documentation lists as being searched?


This function searches directories in the following order: a) The directory the program was started from. b) The current directory. c) The Windows system directory. d) The Windows directory. e) The PATH variable directories. In short: either put the required DLL into your application directory (might be ugly), or usually put it into the Windows system directory.

---

