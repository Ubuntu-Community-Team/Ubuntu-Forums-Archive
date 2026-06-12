---
title: "Need help with online form and scanner"
date: 2010-01-19
forum: General Help
---

### Post by webbdawg on 2010-01-19
Linux seems incapable of doing the simple things and I am just about ready to ditch it and go back to Windoz XP.

I have been using it exclusively for almost 1 month. Previously I played with it on and off.

1.
Recently the most basic of things is filling in an online pdf form. Saving it and emailing it off to the competition organizers. It seems that Mac and Windoz platforms and programs work just fine and save the document with data intact. I have been trying and cannot get my data to save. In previous years when running Windoz it worked just fine.

2.
My scanner portion of my brand new (bought right before I switched) Epson workforce 610 is unusable. I have been getting help in another thread but it is going nowhere.

There is more but I will not unload totally.

Why is Linux incapable of managing the little things?

Thanks for all the help, it has made a difference,

Dave

---

### Post by lykwydchykyn on 2010-01-19
> **webbdawg said:**
> Linux seems incapable of doing the simple things and I am just about ready to ditch it and go back to Windoz XP.

I have been using it exclusively for almost 1 month. Previously I played with it on and off.

1.
Recently the most basic of things is filling in an online pdf form. Saving it and emailing it off to the competition organizers. It seems that Mac and Windoz platforms and programs work just fine and save the document with data intact. I have been trying and cannot get my data to save. In previous years when running Windoz it worked just fine.

What PDF reader are you using?  I've had trouble with filling forms using anything other than Adobe reader on any platform.  Adobe makes a linux version of Adobe reader, maybe you should try that before giving up.
> 
2.
My scanner portion of my brand new (bought right before I switched) Epson workforce 610 is unusable. I have been getting help in another thread but it is going nowhere.

Have you contacted Epson for support?  What did they say?
> 
There is more but I will not unload totally.

Why is Linux incapable of managing the little things?

Probably because 9/10 of the energy, time, and resources of the consumer technology industry is devoted to making products work flawlessly in Windows.  It's just reality that any system that isn't Windows is going to have compatibility issues.

I started with Linux in 2003, and let me tell you things are a lot better now.  Back then you had about a 50% chance that any given piece of hardware was going to work, regardless of how much fiddling you did.  Nowadays, it seems like it works about 80% of the time out-of-the-box, and maybe 90% if you are willing to tinker a bit. (yeah, those are made up statistics based on personal experience, take them with a grain of salt).

So, I guess I'm more amazed at how much stuff does work, considering the relative lack of market share and industry support.

---

### Post by Leppie on 2010-01-19
If you want simplicity for the things that seem simple in windows, why don't you try Linux Mint? it's a distro based on Ubuntu, but once installed you already have all the multimedia things and the whole shebang already installed and configured. and since this is an Ubuntu distro, drivers should not be a big issue.

and to be honest, if i only want to browse the web, listen to some music, watch some films, etc., any system will do that in a good manner. i don't know what exactly you used to use windows for, but i found using it more troublesome than using ubuntu.

---

### Post by webbdawg on 2010-01-19
I do work mostly which is web based.

But when I could not get the pdf form filled in and saved, which used to be all browser based, I got a bit pissed.

---

### Post by RedRat on 2010-01-19
I would concur with the suggestion that you install the linux version of Adobe Reader. However, I too have had problems filling in forms in PDF files IN WINDOWS! Sometimes the forms are permission protected. Might try downloading the form as a pdf file then checking its properties by right clicking on it. You might find that it is set to read only.

Hate to repeat what is oft repeated here, Ubuntu/Linux is not Windows or Mac. As to hardware, one should first do some research about hardware before buying it, e.g., is it supported in Linux? Go to websites and check this out. The sorry fact of life is that not all hardware has Linux support. But this is also true in Windows. I just got an older HP printer/scanner/fax from a friend (the price was right, $0) and found that it was not completely supported in Windows Vista. Some functions will work but not all of them.

---

### Post by Mike'sHardLinux on 2010-01-19
> **webbdawg said:**
> I do work mostly which is web based.

But when I could not get the pdf form filled in and saved, which used to be all browser based, I got a bit pissed.

It is not really browser based in the truest sense. Check your running process and I bet you'll find Adobe running.

---

### Post by Anubis on 2010-01-19
Have you tried Windows 7?

Use what works FOR YOU.

Linux OBVIOUSLY is not incapable or we all would not be using it just fine.

So, maybe you should look at what other part of the human/computer equation might be "incapable'?

---

