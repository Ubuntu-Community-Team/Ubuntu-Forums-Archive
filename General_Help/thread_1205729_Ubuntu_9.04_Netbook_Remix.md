---
title: "Ubuntu 9.04 Netbook Remix"
date: 2009-07-06
forum: General Help
---

### Post by Yumpin_Yimminie on 2009-07-06
I decided to give Ubuntu another try on my Acer Aspire.  It's been about 7 months since I looked at Linux or this computer.

Not having much luck with "**Ubuntu 9.04 Netbook Remix**" package.  I've downloaded from a couple of sites (Purdue & MIT).  When I check the hash with **winMD5Sum** it checks out just fine.  

However after using **Win32DiskImager **to IMG file to flashcard I am having problem.  I can check the directory on the flashcard and have no problems seeing it.  But when I put the flashcard in the aspire and boot from the flashcard.  I then choose the "Check file for errors" option.  I consistently get a report of error in one file.  I've tried this numerous times with downloads from either of the above mentioned sites.  

So I decided to go the DVD route.  I've used a couple of different packages for burning the ISO.  The one's I've used are "**InfraRecorder**" and "**IsoBurner**."  Haven't had any success with this route.  After finishing the burn with either package. I attempted to read the directory using Windows XP Windows Explorer.  All four of the times the system has been unable to read the directories.  I've tried connecting the external DVD writer/reader to the Acer Aspire and boot from it.  It gives me the boot menu option of loading from the DVD but then ends up loading the old Ubuntu version that was currently on the computer.  

I'm looking for suggestions.  From what I've read the file '**Ubuntu 9.04 Netbook Remix**' is supposed to have taken care of a lot of issues that I was having with the previous Ubuntu.  But after so many failures, I'm beginning to wonder if the file has been changed and is non-operable now.

Help would be greatly appreciated.

Thank you.

Have a Great Day,
Jim

---

### Post by jacktar on 2009-07-06
Did you try to boot from your USB stick ? Even if it reports an error it may still load ok.

---

### Post by Yumpin_Yimminie on 2009-07-06
Actually the first time I booted from the USB stick and loaded the 9.04.  Parts of it worked, other parts didn't.  I had selected the install option, not test drive.  For some reason after I shut down the computer and then turned it back on 9.04 was gone.

Have a Great Day,
Jim

---

### Post by Bucky Ball on 2009-07-06
Yes, wouldn't rely on the error checking from another OS. Try anyhow. 

Did you try it from this page?

[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

Check the compatibility list and see if there are any tweaks that need to be performed for your Acer model to run UNR.

---

### Post by Yumpin_Yimminie on 2009-07-06
That is where where I started my download from.  


Have a Great Day,
Jim

---

### Post by Osamabingandhi on 2009-08-17
got the same problem, i have tried an usb memory stick and now i tried an SD memory card and still one error. When i have tried to install it ends early...is there a problem with the download image or the imagewriter? i have only had sucsess with xubuntu. Oh and i have tried to format in all the different ways possible. Any other suggestions?

---

### Post by Bucky Ball on 2009-08-18
If you can install Xubuntu you have success. It is Ubuntu with a different desktop environment. Just install Xubuntu then go:

System->Admin->Synaptic Package Manager

(sorry, you will be in Xubuntu and slightly different but you will have no problems finding Synaptics (think applications->System tools from memory).

Search for and install:

ubuntu-desktop

Log out and when you are back at the log-in screen click 'Sessions' and choose Gnome. Done.

---

### Post by Osamabingandhi on 2009-08-20
I got easy peasy to work! I couldn't finish the test of the image, but this time it worked. Only downside to easy peasy is that it is 8.10...but otherwise it is really good!

---

