---
title: "Drivers for canon ip1700"
date: 2012-04-10
forum: General Help
---

### Post by nipunshakya on 2012-04-10
> **baAng said:**
> Hello,

I also had the same problem, but after a few hours googling around, I found a blog that give a complete instruction on how to install the driver. It is in Bahasa Melayu/Indonesia, I translated it. 
This steps should able to run on Canon printer types of iP1880, iP1700 and iP1980 


Okay, let start!

1) First download the zipped file that contains the drivers here [iP1880 + iP1700]("http://www.box.net/shared/pmepfyq428") 
put the downloaded file at your Desktop.

2) Open the terminal and run this commands line by line.
```
cd ~/Desktop/iP1880+iP1700
sudo dpkg -i *.deb
```3)Open **System &#8594; Administration &#8594; Printing &#8594; New Printer** and choose your printer type (for me Canon iP1700). Click forward.

4) Don't choose **Select Printer from Database**, choose **Provide PPD File** instead

5) Then choose canonip1800.ppd by navigating the windows according to this 
*/usr/share/cups/model/canonip1800.ppd*

6) Give name to your printer (Such as iP1700 or iP1880) and click Apply.

7) Restart your Linux Box.

8. After the restart process finish, open the terminal again and run this commands line by line.
```
cd /usr/lib
sudo ln -s ./libtiff.so.4.2.1 ./libtiff.so.3
```9) Now, you should be able to print :popcorn:

Cheers!!

acknowledgement : [Install Offline]("http://install-offline-ubuntu.blogspot.com/2009/04/canon-ip1880-ip1700-ip1980-printer.html?showComment=1245140273224#c7514199433456817922")


Hello. I have been desperately trying to install drivers for cannon ip1700 in my ubuntu 11.04 (64 bit). Isnt there a .deb package similar to the one you suggested above available for 64 bit? :(

---

### Post by oldos2er on 2012-04-11
Post moved to its own thread.

---