### Post by webbdawg on 2010-01-19
I have the AdbeRdr9.2-1_i486linux_enu.bin file downloaded but, there is always a but.

I cannot get it installed. Why do there have to be so many types of packages. tar, deb, bin some install some don't

I'll try to find out how to install a bin file.

---

### Post by audiomick on 2010-01-19
I saw a thread about .bin files the other day. I _think_ they just run. The right command in the directory it is in, and off it goes.

---

### Post by steveneddy on 2010-01-19
HP printers with the HPLIP software from the HP website seem to work very well for all printing needs on a Linux platform.

---

### Post by webbdawg on 2010-01-19
> **steveneddy said:**
> HP printers with the HPLIP software from the HP website seem to work very well for all printing needs on a Linux platform.
Printing is not the problem. I have a fine driver for the Epson Printer. It is the other multi function parts.

---

### Post by 3rdalbum on 2010-01-19
> **webbdawg said:**
> Printing is not the problem. I have a fine driver for the Epson Printer. It is the other multi function parts.

HPLIP stands for "HP Linux Imaging and Printing" - so if you had an HP multifunction, you'd have printing AND scanning support.

Note, it seems you're still in the Windows mindset; you don't need to download the Acrobat Reader from the Adobe website, it's already in the "partner" repository (I believe). In the Software Sources program, under the Third Party tab, enable the partner repository and then you should find Acrobat Reader in Synaptic Package Manager (just do a search for "adobe").

---

### Post by mcbelisle on 2010-01-19
I have an epson workforce 610 printer/scanner and the scanner works great on network and usb. I also found this website for pdf form filling  [http://pdffiller.com/](http://pdffiller.com/)


for the epson workforce 610 you need this ppa [https://launchpad.net/~matttbe/+archive/ppa/+packages](https://launchpad.net/~matttbe/+archive/ppa/+packages)

install sane-backends. it's the newest version

---

### Post by webbdawg on 2010-01-19
> **3rdalbum said:**
> HPLIP stands for "HP Linux Imaging and Printing" - so if you had an HP multifunction, you'd have printing AND scanning support.

Note, it seems you're still in the Windows mindset; you don't need to download the Acrobat Reader from the Adobe website, it's already in the "partner" repository (I believe). In the Software Sources program, under the Third Party tab, enable the partner repository and then you should find Acrobat Reader in Synaptic Package Manager (just do a search for "adobe").

I tried all that and I could never find it. I might need to edit the software sources.

I have poked my way around fairly successfully. 

I was trying to use the Okular document viewer that came with the distro. But I guess it was seriously lacking in PDF tools.

I got the Acrobat reader plugin installed and everything is rosy (for now). I found a link to a site with the .deb package.

Thanks

---

### Post by Leppie on 2010-01-19
> **webbdawg said:**
> I tried all that and I could never find it. I might need to edit the software sources.

I have poked my way around fairly successfully. 

I was trying to use the Okular document viewer that came with the distro. But I guess it was seriously lacking in PDF tools.

I got the Acrobat reader plugin installed and everything is rosy (for now). I found a link to a site with the .deb package.

Thanks
for both bin and deb files opening them in for example nautilus should suffice.
i think that having more ways to install things make the system more flexible, you just need to get used to it. deb packages are great, whatever you install using these packages can be easily removed as well (unlike in windows).
did you actually also try the adobe website for the acrobat deb package? ;)

---

### Post by RedRat on 2010-01-20
> **3rdalbum said:**
> HPLIP stands for "HP Linux Imaging and Printing" - so if you had an HP multifunction, you'd have printing AND scanning support.

Note, it seems you're still in the Windows mindset; you don't need to download the Acrobat Reader from the Adobe website, it's already in the "partner" repository (I believe). In the Software Sources program, under the Third Party tab, enable the partner repository and then you should find Acrobat Reader in Synaptic Package Manager (just do a search for "adobe").

Guys,
To all who have brought the HP printer thing into this discussion, which was originally about Adobe Reader, I only used it as an example of Windows not completely supporting an older free HP printer (about 6 years old). That printer was for my grandson who runs a Windows Vista machine. In point of fact I know I could attach it my Ubuntu box and it would be fine. HP seems to have pretty good support for the Linux community in terms of its printers.

---

### Post by Leppie on 2010-01-20
> **RedRat said:**
> HP seems to have pretty good support for the Linux community in terms of its printers.
i think they developed the drivers for their HP-UX system first as I suppose that it wouldn't be very nice to tell their clients that their hp printers wouldn't work on their hp unix system.
the step from unix to linux then seems trivial...

---

