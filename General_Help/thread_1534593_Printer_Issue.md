---
title: "Printer Issue"
date: 2010-07-19
forum: General Help
---

### Post by JasonSCarter on 2010-07-19
Hello All! I'm a total noob and I gotta a heck of a first post for  y'all... I'm running 9.10 Net Book Remix on a Dell Latitude D620.  Yesterday I plugged in my printer (HP C5150 photosmart) for the first  time, and it looked like it recognized and installed automatically.  Everything looked fine! Up until I tried to print something, that is. It  wouldn't print. It seems like it lost the printer, I go to the system /  administration / printing and it doesn't see any printers. Keeps  telling me its connected to local host. Then at the bottom left it says  it isn't connected. (it is plugged in, on and connected via USB  cable...) I go to trouble shoot it and it tells me CUPS has stopped. and  tells me to go to system / administration / services, but I don't have a  "services" icon. Nor do I have any icon I can find called cups, and the  cups web page wont come up.   Right now it will only give me the option  to "print to file" Please help. :D 

BTW I plugged in an older,  (but still working) HP Deskjet 3845 and it didnt even recognize it at  all  didnt try to install it or anything...:frown:

Jason

---

### Post by ubunterooster on 2010-07-19
Go to system/administration/printing. Press Ctrl+n. Does it show your printer (you may have to wait about three minutes if it does not show the printers right away)

---

### Post by JasonSCarter on 2010-07-19
> **ubunterooster said:**
> Go to system/administration/printing. Press Ctrl+n. Does it show your printer (you may have to wait about three minutes if it does not show the printers right away)

no it did not...:-k

---

### Post by JasonSCarter on 2010-07-20
Back to the top... anyone have any suggestions?

---

### Post by victorhugo289 on 2010-07-22
I have the same problem in Ubuntu 10.04, I plugged in my HP printer via USB, the printer was apparently recognized and it even showed a little icon in the top panel. I went to System--->Administration--->Printing and there's a printer in there with a green check mark.
I sent to print from Gedit and nothing happened, I tried the 'Print test page' and nothing happened either, it only shows the little printer icon momentarily and then the icon disappears very quickly.

---

### Post by JasonSCarter on 2010-07-22
wow victor I'm sad that this has happened to you but glad I'm not the only one as well! lol Is there anyone else willing to take a stab at this?

---

### Post by coffee412 on 2010-07-22
Sorry to hear that you are all having problems with your printers. Especially the HP's. Normally you should have no problems printing with hps. The only ones that I have ever hated are the Lexmarks. I avoid them like the plague. Anyways - 

What you need to do is download the linux driver package from HP and run thru the setup. The file name is hplip-3.10.4.run or similar depending on version. This should run your printer/scanner/fax with few problems. Just go to hps site and do a search for hplip and download and install in a term window.

HOpe this helps you all!

coffee :p

---

### Post by PRC09 on 2010-07-22
[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

---

### Post by ubunterooster on 2010-07-22
> **PRC09 said:**
> [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)
Or ```
sudo apt-get install hplip
```Preferably the second

---

### Post by JasonSCarter on 2010-07-22
Ok thank you we'll try that!

---

### Post by JasonSCarter on 2010-07-22
It's not working for me, still saying Cups is failing...and not recognising the printer, and is on local host...printing to file... nothing has changed :(

---

### Post by victorhugo289 on 2010-07-23
Definitely, HPLIP solved the issue, I downloaded it directly from HP website: hplip-3.10.5.run.
You have to install the .run file first and then plug your printer in after reboot. I think it is also a good idea to first delete any previous printers that appear in System ---> Administration ---> Printing, so that your system is clean before installing HPLIP.
The website also shows all the 'Supported printers'. Give it a try.

[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

---

