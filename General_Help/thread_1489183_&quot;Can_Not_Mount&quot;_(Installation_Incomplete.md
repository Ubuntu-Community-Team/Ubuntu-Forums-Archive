---
title: "&quot;Can Not Mount&quot; (Installation Incomplete)"
date: 2010-05-20
forum: General Help
---

### Post by Jdean983780 on 2010-05-20
Thanks in advance for your help:
Today I downloaded and installed the ubuntu system from this page below:
[http://www.ubuntu.com/getubuntu/download-wubi](http://www.ubuntu.com/getubuntu/download-wubi)

The installation completed properly as far as I know, however upon the first restart of my computer
after the installation I received a error message (black screen. white text) as follows:

Can Not Mount
/dev / loop1 / (/cdrom/casper/filesystem,Squashfs ) On //Filessystem,squashfs 

This all presented itself just after the little "Ubuntu" splash screen appeared.
** I did attempt to start Ubunbtu several times but received the same error message
each time...I also tried the "Safe start" option and also received the same error message  

More Info:
I use the Windows 2000 operating system
I have more than enough storage space (139gb)
I use the Norton "Go-back" recovery system which loads prior to my O/S options screen

Any help would be appreciated and If you advise me to remove it from my computer to try
the cd disk or reinstall please advise me how to remove it.....
Thank you....Johnny

---

### Post by cariboo on 2010-05-21
For some reason your install wants to mount the Live CD during the boot process. I would suggest you boot from the Live CE and once at the initial Screen with the little man and keyboard, press the any key to see the menu. Use the arrow keys to select boot from the hard drive, to see if that works. If you can get to the desktop, just right click the CD icon on the desktop to eject it properly.

---

### Post by Jdean983780 on 2010-05-21
Thank You Cariboo,
I apologize for my ignorance regarding your assistance, however I do not understand your helpful instructions:

1.) (Live CD)< Are you referring to a actual "compact disc" OR My "compact disc drive"??
OR is this terminology for something else?  

2.) (Live CE) < What is this? and is this listed in the Ubuntu boot options? 
OR are you referring to a copy of Ubunto burnt to a CDR , which is downloaded from the internet?
If you are referring to a burnt copy and booting from it, then will I always have to start Ubuntu from it?

3.) Your words>>"click the CD icon on the desktop to eject it properly." 
Cariboo, I do not have a "CD" in my CD drive to eject properly...

---

### Post by Jdean983780 on 2010-05-21
After reading your instructions several more times, it appears you may of overlooked the first part of my initial message...

I have not installed Ubuntu from a disc but rather from the "online page" below
[http://www.ubuntu.com/getubuntu/download-wubi](http://www.ubuntu.com/getubuntu/download-wubi) 
therefore I have no disc in my drive or one to boot from. or eject..

Again thanks for any help given....Johnny

---

### Post by ryan858 on 2010-05-21
This is a strange one... You may have to burn an installation cd (Live CD)... I don't know though, you should wait for a few more posts before doing anything...

---

### Post by sydbat on 2010-05-21
Jdean983780 - can you boot into Windows?

---

### Post by bcbc on 2010-05-21
With wubi, it downloads the ubuntu install cd (live cd) image, then it uses this the first time you reboot to do the actual ubuntu install (the stuff happening in windows is the setup of virtual disks and the grub setup - more or less as per my understanding). 

So in your case the cd image is stored under c:\ubuntu\tmp or something like that (note that the file extension isn't .iso but the wubi install knows where it is and it will be 750MB approx).

In any case, for some reason it is not able to mount this image. It might help to actually create a physical install cd and then run wubi.exe off that - assuming you have a CD drive. But I can't say for sure...

Edit: here's a link to the guide for more info, maybe it will help: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Edit2: there's also a wubi.log file created under your user temp directory (under Windows). This may only have info from the windows part of the install, but might be worth a look for anything strange.

---

### Post by Jdean983780 on 2010-05-21
Thanks to both of you....
First question "Can I boot into windows"
Yes windows works just fine, no problem

Now I think I understand about the install using windows, It appears I may have to burn a installation disc to install Ubuntu from....looks like doing it using the windows installer from the site I used failed for some reason....If that's the case then I should probably remove what I have here in my computer now, can anyone tell me how to remove this corrupt or incomplete installation I have on here now?... Thank you

---

### Post by bcbc on 2010-05-21
> **Jdean983780 said:**
> Thanks to both of you....
First question "Can I boot into windows"
Yes windows works just fine, no problem

Now I think I understand about the install using windows, It appears I may have to burn a installation disc to install Ubuntu from....looks like doing it using the windows installer from the site I used failed for some reason....If that's the case then I should probably remove what I have here in my computer now, can anyone tell me how to remove this corrupt or incomplete installation I have on here now?... Thank you

Go to Add/Remove programs and look for Ubuntu.

---

### Post by Jdean983780 on 2010-05-21
Thanks to each of you who have opened this tread and offered assistance, I appreciate it.

I have now removed it and once I install from the CD I burn I will be back to do some more reading and learning about this product..I really look forward to using it in a dual boot capacity ......Thanks once again.....Johnny

---

### Post by sydbat on 2010-05-21
You're welcome. :)

---

