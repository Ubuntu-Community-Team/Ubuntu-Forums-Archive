---
title: "cannot print with brother mfc-250c"
date: 2010-05-29
forum: General Help
---

### Post by kennethtb on 2010-05-29
Hi  I have just purchased a brand new Brother printer MFC-250C which includes a fax/copier/scanner but mostly its for printing photos however Ubunto 10.4 does not recognize this model! (it works perfectly over on my other partition with windows7 using the setup disk for Brother)
I have installed everything related to Brother from Synaptic and searched the Brother web site for any drivers relating to this model and have even tried installing from Synaptic MFC-240C drivers in case they may work (no 250c available in synaptic) selecting PRINT for instance in Fspot my printer receives information for the photo but does not commence printing ..the same applies working in Gimp Gutenprint.
Any ideas anyone as I want to go over to a full partition with 10.4  thanks in advance

---

### Post by DagMan on 2010-05-29
These aren't really guaranteed to be Ubuntu compatible. 
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-250C](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-250C)
You'lle need the cupswrapper and the LPR driver in .deb format.
install them using 
sudo dpkg -i name-of-package.deb
and if there's any errors you can try 
sudo apt-get install -f

You can also look at this really old thread that is probably outdated, but may have some info thats helpful for errors you might get when initially trying.  Also if I remember right it suggests that you install one package before the other.
[http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)


These are just the printer drivers that I linked you to, and its the US site because I can't see where you're living in your profile. I live in Australia and we have differant width paper, though I think it would still be the same driver.
Here's the front page though, and after your part of the world you'd click on Linux then mfc or something along those lines, then the model of the printer.  Its a number of levels deep.

I have a brother MFC620-CN and I've found that Linux drivers have evolved for it, but have not been picture quality at all, which is what you're wanting.

---

