---
title: "My PDF Printer doesn't work"
date: 2010-02-21
forum: General Help
---

### Post by sgsawant on 2010-02-21
I have tried all the usual stuff like:
apt-get cups-pdf and similar things. 

Of course I use the proper way (like sudo, etc.) 
As you must have guessed I am new to Linux(Ubuntu).
The point is I can't print PDF files. Have a look at the image:


<snip>


I have also modified to the cups-pdf.conf file and have directed it to /home/{USER}/PDF
And yes the aforementioned folder (i.e. PDF) exists at its proper place. 

So I think the main problem is "P2POutputStream" error which you can see in the image.

Please let me know what you think. 

Thank You in advance.

---

### Post by dionm on 2010-02-21
i think that maybe there is a problem with CUPS .... Seems that CUPS is not setting TMPDIR any more.
So you can change the driver to foomatic/foo2xqx and the hpijs to foomatic/hpijs-ZJS which they have better quality.
some informations for you printer are here
[HTML]https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp[/HTML]


Also you can install HPLIP which is easier .. i think:
[HTML]http://hplipopensource.com/hplip-web/index.html[/HTML]
[HTML]http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c3100_series.html[/HTML]

I hope that I helped.

---

### Post by sgsawant on 2010-02-21
Well thanks a lot my friend! But what you recommended did not work out. I am a bit confused as why would you suggest me to install HP drivers when I need to print PDF files on my computer?

Please forgive, I am quite new to this stuff.

Either ways, I tried to to change the driver to Generic Post-Script printer (as can be seen in the image). But that doesn't work either. 

Please help me out with this new error (if you or anyone can) which is visible in the image:


[IMG]http://img6.imageshack.us/img6/2396/screenshotuyx.png[/IMG]


I had copy-pasted some code in "cups-pdf" file in the /usr/lib/cups/backend/ folder. It seems the code doesn't work for me. Or the code is right but I have not compile it correctly.

Please let me know if you know the correct code OR the correct way to make it executable OR any other way by which I can print PDFs on my system.

Regards,

-sgsawant

---

