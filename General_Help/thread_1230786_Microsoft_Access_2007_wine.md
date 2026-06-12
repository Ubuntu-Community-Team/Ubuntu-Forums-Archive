---
title: "Microsoft Access 2007 wine"
date: 2009-08-03
forum: General Help
---

### Post by devil81 on 2009-08-03
Hi:

I know that the WineHQ website says that access currently does not work under wine. But also found a page on this website that said that it was possible with a few tweaks to get it to work. So I decided to give it a go. I've solved several issues thus far including altering the access manifest file to remove it DAO dependencies as well as putting into the system 32 folder of wine msvcp80.dll and msvcr80.dll and installed vcrun2005 etc using the winetricks shell script.  But I am now getting the following error:

[B]Runtime error

Program: C:\Program Files\Microsoft Office\Office12\MSACCESS.EXE 

r6034

an application made an attempt to load the C runtime library incorrectly....  
[/B]
 
I know you're probably asking yourselves why bother with an overblown piece of "£$% like access?

Well I'm due in September to starting teaching at a college that has a strong reliance on Office products and still insists on teaching basic db skills using access so I want to try and get it up and running before then and I am starting to really like ubuntu and would loath to have to boot in and out of windows and ubuntu, if I can help it.

So any help will be much appreciated.

devil81

---

### Post by clonne4crw on 2009-08-08
I personally have had terrible luck trying to get ANY MSOffice product working in wine, so I feel your pain. I wish that OpenOffice was more compatable with MS Office, because that would allow me to use it for school work. But, no, I am pretty much forced to use s*** like MS Office.  

Have you considered just setting up a virtual machine running XP or 2000 to just run office?

---

