---
title: "Samsung SCX-4216F printer.. not working on ubuntu"
date: 2006-02-13
forum: General Help
---

### Post by hak on 2006-02-13
I had a Samsung SCX-4216F network printer on my office.. i downloaded the driver from [http://www.samsung.com/support/productsupport/download/FileView.aspx?cttfileid=247799&type=MFP&typecode=300600&subtype=Multi+Function+Product&subtypecode=300601&cmssubtypecode=&model=SCX-4216F&filetype=DR&language=](http://www.samsung.com/support/productsupport/download/FileView.aspx?cttfileid=247799&type=MFP&typecode=300600&subtype=Multi+Function+Product&subtypecode=300601&cmssubtypecode=&model=SCX-4216F&filetype=DR&language=)

then followed the installation instruction step by step.. and that what happened:
root@hisham:/home/hisham/Desktop# ./cdroot/Linux/install.sh

Please, select your device model...
         [1] MFP 560 Series
         [2] MFP 750 Series
         [3] SCX 4x20 Series
         [4] SCX 4100 Series
         [5] SCX 6x20 Series
         [6] SCX 4x21 Series
         [7] SCX 4x16 Series
         [8] SCX 4200 Series
         [9] Cancel installation
Please make your choice [1,2, ...]:7

What would you like to do?..
        [1] Install driver package
        [2] Uninstall driver package
        [3] Cancel installation
Please make your choice [1,2,3]:1

./cdroot/Linux/install.sh: line 84: rpm: command not found
MFP driver package is about to be installed on your system...

CUPS that is required for driver package to work properly was not
detected on your system. Please exit installation procedure and install
CUPS package from your Linux distribution CD-ROM or from Linux distribution
vendor web site
        [1] Exit installation procedure
        [2] I am sure I have necessary software installed. Continue installation
Please make your choice [1,2]: 
[B][COLOR="Red"]"So, here i exit installation and went to synaptic package manager..then i installed the package required (CUPS).. but it still gives me the same result above"
[/B][/COLOR]

any idea how to solve this problem..:confused:

---

### Post by Chabbrik on 2006-04-28
Hi Hak,

I do not if this problem is still relevat to you, but I think other unlucky with Samsungs might benefit from my experience. Yesterday I also tried to install Samsung 4216F.

I got the same error as you, but being cool Linuxoid, I went ahead. I said I'm sure that everything is fine, sky is blue and grass is green.

It then asked if I have a proper sane configuration, I said I have eventhough I didn't (At that moment scanning was not important to me.) The first time I run it, it failed, because I didn't start it as a root. (Do'h, I'd better start following manuals :) )

But second time despite all warnings it worked fine. I can print without any problem and as long as it works, I'm happy.

So, Samsung actually works under Linux (at least under Ubuntu, which is great)

---

### Post by hulleye on 2006-04-28
Hi Chabbrik,

I just wanted to find out exactly what you did to get the SCX-4216f running in Ubuntu. Am a relative newbie to the linux world so am still trying to figure out a lot of things. What exactly did you have to run as root in order to get the printer working. Because the stage I'm at, it sends a command to the printer, the printer goes through a warm-up cycle and the LCD display reports it is "Printing..." but no pages are actually printed.

Any help would be appreciated.

Thanks

---

### Post by Chabbrik on 2006-05-02
Hmm, I did nothing special. Well, I was not really using Ubuntu, I had installed Baltix - Lithuanian version of Ubuntu, which might have some bugs fixed.

I followed the instructions that Hak gave, just ignored the warnings given.

I tried to print from OpenOffice, that was what mattered for my client anyway. I do not know how you are trying to print something.

Have you got an icon to Samsung printers on the desktop?

---

### Post by nmsa on 2006-06-17
I can also use this printer in Ubuntu.
need to mention is not working on 64 bi arch.
just make sure you setup the port from printing and not from the driver window

---

